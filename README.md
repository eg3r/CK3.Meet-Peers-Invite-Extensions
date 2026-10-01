# Meet Peers - Invite Extensions

A Crusader Kings III mod that expands the **Meet Peers** activity: child rulers can invite children from beyond their own realm, pick a goal aimed at one of the other children, host Meet Peers more often, and get invited by AI children nearby.

## Features

### Guest invite options
- **Neighboring Children** (on by default): the rulers next door who are children themselves, and the children of
  - rulers of bordering foreign realms (including across water)
  - same-rank rulers bordering you, e.g. the count next door in another duchy
- **Nearby Player Children** (on by default): in multiplayer, other players whose characters are children living nearby. The same rule makes nearby AI children invite you (see below).
- **Children of the Same Faith** (opt-in): children of your faith at any court in diplomatic range
- **Vanilla rules still apply**: guests must be children aged 4–13, healthy, free, not hostages, and within diplomatic range

Invite options add guests together: a child is invited if any ticked option includes them. The guest list is capped at 30, and the new options fill after your own realm's children.

### Meet Peers goals
In vanilla, Recreation is the only goal (intent) for Meet Peers. Player children, whether hosting or attending as a guest, can now also pick a goal aimed at another child:
- **Befriend a Peer**: a chance to become friends with your target (10–90%). It is better if you are already potential friends, if they like you, and if your diplomacy is high; Gregarious or Trusting children make friends more easily, Shy, Callous or Paranoid ones less. Bringing a gift (10 gold) or using your standing adds 15%. Standing costs 50 prestige and makes them a little annoyed with you (-10 opinion); administrative governments pay 30 influence instead, without the annoyance. A Charming child can make them laugh (+20%), and a Rowdy or Curious child has their own approach (+10%). If it fails, you may still become potential friends.
- **Learn from a Peer**: a chance to gain +1 in the skill where your target is furthest ahead of you (15–70%), or in their second-best skill at a lower chance. Any of the six skills counts, prowess included. The bigger the gap and the better your learning, the better the chance; a lesson in your education focus, or being Diligent or Curious, helps, being Lazy hurts. Praying for wisdom first (75 piety) or using your standing adds 15%.
- **Role Model**: a chance to take on one of your target's personality traits (10–50%), or another of their traits at a lower chance. It is better if you are friends or no more than 2 years apart, and easier for Fickle children than for Stubborn ones; asking the chaplain for guidance (75 piety) adds 15%. It never picks a trait you have or one that conflicts with yours, never lustful or chaste, and only applies while you have fewer than 4 personality traits.

How the goals work:
- Once you and your target have both arrived, a moment together usually comes up (about 80%: more for Gregarious, Charming or Rowdy children, less for Shy ones). It comes at a random point during the Meet Peers, not right at the start. If it doesn't, you get a second, smaller chance (about 30%) in the last month. If you try and fail, another moment may come about three weeks later (about 30%, once per goal in each Meet Peers).
- The event shows the skill or trait and the chance of each option before you decide. As in vanilla Meet Peers, the choices also cost or relieve stress depending on your child's traits (Shy, Gregarious, Rowdy, Pensive, Curious, Diligent, Lazy and more).
- Every event also offers an alternative pastime instead: play with the others or find a quiet corner (less stress), visit the chapel (piety), or show off (prestige).
- Successes and failures are recorded in the activity log. If no moment came up, or your target never showed up, the conclusion says so.
- AI children keep Recreation.

### Cooldown
- **Shorter Meet Peers cooldown**: 2 years instead of the vanilla 3. The **Meet Peers Cooldown** game rule (Tweaks) can set it to 1, 2 or 3 years.
- **Reset Meet Peers Cooldown** decision (off by default): lets a child ruler plan the next Meet Peers right away instead of waiting for the cooldown. Planning it starts a new cooldown.

### AI children host and invite you
In vanilla, AI child rulers rarely host Meet Peers, and when they do, they almost never invite a player child who isn't a relative, friend or part of their realm. Now:
- **AI children host more often:** about once per childhood for counts, twice for dukes, three times for kings and four times for emperors, spread out over time.
- **They invite you:** an AI child hosting nearby puts your child at the top of the guest list. "Nearby" means the same or a neighboring realm, or close by. AI children of your faith also invite you from further away.
- **They host more when you're near:** AI children near a player child host more readily, and even child counts who would otherwise rarely host.
- **Game rule "AI Meet Peers and Player Children"** (Tweaks): Off / Nearby / Nearby and Same Faith (default). **Off** turns the whole feature off: AI children host and invite as in the base game.
- **Game rule "Meet Peers Guests at War"** (Tweaks, allowed by default): in vanilla, a child at war can't attend a Meet Peers. Child rulers often inherit wars, so by default player children at war can still attend as guests. Set it to "Not Allowed" for the vanilla behavior.

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
4. To pick a goal, open the goal (intent) selection in the planner, choose **Befriend a Peer**, **Learn from a Peer** or **Role Model**, and pick the child it is aimed at. The goal only plays out if that child accepts the invitation and attends. You can also pick or change the goal during the activity, and guests can pick one too.
5. To change how long you wait between Meet Peers, set the **Meet Peers Cooldown** game rule (Tweaks) when starting a new game. Saves from before this rule existed use the 2-year default. A cooldown that is already running keeps its end date; the new length applies from the next Meet Peers.
6. To host again before the cooldown ends, take the **Reset Meet Peers Cooldown** decision from the Decisions menu. It's off by default:
   - **New game:** set the **Meet Peers Cooldown Reset** game rule (Tweaks) to *Enabled*
   - **Running game:** game rules can't be changed after the start, so enable it from the console (debug mode): `effect set_global_variable = mpie_meet_peers_cooldown_reset_enabled`
   - A cooldown from a Meet Peers hosted with an older version of this mod is stored by the game itself. It can't be reset and simply runs out.

## Compatibility

- **CK3 Version**: 1.20.*
- **Achievements**: No (the mod changes `common/` files, which changes the game checksum)
- **Save Game Compatible**: Yes
- **Conflicts**: replaces vanilla `common/activities/activity_types/playdate.txt`, so it conflicts with other mods that change the Meet Peers activity

## Support

For issues or suggestions, visit the GitHub repository.
