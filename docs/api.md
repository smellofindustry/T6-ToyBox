[← Back to Toy Box](../README.md)

# Web API

For bots, stream tools and overlays.

Every call needs the key from the friend link: the `X-Toybox-Key` header, or `?k=` in the URL.

## Join first

`POST /api/join` with `{"name":"Sam"}` returns `{"ok":true,"token":"…","name":"Sam"}`.

- Send the token as the `X-Toybox-Join` header (or `?j=`) on later calls.
- Joining again with the token and a new name renames you.
- `409`: someone on the page has that name, or it's "Host".
- `429`: more than 10 joins or renames from one address in a minute.

## Calls

| Call | Returns |
|---|---|
| `GET /api/state` | Connected or not, paused, map, round, zombies left, players with points, who's on the page, and your name (`you`) |
| `GET /api/catalog` | This map's weapons, perks, power-ups, enemies and commands |
| `POST /api/command` | Send `{"command":"give raygun"}` with a token. Returns `{"ok":true,"id":7}` or an error |
| `GET /api/command?k=KEY&name=Sam&cmd=give%20raygun` | The same as a link. Only with `allow_get_commands` on, otherwise `405` |
| `GET /api/log?since=0` | Recent commands with the game's answer, plus joins and renames. Pass the last `rev` to get only new ones |
| `GET /api/stats` | This match's stats for players and friends. `match` is `null` if it ended before the current link was made |
| `GET /api/history` | Saved matches played on the current link (newest 100) |
| `GET /api/history/<id or current>?format=json\|csv` | One of those matches as a download |

## Details

**Commands**
- Without a token, give a `"name"` nobody on the page is using. With neither, `401`.
- `429` while 8 of that friend's commands, or 50 in all, are waiting for the game.
- `429` when one of the host's limits says not yet. The error says when, like "Max Ammo: once every 3 rounds. Try again in round 8."

**State**
- Comes with an `ETag`. Send it back as `If-None-Match` to get a `304` while nothing has changed.
- `versions`: the mod's and the app's bridge protocol, and which to update when they differ.
- `game` lists `bounties`, `effects`, `scheduled`, `events` and `solo` (the simulated friend).
  - `effects`: `{id,label,seconds_left}`. `-1` means until the round ends, `0` until turned off.
  - `scheduled`: `{id,when,command,by}`. `when` is seconds, or `r<round>`.
  - `events`: `{on,every,next_round,last}`.
  - `solo`: `{mode,level}`. Mode 0 off, 1 fair, 2 troll. Level 1 chill, 2 normal, 3 wild.
  - `moments`: things that happen once, kept about 10 seconds so every page sees them. `{id,kind:"horde",player,kills,heads}` is a player getting more than 7 kills within 5 seconds (the game's own kill-streak rule). `{id,kind:"bot",name,command}` is a move by the simulated friend.
- `players` have `char` when the game says which character they are (its `characterindex`).
- `limits`: the host's limits, as they stand for you. `{label,text,each,all,match,seconds,rounds,uses,wait,next_round,left,use_times,use_rounds}`.
  - `match`: how the commands it covers start, like `ammo` or `powerup full_ammo`. `all`: it covers every command.
  - `wait`: seconds until it's ready. `next_round`: the round it's back, or 0. `left`: uses left this match, or `-1` with no cap.
  - `use_times` and `use_rounds`: when each use counted so far runs, in seconds from now (above 0 means it's scheduled for later) and as a round. A new use has to be a full cooldown away from all of them.

**Names**
- A name is taken while its page is open.
- A page that stops checking in for 45 seconds leaves the list, and its name is free again.
- The friend page checks every 2 seconds during a match, up to every 10 seconds while the game isn't live, and every 20 seconds while its tab is hidden.

**History**
- JSON has everything, with every command and the game's answer. CSV is one row per player and friend.
- In the CSV, names starting with `=`, `+`, `-` or `@` get a leading `'`, so spreadsheets don't run them as formulas.

## Host-only calls

- Host controls are `/host` and `POST /api/host/*`.
- They only answer requests from this PC that didn't come through the tunnel.
- The API also needs the `X-Toybox-Host` header with `host_key`.
- Host commands reach the game with the name `!host`, which no friend can use.
- `POST /api/host/history` with `{"id":"…","format":"csv"}` downloads any saved match, older links included.

## How the game and the app talk

Through files in the mod's `scriptdata` folder, with Plutonium's `fs_*` functions. The format is at the top of `scripts/zm/toybox_remote.gsc`.

The game reads commands 4 times a second while the app runs, and checks for the app once a second while it doesn't.
