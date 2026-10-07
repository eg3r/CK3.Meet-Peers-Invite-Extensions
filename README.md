# Meet Peers - Invite Extensions

A Crusader Kings III mod that expands the **Meet Peers** activity: child rulers can invite children from beyond their own realm, pick a goal aimed at one of the other children, host Meet Peers more often, and get invited by AI children nearby. Children who live at court without a title of their own, such as a king's children, can host too.

## Features

### Guest invite options
- **Neighboring Children** (on by default): the rulers next door who are children themselves, and the children of
  - rulers of bordering foreign realms (including across water)
  - same-rank rulers bordering you, e.g. the count next door in another duchy
- **Nearby Player Children** (on by default): in multiplayer, other players whose characters are children living nearby. The same rule makes nearby AI children invite you (see below).
- **Children of Court and Vassals** (on by default when a ruler plans a Meet Peers for a child at court): the children living at the court and the children of the ruler's vassals
- **Children of the Same Faith** (opt-in): children of your faith at courts up to about half the size of France away
- **Family first**: the host's brothers, sisters and cousins are invited before anyone else, and are more likely to come (a little less likely than friends)
- **Vanilla rules still apply**: guests must be children aged 4–13, healthy, free, not hostages, and within diplomatic range

Invite options add guests together: a child is invited if any ticked option includes them. Up to 30 children are invited, and children close to you, such as your family, court and realm, come first.

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
- **They host more when you're near:** AI children near a player child host more readily.
- **But not all at once:** AI children are less likely to host while other Meet Peers already run nearby, so the children around aren't spread over too many at the same time.
- **Game rule "AI Meet Peers and Player Children"** (Tweaks): Off / Nearby / Nearby and Same Faith (default). **Off** turns the whole feature off: AI children host and invite as in the base game.
- **Game rule "Meet Peers Guests at War"** (Tweaks, allowed by default): in vanilla, a child at war can't attend a Meet Peers. Child rulers often inherit wars, so by default player children at war can still attend as guests. Set it to "Not Allowed" for the vanilla behavior.

### Court children host Meet Peers
In vanilla, only children who hold a title can host Meet Peers, so the children of a king who live at court never do. Now the ruler plans it, and the child takes over as host:
- **Plan it yourself:** as a king or emperor (or a duke, with the game rule below) with a child aged 4–13 at court, you can plan Meet Peers from the Activities menu. Pick the child in the **Young Host** slot (click it to choose from the guest list). The new **Children of Court and Vassals** guest option invites the children living at your court and the children of your vassals. You pay what Meet Peers costs at your rank (duke 20, king 55, emperor 65 gold; tribal rulers half). When it starts, your child becomes the host and you stay home.
- **A child asks:** once a year, a child at court may ask for one. AI rulers say yes if they can afford it and plan it. As a player ruler you get an event: say yes, and the Meet Peers planner opens with that child already set as the Young Host (you can also plan it later during the next year: a reminder at the top of the screen takes you back to it); refuse, and the child is disappointed in you (-15 opinion, fading over 5 years) and asks again after a year at the earliest.
- **Not too many in one place:** children don't ask while several Meet Peers are already running nearby, so the children around aren't spread too thin. AI rulers also wait until a few children nearby are free to come; where children are few, they host anyway after a while. A child who is away, or a court that has to wait, gets another chance a few months later instead of next year. Planning one yourself is never held back.
- **You hear how it went:** when it's over, you get a short report: how many children came, who of your family was there, and whom your child made friends with.
- **Your children thank you:** the young host likes you more (+20 opinion, fading over 10 years), and every child of your family who comes too, as soon as it begins (+10, fading over 5 years).
- **One per court every 2 years.** The child hosts at the ruler's capital. Their siblings, the children of the ruler's vassals and of neighboring realms, and nearby player children are invited.
- **Game rule "Court Children Host Meet Peers"** (Tweaks): Off / Kings and Above (default) / Dukes and Above.

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

1. Play a landed child ruler aged 4–13 (Count or higher), or a king or emperor with a child aged 4–13 at court
2. Plan the **Meet Peers** activity from the Activities menu. As a ruler planning for your child, pick them in the **Young Host** slot
3. In the guest list, tick the invite options you want
4. To pick a goal, open the goal (intent) selection in the planner, choose **Befriend a Peer**, **Learn from a Peer** or **Role Model**, and pick the child it is aimed at. The goal only plays out if that child accepts the invitation and attends. You can also pick or change the goal during the activity, and guests can pick one too.
5. To change how long you wait between Meet Peers, set the **Meet Peers Cooldown** game rule (Tweaks) when starting a new game. Saves from before this rule existed use the 2-year default. A cooldown that is already running keeps its end date; the new length applies from the next Meet Peers.
6. To host again before the cooldown ends, take the **Reset Meet Peers Cooldown** decision from the Decisions menu. It's off by default:
   - **New game:** set the **Meet Peers Cooldown Reset** game rule (Tweaks) to *Enabled*
   - **Running game:** game rules can't be changed after the start, so enable it from the console (debug mode): `event mpie_debug.0001`. The original command, `effect set_global_variable = mpie_meet_peers_cooldown_reset_enabled`, also works.
   - A cooldown from a Meet Peers hosted with an older version of this mod is stored by the game itself. It can't be reset and simply runs out.
7. To see only this mod's game rules, pick **Meet Peers** in the filter dropdown of the Game Rules screen

## Compatibility

- **CK3 Version**: 1.20.*
- **Achievements**: stay available with the mod. Only two settings switch them off, like vanilla's cheat-like rules: the 1-year **Meet Peers Cooldown** and **Meet Peers Cooldown Reset** set to Enabled
- **Save Game Compatible**: Yes
- **Conflicts**: replaces vanilla `common/activities/activity_types/playdate.txt`, so it conflicts with other mods that change the Meet Peers activity
- **Details**: see [compatibility.md](compatibility.md) for exactly what the mod replaces, what it only adds, and how other mods are affected

## Support

For issues or suggestions, visit the GitHub repository.
