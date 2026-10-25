# Toy Box for BO2 Zombies

Your friends control your zombies match from their phones. Send them a link and they get buttons for Max Ammo, perks, Ray Guns, hordes, hellhounds, bosses, low gravity, fake power-ups and a lot more. Everything they do shows up on your screen with their name on it.

<p align="center"><img src="docs/images/friend-phone.png" width="300" alt="The friend page on a phone: the match, who's on, what's running and the Quick buttons"></p>

## Get started

1. **[Download ToyBox.exe](../../releases/latest/download/ToyBox.exe)**, open it and click **Install**.
2. Start BO2 Zombies with Plutonium, click **Mods**, pick **Toy Box** and start any map.
3. The friend link is already copied. Paste it to your friends.

That's it. Your friends just open the link and type a name. They don't need the game.

> If Windows says "Windows protected your PC", click **More info**, then **Run anyway**. That shows up because the alpha isn't code-signed yet.

You need Windows 10 or 11 and [Plutonium](https://plutonium.pw) with BO2 Zombies. Works on every zombies map, Survival and Classic.

**Playing alone?** Press **Esc** in a match, go to **Options > Settings > TOY BOX** and set **Simulate a friend** to **FAIR** or **TROLL**. Someone with a random gamertag takes the controller.

> This is an alpha. If something breaks, please open an issue on the [Issues](../../issues) page with the map and what happened.

## What your friends get

![The friend page on a computer: Quick buttons, what's on, the activity feed and match stats](docs/images/friend-desktop.png)

- **Quick buttons:** Max Ammo, perks, Pack-a-Punch, god mode, revive, kill everything.
- **Power-ups, perks and weapons** from this map and every other one.
- **Spawning:** zombies, hellhounds and each map's own enemies (Brutus, Panzers, Jumping Jacks, Buried's ghosts). Zombies friends send have **white eyes**.
- **The map:** power on, open every door, move the box, fire sales.
- **Tricks and scares:** sprinters, crawlers, freeze, slow motion, low gravity, fake power-ups, the announcer, a screen shake.
- **Bounties:** "10 headshot kills in 60 seconds for 2000 points".
- **Match stats:** who sent the most zombies, caused the most downs, won the most bounties.

## The teddy bear by the clock

Toy Box sits by the clock as a teddy bear (click the **^** arrow if you don't see it). Click it for:

- **Copy friend link** and **Open friend link**: the link your friends use.
- **Pause friends** and **Panic**: stop their buttons, or undo the chaos (kills what they sent, cancels what's scheduled).
- **Host controls**: who's on (kick and ban), what friends can use, limits, and match history.

It starts with Windows and does nothing until you play. The link changes each time you open the game, so send the new one each time. Anyone with the link can control your match, so only share it with people you're playing with.

## Something not working?

- **No link on screen:** make sure the teddy bear is by the clock (if it isn't, open ToyBox.exe again and click **Reinstall**) and that you picked **Mods > Toy Box**. Then click the teddy bear > **Show link in game**.
- **The link doesn't open:** send the newest one (it changes when the game restarts), and give a brand-new link about 20 seconds.
- **Friends' buttons do nothing:** your game is paused (a solo game pauses in menus or when you alt-tab), or friends are paused. Their page says which.
- **Anything else:** click the teddy bear > **Open log**, and attach the log to an [issue](../../issues).

**Update:** download the new ToyBox.exe and open it. Your link, settings and match history stay.
**Remove:** Windows Settings > Apps > Installed apps > Toy Box > Uninstall.

---

Everything below is extra: you don't need it to play.

- [Simulate a friend, in detail](#simulate-a-friend-in-detail)
- [Host controls](#host-controls)
- [Contests with match stats](#contests-with-match-stats)
- [The TOY BOX settings tab](#the-toy-box-settings-tab)
- [Typing commands yourself](#typing-commands-yourself)
- [Installing without ToyBox.exe](#installing-without-toyboxexe)
- [Running on top of another mod](#running-on-top-of-another-mod)
- [Privacy and safety](#privacy-and-safety)
- [Reference](#reference): [commands](#commands), [settings](#settingsjson), [API](#api), [compatibility](#compatibility-and-the-mod-api)
- [Building from source](#building-from-source)
- [License](#license) and [credits](#credits)

## Simulate a friend, in detail

When nobody's around to press buttons, the game plays a friend for you. Everything they do shows on screen the same way a real friend's would.

1. In a Toy Box match, press **Esc** and go to **Options > Settings > TOY BOX**.
2. Set **Simulate a friend** to **FAIR** or **TROLL**, and **Intensity** to **CHILL**, **NORMAL** or **WILD**.
3. Go back to the game. Within a few seconds "<gamertag> joined the controller" shows up.

**Fair** watches how you're doing: whether you're down or hurt, how many zombies are close, whether you're low on ammo.
- When things have been quiet for a while, they push back: a horde, sprinters, hellhounds or Jumping Jacks. Tougher zombies come from round 8, and Brutus or a Panzer from round 12. The big ones come a few seconds after the hellhound music sting.
- After each push, they give you time to breathe.
- When you're struggling, they help: a Max Ammo, an Insta-Kill, a short freeze, or a few seconds where the zombies lose track of you. They never take anything away.

**Troll** messes with you every minute or so (more often on wild, less on chill):
- a Max Ammo that turns out to be fake (then a real one);
- a free perk you lose if you don't get the kills in a minute;
- a stampede of sprinting zombies, with a speed boost for you;
- frozen zombies and a few free points;
- 500 points taken, then 1000 given back;
- low gravity, dares, hellhounds, a moved box, lights out.

They show up in the match stats under their gamertag, like any friend. They sit out while a real friend is sending commands, and pick up again a minute after. You can also switch them from Host controls or the console: `set tb simulate fair`, `set tb simulate troll wild`, `set tb simulate off`. `set tb simulate now` makes them do something right away.

## Host controls

![Host controls: the friend link, Panic, who's on with kick and ban, and what friends can use](docs/images/host-controls.png)

Click the teddy bear by the clock and choose **Host controls**. A page opens in your browser. It only works on your own PC; friends can't reach it through their link.

- **Who's on:** everyone on the friend page. Kick or ban anyone.
- **What friends can use:** switch whole groups off, like spawning, weapons, rounds or god mode. Skipping rounds and killing everything are off for friends until you turn them on. With Points off, the bounties friends set are for 0 points.
- **Limits:** a cooldown between each friend's commands, and the most zombies one spawn can send. Each friend can also have only 8 commands waiting for the game at a time, so one fast clicker can't hold everyone else up.
- **Events and a simulated friend:** turn random events on or off, and have the game simulate a friend (fair or troll).
- **Live now:** running bounties, effects and scheduled commands, each with a cancel button.
- **A command box:** type any command and it runs as you.
- **Match history:** every match with what each friend did, as downloads. Friends only see the matches played since the last New link.

The teddy bear's menu also has **Show link in game**, **New link** (old links stop working right away, and friends on the new one can't see earlier matches) and **Start with Windows**. Its first line shows the version, for bug reports.

When your game is paused, friends' buttons wait in line and run when you come back. Their page says so.

## Contests with match stats

Toy Box keeps score for everyone: players' kills, headshots, downs and revives, and for each friend, the zombies they sent, how many of those got killed, the downs they caused, and the bounties they set, won and lost.

Some ideas:
- **Who can take down the host?** Friends get 5 rounds each; most downs caused wins.
- **Bounty hunter.** Friends set bounties on each other's turns; most bounties won wins.
- **Survive the troll.** Everyone plays solo on the same map with a simulated friend on troll, wild; highest round wins.

To get the numbers:
- Friends see **Match stats** on their page during the match.
- After the match, **Host controls > Match history** has every match as **CSV** (one row per player and per friend, ready for a spreadsheet) or **JSON** (everything, with every command and the game's answer). Friends can download the ones played on the current link from their page too.
- The newest 100 matches are kept. Click the teddy bear and choose **Open match history folder** to find the files.

## The TOY BOX settings tab

In a Toy Box match or the main menu, go to **Options > Settings > TOY BOX**.

- **Friend controller:** on or off. When it's off, friends' buttons do nothing and their page says you turned it off.
- **Show link on screen** and **Copy link:** the friend link at the top of your screen again, or on your clipboard again.
- **Zombie eyes:** the map's own, orange, red, blue or purple, for everyone in the match.
- **Random events:** off, or a random event every 1, 2, 3 or 5 rounds.
- **Simulate a friend** and **Intensity:** see [Simulate a friend, in detail](#simulate-a-friend-in-detail).
- **Compatibility mode:** lets Toy Box use what other mods add (see [Compatibility](#compatibility-and-the-mod-api)).
- Under them: your friend link, whether it works from anywhere or only on your network, and who's on the controller right now.

Settings are saved for your next game. In a solo game the menu pauses the match, so the buttons take effect when you go back.

## Typing commands yourself

Everything your friends can do, you can type yourself.

1. In a match, open the console with the **~** key (the one under Esc).
2. Type `set tb help` and press Enter. The full list prints in the console.
3. Try a few:

   ```
   set tb give raygun
   set tb perk jug
   set tb spawn dog 4
   set tb zombies sprint
   set tb powerup insta drop
   set tb later 30 spawn zombie 10
   ```

Commands affect you by default. Add `@all`, a player number like `@2`, or part of a name like `@sam` to choose who: `set tb perk all @all` gives everyone every perk.

Bind them to keys: `bind F1 "set tb ammo"`. Every command is listed under [Commands](#commands).

## Installing without ToyBox.exe

The release also has a **mod-only zip**, for people who'd rather not run an exe. Without ToyBox.exe there's **no friend link**, but everything else works: the console commands, a simulated friend, eye colors, random events and the settings tab.

1. Press **Win + R**, type `%LOCALAPPDATA%\Plutonium\storage\t6\mods` and press Enter.
2. Unzip the mod-only zip there, so you have a `zm_toybox` folder containing `mod.json`, `mod.iwd` and `scripts`.
3. In game: **Mods > Toy Box**.

You can run ToyBox.exe later to add the friend link; it updates this same folder.

## Running on top of another mod

Plutonium loads one mod at a time, but scripts in the global scripts folder load under any mod. Toy Box can run there too, on top of someone else's mod.

1. Open `%LOCALAPPDATA%\Plutonium\storage\t6\scripts\zm` (create the folders if they're missing).
2. From the mod-only zip, copy every `toybox*.gsc` from `zm_toybox\scripts\zm` into it.
3. Also copy the four map folders (`zm_prison`, `zm_tomb`, `zm_highrise`, `zm_buried`) with the file inside each one.
4. Load the other mod as usual. ToyBox.exe finds the game under any mod.

The settings tab and eye colors need the zm_toybox mod itself, so use the console under another mod: `set tb remote link`, `set tb remote off`, `set tb simulate fair`. If Toy Box is installed both ways, it only starts once. To remove the global copy, delete those files.

## Privacy and safety

- The friend link holds a random secret key. Anyone with the link can control your match, nothing more. **New link** makes the old one stop working, and friends on the new link can't see matches from before it. Saved matches keep a fingerprint of the key they were played under, never the key itself.
- Host controls only answer your own PC, never the link.
- The link goes through a free Cloudflare Quick Tunnel, with no account. It runs only while the game is open and stops a minute after you close it.
- ToyBox.exe doesn't collect or send anything else. Settings, the log and match history stay in `%LOCALAPPDATA%\Toy Box` on your PC.
- The friend page and host controls load everything, fonts included, from ToyBox.exe itself, so a friend's browser only talks to your link.
- It installs only for your Windows user, with no administrator prompt. It starts with Windows, which you can switch off in the teddy bear's menu.
- Antivirus or SmartScreen may warn about it: the alpha isn't code-signed, and it includes Cloudflare's tunnel tool, cloudflared. The release page lists each file's SHA-256 so you can check your download.

## Reference

### Commands

Type them in the console as `set tb <command>`. Friends send the same commands from their page.

| Command | What it does |
|---|---|
| `help [command]` | Lists the commands in the console, or shows one command's usage |
| `give <weapon> [pap]` | Gives a weapon the way the game does; `pap` gives the upgraded one. A gun they already have is refilled, with the ka-ching |
| `take [weapon\|all]` | Takes the held gun, a named weapon, or every gun (fists are left, as in stock) |
| `pap` | Pack-a-Punches the held gun, with the machine's ready ding and the character's line |
| `ammo` | Max Ammo for that player, with the Max Ammo text and sound on their screen |
| `points <add\|take\|set> <amount>` | Changes points (`points 500` adds), with the purchase ka-ching and the score's +N/-N |
| `perk <name\|all\|random>` | Gives a perk, with the burp and the character's perk line |
| `unperk <name\|all>` | Takes a perk away |
| `powerup <name> [drop]` | Gives the player a power-up as a real pickup: the map's announcer, effect and HUD all play. With `drop` it lands where they're looking instead |
| `spawn <enemy> [count]` | Spawns enemies: `zombie`, `dog` (maps with hellhounds), and each map's own: `brutus` (Mob of the Dead, one at a time), `panzer` (Origins, up to 3), `leaper` (Die Rise), `ghost` (Buried Classic, up to 4) |
| `killall` | Kills every enemy alive, bosses and ghosts too, and stops Toy Box spawns still queued |
| `round <number>` | Ends the current round; that round comes next |
| `god [on\|off]` | Takes no damage |
| `revive` | Revives everyone who is down |
| `weapons`, `perks`, `powerups`, `enemies` | Lists what this map has |
| `power` | Turns the power on the way the map does: the switch on Die Rise and Buried, every generator on Origins, every perk machine on Mob of the Dead. On Origins each generator plays its capture sound |
| `doors` | Opens every door and debris pile money or power opens (and Buried's Sloth barricades). Quest doors stay shut |
| `box` | Moves the Mystery Box the way the teddy bear does: the laugh, the announcer, the box leaving and landing somewhere else |
| `firesale` | Starts a fire sale, on maps that have them (not TranZit or Die Rise) |
| `zombies sprint\|crawl\|health <x>\|freeze [s]\|slowmo [s]\|normal` | Every zombie sprints this round; every zombie loses its legs; zombie health times x this round; zombies frozen in place; slow motion for everyone; back to normal |
| `player speed <x> [s]\|gravity low\|normal\|ammo [s]\|onehit [s]\|ignore [s]\|teleport <player>\|normal` | Move speed times x; low gravity (everyone, until the round ends); every shot put back in the clip; one-hit kills (TranZit, Die Rise and Buried show the one-player Insta-Kill skull); zombies ignore the player; teleport next to another player; back to normal |
| `scare announcer [line]\|music\|shake\|flash\|fake [player]` | The announcer calling a power-up nobody got, the hellhound sting, a screen shake, the nuke's flash, or a power-up that turns out to be fake |
| `later <seconds\|nextround> <command>` | Runs any command later; `later list`, `later cancel <id>`. Like scares and the lists, a friend's `later` answers on their page but doesn't show on the host's screen |
| `events on\|off\|every <1\|2\|3\|5>\|now` | A random event every few rounds: sprinters, a fake power-up, hellhounds, low gravity, a boss... |
| `bounty <kills\|headshots\|knife\|explosive> [goal] [seconds] [reward]` | A challenge for a player, shown on their screen with a timer; points if they make it (1000 unless you give a reward). `bounty list`, `bounty cancel <id>`. With Points off for friends, a friend's bounty is for 0 points |
| `simulate off\|fair\|troll [chill\|normal\|wild]\|now` | A simulated friend (see [Simulate a friend, in detail](#simulate-a-friend-in-detail)). `simulate now` makes them act now. `bot` is the old name and still works |
| `eyes [default\|orange\|red\|blue\|purple]` | Changes the zombies' eye color for everyone, the ones already up too; `default` is the map's own. Needs the zm_toybox mod |
| `compat [on\|off]` | Shows or sets compatibility mode |
| `remote [on\|off\|link\|copy]` | Friend control: status, on, off, show the friend link again, or copy it again |
| `panic` | Undoes the chaos: stops Toy Box spawns, kills the enemies friends sent (hellhounds and bosses too), cancels what's scheduled, zombies and gravity back to normal. A simulated friend backs off for 90 seconds |

Names:

- Weapons use their real names (`ray_gun_zm`), the name without `_zm` (`ray_gun`), any unique part of one (`galil`), or a short name: `raygun`, `mk2`, `semtex`, `galva`, `paralyzer`, `sliquifier`.
- Perks use short names (`jug`, `qr`, `speed`, `dt`, `stamin`, `deadshot`, `mule`, `tombstone`, `whoswho`, `phd`, `cherry`, `vulture`) or real names (`specialty_armorvest`).
- Power-ups use real names (`full_ammo`) or short ones (`max`, `insta`, `double`, `firesale`, `perk`, `deathmachine`, `blood`).

How commands behave comes from the game's own scripts, not new numbers:

- `give`, `pap`, `ammo`, `perk` and `unperk` follow the wall buy, the Pack-a-Punch machine, the Max Ammo power-up, and the Free Perk and Lose Perk power-ups.
- `spawn zombie` follows the round spawner: same spawn spots, AI limit and spawn delay. Extra zombies don't count against the round, so the round lasts until they're dead too.
- `spawn dog` uses the call mixed rounds use, which allows 9 hellhounds alive at once; the rest wait for room.
- `round` and `killall` follow the developer menu's round skip. A skip keeps each map's special rounds on schedule (hellhounds, Jumping Jacks, Brutus, Panzers), and waits while one is running that can't be cut short.
- While a player's gear is put away (a Mob of the Dead ghost, a Die Rise Who's Who clone), commands that give or take guns and perks wait until they're back; points go to the score they'll get back.
- `zombies sprint` uses the game's own sprint; `crawl` is the game's leg gib; `freeze` holds zombies the way they're held while rising, slowed to a stop with the anim rate the Paralyzer (Buried) and the Ice Staff (Origins) send, and standing idle the way inert zombies do on other maps; `slowmo` is the killcam's slow motion; `onehit` is the per-player insta-kill; `ignore` is how Who's Who hides a player; `teleport` finds a spot the way a host migration does.
- Durations and sizes Toy Box picks itself (event lengths, bounty limits, low gravity at 40%, every simulated friend timing) are marked as Toy Box's own in the scripts.

### settings.json

`%LOCALAPPDATA%\Toy Box\settings.json`, made on first run. Host controls change most of these.

| Setting | Default | What it does |
|---|---|---|
| `key` | random | The secret part of the link. **New link** makes a new one, so old links stop working |
| `port` | 8787 | Local port; the next free one is used if it's taken |
| `tunnel` | `auto` | `auto` uses cloudflared when it's there; `none` never makes a public link |
| `lan` | `false` | `true` also gives a link for your home network, with no tunnel |
| `copy_link` | `true` | Puts the link on your clipboard when a match loads |
| `cooldown_seconds` | 0 | Time each friend must wait between commands, per connection (joining under a new name doesn't reset it); 0 is off |
| `allow_get_commands` | `false` | `true` lets a plain link send a command (for Stream Deck buttons and bots). Chat apps open links to preview them, so a pasted command link would run itself |
| `max_spawn` | 0 | Most enemies one `spawn` may ask for; 0 is no limit |
| `blocked` | `compat`, `remote`, `panic`, `bot`, `simulate`, `round`, `killall` | Commands friends can't use (`round` and `killall` can end a run in one press; unblock them in Host controls). A `later` command is checked for the command it schedules too. With `points` blocked, a friend's bounty can't have a reward above 0, and one with no reward gets 0 |
| `host_key` | random | The key for host controls, separate from `key` and never part of a friend link |
| `friends_off` | `false` | Pause friends: their commands are refused, joining still works |
| `notifications` | `true` | Pop-ups by the clock when the link is ready and when a friend joins |

### API

For bots, stream tools and overlays. Every call needs the key, as the `X-Toybox-Key` header or `?k=` in the URL.

| Call | Returns |
|---|---|
| `POST /api/join` with `{"name":"Sam"}` | `{"ok":true,"token":"…","name":"Sam"}`. `409` if someone on the page has that name or it's "Host", which the game uses (with or without spaces, `-` or `_` around it), `429` after 10 joins or renames from one address in a minute. Send the token as the `X-Toybox-Join` header (or `?j=`) on later calls; joining again with it and a new name renames you |
| `GET /api/state` | Connected or not, paused, map, round, zombies left, players with points, who's on the page (`controllers`) and, with a token, your name (`you`). Comes with an `ETag`: send it back as `If-None-Match` and the answer is a `304` with no body while nothing has changed |
| `GET /api/catalog` | This map's weapons, perks, power-ups, enemies and commands |
| `POST /api/command` with `{"command":"give raygun"}` and a token | `{"ok":true,"id":7}`, or an error. Without a token, give a `"name"` nobody on the page is using; with neither, `401`. `429` while 8 of that friend's commands (per token, or per address without one) or 50 in all are waiting for the game |
| `GET /api/command?k=KEY&name=Sam&cmd=give%20raygun` | The same, as one link, only with `allow_get_commands` on; otherwise `405` |
| `GET /api/log?since=0` | Recent commands with the game's answer, plus joins and renames (`kind`); pass the last `rev` to get only new ones |
| `GET /api/stats` | This match's stats so far: players (score, kills, headshots, downs, revives) and friends (commands, zombies sent, their zombies killed, downs caused, bounties set/won/lost, points given/taken). `match` is `null` if the match was over before the current link was made |
| `GET /api/history` | The saved matches played on the current link (the newest 100 are kept) |
| `GET /api/history/<id or current>?format=json\|csv` | One of those matches as a download (`404` for others): JSON has everything, with every command and the game's answer; CSV is one row per player and friend. Names starting with `=`, `+`, `-` or `@` get a leading `'` in the CSV, so spreadsheets don't run them as formulas |

- `/api/state` also has `versions`: the mod's and the app's bridge protocol, and which one to update when they differ. A newer app works with an older mod (newer features are hidden); an older app gets a "run ToyBox.exe again" on the host's screen.
- `/api/state`'s `game` lists `bounties`, `effects` (`{id,label,seconds_left}`: seconds, `-1` until the round ends, `0` until turned off), `scheduled` (`{id,when,command,by}`, `when` is seconds or `r<round>`), `events` (`{on,every,next_round,last}`) and `solo`, the simulated friend (`{mode,level}`: 0 off, 1 fair, 2 troll; 1 chill, 2 normal, 3 wild).
- A name is taken while its page is open. A page that stops checking in for 45 seconds leaves the list, and its name is free again. The friend page checks every 2 seconds during a match, less often (down to every 10 seconds) while the game isn't live, and every 20 seconds while its tab is hidden.
- Host controls are `/host` and `POST /api/host/*`. They answer only requests from this PC that didn't come through the tunnel, and the API also needs the `X-Toybox-Host` header with `host_key`. Host commands reach the game with the name `!host`, which no friend name can be. `POST /api/host/history` with `{"id":"…","format":"csv"}` downloads any saved match, including ones from before the current link.

How the game and the app talk: through files in the mod's `scriptdata` folder (Plutonium's `fs_*` functions); the format is at the top of `scripts/zm/toybox_remote.gsc`. The game reads commands 4 times a second while the app runs, and checks for it once a second while it doesn't.

### Compatibility and the mod API

Toy Box keeps working when other mods add content, and other mods can add to Toy Box.

**Two modes.** The dvar `tb_compat` picks one: the settings tab, `seta tb_compat 1` to keep it between games, or `set tb compat on` for one match.

- **Default (`tb_compat 0`): stock content only.** Built-in tables of what stock BO2 always has (perks with their short names, power-ups, enemy types), each checked against the running map, so nothing is offered where it doesn't exist. Weapons always come from the game's own list of what this map can give. Nothing is scanned.
- **Compatibility (`tb_compat 1`): stock content plus whatever mods add.** Once per match, the first time it's needed, Toy Box scans the perk machines and custom perks for ones it doesn't know, and accepts every power-up the map has. Commands, enemy types and short names other mods register are switched on.

**Performance.** No per-frame loops. The command input is read every 0.1 s, the compatibility scan runs once and is cached, and a simulated friend looks every 5 seconds.

**No function replacing.** Toy Box doesn't `replaceFunc` stock functions; another mod may replace the same ones, and two replacements can't both win. It calls the stock functions by path instead, so a mod that replaces one is used automatically.

**API for other mods.** `scripts/zm/toybox_api.gsc` is the public API, documented at the top of the file.

- `register_command( name, handler, usage, help, scope )` adds a command.
- `register_enemy( name, spawn_func, help )` adds an enemy type for `spawn`.
- `register_alias( kind, alias, real_name )` adds a short name for a weapon, perk or power-up.
- `register_origin( kind, name, "My Mod" )` names the mod a weapon, perk, power-up or enemy comes from, so the friend page lists it under that mod. `register_command` and `register_enemy` take the mod's name as an optional last argument too.
- `run_command( line, player )` runs a command from script.
- Every change Toy Box makes sends `level notify( "toybox_event", event, player, detail )`, e.g. `weapon_given`, `perk_given`, `enemy_spawned`, `round_set`.
- A mod that can live without Toy Box calls through `level.toybox_api`, which exists only when Toy Box is loaded:

  ```
  if ( isdefined( level.toybox_api ) )
      [[ level.toybox_api.register_command ]]( "boss", ::my_boss_command, "boss [count]", "spawns my boss" );
  ```

- A mod that requires Toy Box can call `scripts\zm\toybox_api::register_command( ... )` directly.
- Registered items run only in compatibility mode, and a mod can't replace a built-in command.

## Building from source

The source code goes up with the beta. Until then this page has the guide, and the releases have everything you need to play.

- **Build the eye colors:** `powershell -File tools\make_ff.ps1` builds `build\mod.ff` with [OpenAssetTools](https://github.com/Laupetin/OpenAssetTools)' Linker from your own copy of the game: it copies the game's eye effects in, then `tools\t6_ff_patch.py` renames and recolors the copies and checks each one against the effect it came from. Set `OAT_BASE` and `BO2_GAME` if OpenAssetTools or the game aren't in their default folders. The other steps below need this file.
- **Install the mod from the repo:** run `install.bat`. It copies `mod.json`, `scripts\` and `build\mod.ff` to `%LOCALAPPDATA%\Plutonium\storage\t6\mods\zm_toybox` and packs `ui\` into `mod.iwd` there. It refuses to run while the game is open. `install.bat global` and `install.bat unglobal` add and remove the global copy.
- **Check the scripts:** `python -I tools\check_gsc.py --stock <decompiled T6 zombies scripts>` finds what would stop the mod from loading: a call to a function that doesn't exist, a common script calling a function only one map has, too many arguments, a missing `;`. Without `--stock` it checks the syntax and calls between Toy Box's own scripts.
- **Build the friend page's art:** `python tools/make_art.py <dump folders>` (Pillow and numpy) takes the perk icons, the gold power-ups and the weapon pictures from your own copy of the game; its header has the OpenAssetTools commands for the dumps. `remote/art` is checked in, so you only need this to change it.
- **Build ToyBox.exe:** `powershell -File tools\make_app.ps1` builds `dist\ToyBox.exe` from `app\` (C# 5, compiled by the .NET Framework 4 compiler that comes with Windows, so there's nothing to install). It needs `remote\cloudflared.exe` (from `remote\get-cloudflared.bat`) and refuses one that isn't signed by Cloudflare.
- **Build a release:** `tools\make_release.ps1 [-InstallerUrl <url>] [-Test]` builds ToyBox.exe, signs it when `TOYBOX_SIGN` is set, writes winget manifests, and with `-Test` runs the tests first.
- **Tests:** `tests\app\test_server.ps1` runs the app and host controls against a fake game; `tests\app\test_installer.ps1` installs, updates and uninstalls in a temp folder. Each runs with one command and cleans up after itself.
- `ToyBox.exe /S` installs with no window (for winget).

Files:

- `mod.json`: the name shown in the Mods menu.
- `scripts/zm/toybox.gsc`: the command input, the built-in commands and the stock tables.
- `scripts/zm/toybox_api.gsc`: the public API for other mods.
- `scripts/zm/toybox_remote.gsc`: the game side of the friend link, and the link on screen.
- `scripts/zm/toybox_world.gsc`, `toybox_mods.gsc`, `toybox_fun.gsc`, `toybox_events.gsc`: the map, zombie and player modifiers, scares, and what runs over time (later, events, bounties, the effects list and match stats).
- `scripts/zm/toybox_bot.gsc`: the simulated friend.
- `scripts/zm/toybox_eyes.gsc`, `zone_source/mod.zone` and `tools/t6_ff_patch.py`: the zombie eye colors. Orange is the game's own eye. Red and blue are the Mob of the Dead and Buried eyes, copied so they work on every map. Purple is the orange eye recolored, and white is the orange eye's elements moved into the slot of another stock eye, since each copy needs its own source. `tools/t6_fx_read.py` reads effects out of a fastfile.
- `scripts/zm/<map>/`: what only exists on one map (Brutus, the Panzer, Jumping Jacks, Buried's ghosts, the Origins generators and staffs).
- `scripts/zm/toybox_origins.gsc`: which stock maps have each weapon, perk and power-up. Generated by `tools/make_origins.py` from a dump of the stock scripts; don't edit by hand.
- `ui/t6/options.lua`: the Options menu with the TOY BOX settings tab at the end.
- `app/`: ToyBox.exe: the installer, the tray app, the server for the friend page (`Remote.cs`, `RemoteHttp.cs`, `Tunnel.cs`, `History.cs`) and host controls (`RemoteHost.cs`, `host.html`).
- `remote/`: `page.html` (what friends see), and the older PowerShell companion, `toybox-remote.ps1`, kept as a development fallback.
- `release/README.txt`: the player guide that ships with the release.
- `tests/app/`: the tests, with `fake_game.ps1` standing in for the game.
- `tools/check_gsc.py`: the script checker. `.github/workflows/check.yml` runs it, compiles the app and parses every PowerShell script on each push.

## License

Toy Box is licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/): share it and build on it with credit, not for money, under the same license. [LICENSE.md](LICENSE.md) has the details and what it doesn't cover.

## Credits

- [Plutonium](https://plutonium.pw).
- The Options menu is built on BO2 Reimagined's decompile of the stock menu.
- [cloudflared](https://github.com/cloudflare/cloudflared) by Cloudflare (Apache 2.0) makes the friend link reachable from anywhere; its license ships with ToyBox.exe.
- The eye colors are built with [OpenAssetTools](https://github.com/Laupetin/OpenAssetTools).
- Fonts: [Barlow](https://github.com/jpt/barlow) and Barlow Condensed by Jeremy Tribby, [Black Ops One](https://fonts.google.com/specimen/Black+Ops+One) by James Grieshaber and Eben Sorkin (SIL Open Font License 1.1), [Permanent Marker](https://fonts.google.com/specimen/Permanent+Marker) by Font Diner (Apache 2.0). They ship inside ToyBox.exe with their licenses (`remote/fonts`).
- The app and tray icon is the Mystery Box teddy bear, rendered from Black Ops II zombies' own model and texture (`app/art`).
- The friend page's perk icons, power-ups and weapon pictures are Black Ops II's own, taken from the game's files by `tools/make_art.py` (`remote/art`).

Toy Box isn't affiliated with Activision, Treyarch or Plutonium.
