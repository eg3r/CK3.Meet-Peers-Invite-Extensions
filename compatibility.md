# Compatibility

## In short

- The mod **replaces one vanilla file**: the Meet Peers activity (`common/activities/activity_types/playdate.txt`). Any other mod that changes the Meet Peers activity itself conflicts with it: whichever loads last wins, and the other mod's Meet Peers changes are lost.
- Everything else is **added**, not replaced: new invite options, goals, events, game rules, decisions, opinions and texts, all under its own names (prefix `mpie_`). These can't clash with vanilla or with other mods.
- It hooks into one vanilla yearly pulse the way vanilla's modding notes recommend, so other mods using the same pulse keep working.
- It doesn't change any interface (`.gui`) files, defines or vanilla localization.
- Achievements stay available: the mod changes the game's checksum (its files are in checksummed folders: `common`, `events`, `localization`), but CK3 1.20 still shows "Achievements: Available" with a modified checksum (confirmed on the Game Rules screen). Only two of the mod's settings switch them off, flagged like vanilla's cheat-like rules: the 1-year Meet Peers Cooldown and the Meet Peers Cooldown Reset.

## What the mod replaces

### `common/activities/activity_types/playdate.txt` (full override)

CK3 can't add to an activity type from another file: the invite options, goals (intents), special guests and AI settings all live inside the single `activity_playdate` definition. So the mod ships the whole file, at the vanilla path, and it replaces vanilla's file entirely.

It's vanilla's file from CK3 1.20.0.3 (927 lines) with every change marked `# MPIE`. Everything not marked is vanilla, unchanged. With the "AI Meet Peers and Player Children" rule set to Off, every AI-related change below falls back to vanilla behaviour.

| Part of the activity | Vanilla | This mod |
|---|---|---|
| `is_shown` | only children (`is_adult = no`); child counts need sociability 100 | also adults, when they may plan a Meet Peers for a child at their court; the sociability requirement for child counts drops while the "AI Meet Peers and Player Children" rule is on |
| `can_start_showing_failures_only` | children aged 4-13 | adults planning for a child at court are checked against the court's own cooldown instead of their age; the mod's own cooldown check is added |
| `is_valid` | the host must hold land | also valid when the host is a child at court who took over from the ruler |
| `on_invalidated` | "the host lost their land" message | skipped for a child at court, who never had land |
| `cooldown` | native 3-year cooldown | **removed**; the mod runs its own cooldown (game rule, 1-3 years) so the reset decision can work |
| phase `on_phase_active` | vanilla events | plus goal encounters and the family bonus |
| phase `on_weekly_pulse` | none | new: goal encounters |
| phase `on_end` | vanilla conclusion | plus goal wrap-up, family bonus, the end report for players, a prestige check for a child host, debug logging; the vanilla conclusion still runs |
| `ai_will_do` | vanilla | the affordability check is replaced for children (rule on), plus the mod's bonus (0 with the rule off) |
| `guest_invite_rules` | vanilla rules | adds the mod's own options, including close and extended family (family first: for player hosts, and for AI hosts only while the "AI Meet Peers and Player Children" rule is on); friends, crushes, scheme targets and confederates move from priority 1 to 2 |
| `can_be_activity_guest` | `is_available_for_child_activity_trigger` | the same check, except player children at war may attend (game rule) |
| `special_guests` | none | new: the "Young Host" slots for a child at court |
| `host_intents` / `guest_intents` | Recreation only | adds the three goals |
| `guest_join_chance` | vanilla | adds a bonus for the host's siblings and family (same condition as family first) |
| `on_start` | vanilla | plus the mod's cooldown, hosting count, debug log, and the handover of a ruler-planned Meet Peers to the child |

**What this breaks in other mods:** any mod that ships its own `playdate.txt`, or otherwise redefines `activity_playdate`, e.g. mods that add Meet Peers guests, goals, options or events wired into the activity, change its cooldown or its AI. One of the two loses all its Meet Peers changes:

- **This mod loads last:** the other mod's Meet Peers changes are gone; its other content (events, files of its own) still loads.
- **The other mod loads last:** this mod's Meet Peers changes are gone, but its other parts still run, which leaves some features half-working:
  - the new invite options, goals and the Young Host slot don't appear;
  - the native 3-year cooldown is back, and the cooldown game rule and the reset decision do nothing;
  - children at court still ask for a Meet Peers every year, but rulers can't plan one: AI rulers keep failing and retrying, and players see a planner that won't let them;
  - AI children host at vanilla rates again.

  The only fix is a compatibility patch that merges both files (see below).

**What this breaks in vanilla updates:** the file is a copy of CK3 1.20.0.3. If a game update changes vanilla Meet Peers, the mod keeps the old version until it's re-synced (see AGENTS.md, "Updating for a new CK3 version").

## What the mod adds (no conflicts)

All new definitions use the prefix `mpie_` in files of their own, so they can't overwrite vanilla or other mods:

| Folder | Content |
|---|---|
| `common/activities/guest_invite_rules/` | the invite options (Neighboring Children, Nearby Player Children, Children of Court and Vassals, Children of the Same Faith, and one more opt-in option) |
| `common/activities/intents/` | the three goals |
| `common/decisions/` | Reset Meet Peers Cooldown |
| `common/game_rules/` | five game rules |
| `common/important_actions/` | the "Promised Meet Peers" reminder |
| `common/on_action/` | the mod's own on_actions (see below) |
| `common/opinion_modifiers/` | the court opinions |
| `common/script_values/`, `scripted_effects/`, `scripted_triggers/` | the mod's logic |
| `common/trigger_localization/` | cooldown tooltips |
| `events/activities/` | the goal encounters (namespace `mpie_peer`) and the court events (namespace `mpie_court`) |
| `localization/<language>/` | 158 new keys in 9 languages; no vanilla key is overridden |

Event namespaces `mpie_peer` and `mpie_court` would only clash with another mod using the same namespace names.

## Shared hook: the yearly pulse

`common/on_action/mpie_on_actions.txt` adds its own on_actions to vanilla's `random_yearly_playable_pulse` (the yearly court request, a cleanup for promises that can't be kept, an extra yearly hosting check for AI child rulers while the AI rule is on, and a debug-only census):

```
random_yearly_playable_pulse = {
	on_actions = { mpie_court_meet_peers_pulse mpie_court_meet_peers_stale_promise_pulse mpie_ai_meet_peers_extra_check_pulse mpie_titled_meet_peers_census_pulse }
}
```

This is the pattern from vanilla's `_on_actions.info`: on_action lists from several files are merged, so vanilla's pulse and other mods' additions keep working. It would only break if another mod added a second `effect` or `trigger` block directly to `random_yearly_playable_pulse`, which vanilla's notes forbid anyway. The census on_action does nothing outside debug mode.

## What the mod relies on from vanilla

The mod doesn't change these, but uses them. A mod that changes them changes how this mod behaves. That's usually fine (the mod follows along), but worth knowing when something looks off:

- **Meet Peers events and on_actions**, referenced by the overridden `playdate.txt` exactly as in vanilla: `playdate.0020`-`0022`, `2001`, `2003`, `2501`, `9001`, `9002` and the on_action `playdate_event_selection`. A mod that removes or renames them breaks Meet Peers events, with or without this mod.
- **Invite rules:** `activity_invite_rule_siblings`, `_friends`, `_crushes`, `_personal_scheme_targets`, `_confederates`, `_liege`, `_vassals`, `_vassals_children`, `_powerful_vassals_children`, `_fellow_vassals`, `_fellow_vassals_children`, `activity_invite_mp`.
- **Guest acceptance:** `activity_guest_shared_ai_accept_modifier`, `base_activity_modifier`.
- **Who can be a guest:** `is_available_for_child_activity_trigger`, `less_than_two_years_to_adulthood_value` (the mod follows a changed childhood age automatically).
- **AI hosting:** `ai_activity_war_check`, `ai_activity_coronation_check`, `activity_general_ai_will_do_value`, `can_make_expensive_purchase_trigger`, `activity_minor_gold_value`.
- **Costs and amounts:** `standard_playdate_activity_cost`, `standard_playdate_cooldown_time`, `medium_prestige_gain`, `minor_prestige_gain`, `minor_piety_gain`, `minor_influence_value`, the stress impact values, `personality_trait_limit`.
- **Relations:** `can_set_relation_friend_trigger`, `can_set_relation_potential_friend_trigger`; opinions `hosted_successful_playdate_opinion`, `haughty_opinion`.
- **Distances:** `squared_distance_medium`, `squared_distance_large`.
- **The planner window:** the Young Host is a normal special guest slot, shown by vanilla's activity planner. A UI mod that rebuilds the planner should still show it, as long as it keeps special guests.

## Typical mod combinations

| Other mod | Result |
|---|---|
| Changes the Meet Peers activity (`playdate.txt`) | **Conflict.** One mod's Meet Peers changes are lost (see above). Needs a compatibility patch. |
| Adds new Meet Peers events or changes vanilla Meet Peers events | Works, as long as the vanilla event ids above still exist. |
| Adds new activities, or changes other activities | Works. The mod only counts other activities when it spreads Meet Peers out; it doesn't change them. |
| Changes guest acceptance, invite rules, costs, AI activity rules, childhood age | Works; this mod follows those changes. |
| Changes the activity planner or other interface | Works, as long as special guest slots stay. |
| Uses `random_yearly_playable_pulse` | Works (merged on_action lists). |
| Total conversions with their own Meet Peers or without it | Not tested. |

## Saves

- **Adding the mod to a running game:** works. Game rules then use their defaults (they can't be changed after the start); the reset can be switched on from the console (see README).
- **Removing the mod from a running game:** cooldowns set by the mod stay behind as unused variables and simply expire. A Meet Peers hosted by a child at court that is still running when the mod is removed is cancelled by vanilla, because its host holds no land.

## Making a compatibility patch

For another mod that also changes `playdate.txt`:

1. Take the other mod's `playdate.txt`.
2. Re-apply every change marked `# MPIE` from this mod's file (`diff` this file against vanilla 1.20.0.3 to list them).
3. Ship it as a third mod that loads after both, at the same path.
