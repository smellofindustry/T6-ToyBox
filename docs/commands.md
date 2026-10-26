[← Back to Toy Box](../README.md)

# Console commands

Everything your friends can do, you can type yourself.

## Try it

1. In a match, open the console with the **~** key (under Esc).
2. Type `set tb help` and press Enter. The full list prints.
3. Try a few:

```
set tb give raygun
set tb perk jug
set tb spawn dog 4
set tb zombies sprint
set tb powerup insta drop
set tb later 30 spawn zombie 10
```

## Who it affects

Commands affect you unless you add a target:

- `@all`: everyone
- `@2`: player 2
- `@sam`: anyone whose name has "sam" in it

Example: `set tb perk all @all` gives everyone every perk.

## Bind to a key

`bind F1 "set tb ammo"`

---

## All commands

Type them as `set tb <command>`. Friends send the same commands from their page. Limits and switches in [Host controls](host-controls.md) only hold friends back, never you.

### Gear

| Command | What it does |
|---|---|
| `give <weapon> [pap]` | Gives a weapon. `pap` gives the upgraded one. A gun they have is refilled |
| `take [weapon\|all]` | Takes the held gun, a named one, or every gun |
| `pap` | Pack-a-Punches the held gun |
| `ammo` | Max Ammo for that player |
| `points <add\|take\|set> <amount>` | Changes points. `points 500` adds |
| `perk <name\|all\|random>` | Gives a perk |
| `unperk <name\|all>` | Takes a perk away |
| `powerup <name> [drop]` | A real power-up. `drop` lands it where they're looking |
| `god [on\|off]` | Takes no damage |
| `revive` | Revives everyone who's down |

### Enemies and rounds

| Command | What it does |
|---|---|
| `spawn <enemy> [count]` | `zombie`, `dog` (TranZit), `brutus` (Mob of the Dead), `panzer` (Origins), `leaper` (Die Rise), `ghost` (Buried Classic) |
| `killall` | Kills every enemy, bosses too |
| `round <number>` | Ends this round. That round comes next |

### The map

| Command | What it does |
|---|---|
| `power` | Turns the power on, the way the map does |
| `doors` | Opens every door and debris pile. Quest doors stay shut |
| `box` | Moves the Mystery Box, teddy bear laugh and all |
| `firesale` | Starts a fire sale (not on TranZit or Die Rise) |

### Tricks and scares

| Command | What it does |
|---|---|
| `zombies sprint` | Every zombie sprints this round |
| `zombies crawl` | Every zombie loses its legs |
| `zombies health <x>` | Zombie health times x this round |
| `zombies freeze [s]` | Zombies frozen in place |
| `zombies slowmo [s]` | Slow motion for everyone |
| `zombies normal` | Back to normal |
| `player speed <x> [s]` | Move speed times x |
| `player gravity low\|normal` | Low gravity for everyone, until the round ends |
| `player ammo [s]` | Every shot put back in the clip |
| `player onehit [s]` | One-hit kills |
| `player ignore [s]` | Zombies ignore the player |
| `player teleport <player>` | Teleports next to another player |
| `player normal` | Back to normal |
| `scare announcer [line]` | The announcer calls a power-up nobody got |
| `scare music` | The hellhound sting |
| `scare shake` | A screen shake |
| `scare flash` | The nuke's flash |
| `scare fake [player]` | A power-up that turns out to be fake |

### Over time

| Command | What it does |
|---|---|
| `later <seconds\|nextround> <command>` | Runs a command later. `later list`, `later cancel <id>` |
| `events on\|off\|every <1\|2\|3\|5>\|now` | A random event every few rounds |
| `bounty <kills\|headshots\|knife\|explosive> [goal] [seconds] [reward]` | A timed challenge for points (1000 unless you set a reward). `bounty list`, `bounty cancel <id>` |
| `simulate off\|fair\|troll [chill\|normal\|wild]\|now` | A [simulated friend](play-alone.md). `bot` still works too |

### Toy Box itself

| Command | What it does |
|---|---|
| `help [command]` | Lists the commands, or shows one command's usage |
| `weapons`, `perks`, `powerups`, `enemies` | Lists what this map has |
| `eyes [default\|<color>\|<hex color>]` | Zombie eye color for everyone: yellow, orange, red, crimson, pink, magenta, purple, deep blue, blue, pale blue, teal, green or lime. A hex color like `ff66cc` gets the closest one. Needs the zm_toybox mod |
| `compat [on\|off]` | Compatibility mode ([more](mod-api.md)) |
| `remote [on\|off\|link\|copy]` | The friend link: status, on, off, show it, copy it |
| `panic` | Undoes the chaos. A simulated friend backs off for 90 seconds |

---

## Short names

- **Weapons:** the real name (`ray_gun_zm`), without `_zm` (`ray_gun`), any unique part (`galil`), or a short name: `raygun`, `mk2`, `semtex`, `galva`, `paralyzer`, `sliquifier`.
- **Perks:** `jug`, `qr`, `speed`, `dt`, `stamin`, `deadshot`, `mule`, `tombstone`, `whoswho`, `phd`, `cherry`, `vulture`, or the real name (`specialty_armorvest`).
- **Power-ups:** `max`, `insta`, `double`, `firesale`, `perk`, `deathmachine`, `blood`, or the real name (`full_ammo`).

## How they work

Every command follows the game's own scripts. No made-up numbers.

- `give`, `pap`, `ammo`, `perk` and `unperk` work like the wall buy, the Pack-a-Punch machine, the Max Ammo, and the Free Perk and Lose Perk power-ups.
- `spawn zombie` uses the round spawner: same spawn spots, AI limit and delay. Extra zombies don't count toward the round, so the round lasts until they're dead too.
- `spawn dog` allows 9 hellhounds alive at once, like mixed rounds. The rest wait for room.
- `round` and `killall` work like the developer menu's round skip. Special rounds (hellhounds, Jumping Jacks, Brutus, Panzers) stay on schedule.
- While a player's gear is put away (a Mob of the Dead ghost, a Who's Who clone), gun and perk commands wait until they're back.
- `sprint` is the game's own sprint. `crawl` is the leg gib. `freeze` holds zombies the way they're held while rising. `slowmo` is the killcam's slow motion. `onehit` is the one-player Insta-Kill. `ignore` is how Who's Who hides you.
- Numbers Toy Box picks itself (event lengths, bounty limits, low gravity at 40%, simulated friend timing) are marked as Toy Box's own in the scripts.
