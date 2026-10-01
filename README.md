# Meet Peers - Invite Extensions

A Crusader Kings III mod that adds new guest invite options to the **Meet Peers** activity, so child rulers can invite children from beyond their own realm.

## Features

### Current
- **Neighboring Rulers' Children** (on by default): children of
  - rulers of bordering foreign realms (including across water)
  - same-rank rulers bordering you, e.g. the count next door in another duchy
- **Children of the Same Faith** (opt-in): children of your faith at any court in diplomatic range
- **Children of the Opposite Sex** (opt-in): children of the opposite sex at any court in diplomatic range
- **Vanilla rules still apply**: guests must be children aged 4–13, healthy, free, not hostages, and within diplomatic range
- **Reset Meet Peers Cooldown** decision (off by default): lets a child ruler plan the next Meet Peers right away instead of waiting 3 years. Planning it starts a new cooldown.

Invite options add guests together: with both opt-in options ticked you get children who are of your faith **or** of the opposite sex, not only those who are both. The guest list is capped at 30, and the new options fill after your own realm's children.

## Installation

### Steam Workshop (Recommended)
1. Subscribe to the mod on the Steam Workshop
2. Launch Crusader Kings III
3. The mod will be enabled automatically in the launcher
4. Start or load your game

### Manual Installation
1. Download the latest release from GitHub
2. Extract the archive
3. Copy the `MeetPeersInviteExtensions` folder to:
   ```
   Documents\Paradox Interactive\Crusader Kings III\mod\
   ```
4. Copy the `descriptor.mod` file to the same `mod` folder and rename it to `MeetPeersInviteExtensions.mod`
5. Launch Crusader Kings III
6. Enable "Meet Peers - Invite Extensions" in the launcher's Mods tab
7. Start or load your game

## How to Use

1. Play a landed child ruler aged 4–13 (Count or higher)
2. Plan the **Meet Peers** activity from the Activities menu
3. In the guest list, tick the invite options you want
4. To host again before the 3-year cooldown ends, take the **Reset Meet Peers Cooldown** decision from the Decisions menu. It's off by default:
   - **New game:** set the **Meet Peers Cooldown Reset** game rule (Tweaks) to *Enabled*
   - **Running game:** game rules can't be changed after the start, so enable it from the console (debug mode): `effect set_global_variable = mpie_meet_peers_cooldown_reset_enabled`

## Compatibility

- **CK3 Version**: 1.20.*
- **Achievements**: No (the mod changes `common/` files, which changes the game checksum)
- **Save Game Compatible**: Yes
- **Conflicts**: replaces vanilla `common/activities/activity_types/playdate.txt`, so it conflicts with other mods that change the Meet Peers activity

## Support

For issues or suggestions, visit the GitHub repository.
