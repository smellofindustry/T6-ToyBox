[← Back to Toy Box](../README.md)

# Mod API and compatibility

Toy Box keeps working when other mods add content, and other mods can add to Toy Box.

## Two modes

The dvar `tb_compat` picks one. Set it in the settings tab, with `seta tb_compat 1` to keep it between games, or with `set tb compat on` for one match.

**Default (`tb_compat 0`): stock content only.**
- Built-in tables of what stock BO2 has: perks, power-ups, enemy types.
- Each is checked against the running map, so nothing is offered where it doesn't exist.
- Weapons always come from the game's own list for this map.
- Nothing is scanned.

**Compatibility (`tb_compat 1`): stock plus whatever mods add.**
- Once per match, Toy Box scans for perk machines and custom perks it doesn't know.
- Every power-up the map has is accepted.
- Commands, enemy types and short names other mods register are switched on.

## Built to share

- **No per-frame loops.** Commands are read every 0.1 s. The compatibility scan runs once and is cached. A simulated friend looks every 5 seconds.
- **No function replacing.** Toy Box doesn't `replaceFunc` stock functions. It calls them by path, so a mod that replaces one is used automatically.

## The API

`scripts/zm/toybox_api.gsc` is the public API, documented at the top of the file.

| Function | What it does |
|---|---|
| `register_command( name, handler, usage, help, scope )` | Adds a command |
| `register_enemy( name, spawn_func, help )` | Adds an enemy type for `spawn` |
| `register_alias( kind, alias, real_name )` | Adds a short name for a weapon, perk or power-up |
| `register_origin( kind, name, "My Mod" )` | Lists a weapon, perk, power-up or enemy under your mod's name on the friend page |
| `run_command( line, player )` | Runs a command from script |

- `register_command` and `register_enemy` also take your mod's name as an optional last argument.
- Every change Toy Box makes sends `level notify( "toybox_event", event, player, detail )`. Examples: `weapon_given`, `perk_given`, `enemy_spawned`, `round_set`.
- Registered items only run in mod compatibility mode. A mod can't replace a built-in command.

## Calling it

A mod that works without Toy Box calls through `level.toybox_api`, which only exists when Toy Box is loaded:

```
if ( isdefined( level.toybox_api ) )
    [[ level.toybox_api.register_command ]]( "boss", ::my_boss_command, "boss [count]", "spawns my boss" );
```

A mod that requires Toy Box can call `scripts\zm\toybox_api::register_command( ... )` directly.
