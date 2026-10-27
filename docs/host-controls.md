[← Back to Toy Box](../README.md)

# Host controls

Click the teddy bear by the clock, then **Host controls**.

A page opens in your browser. It only works on your PC. Friends can't reach it.

![Host controls](images/host-controls.png)

## What's on it

- **Who's on:** everyone on the friend page. Kick or ban anyone.
- **What friends can use:** switch whole groups off, like spawning, weapons or god mode.
- **Limits:** a cooldown or a number of uses on one button, a group, or every command. For example "Max Ammo: once every 3 rounds" or "Kill All: 1 use per match".
- **Wait and spawn size:** a wait between each friend's commands, and the most zombies one spawn can send.
- **Events and a simulated friend:** switch them on or off.
- **Live now:** running bounties, effects and scheduled commands. Each has a cancel button.
- **A command box:** type any command. It runs as you.
- **Setups:** save how you like it and load it again later, or share it with a friend.
- **Match history:** every match, with what each friend did, as downloads.
- **Screen:** the friend page's 8-bit TV, bigger. It plays friends' moves and the simulated friend's, so it's fun when you play alone too. Click **Screen** at the top.

## The defaults

Out of the box, friends get nearly every button. A few stay yours: skipping rounds, Kill All, God Mode, everyone's eye color and random events. The rough ones are spaced out:

- Spawning, points, power-ups and Max Ammo: once every 20 or 30 seconds for each friend, and at most 10 zombies a spawn
- Take Gun: once a round
- Take Perks and Every Perk: once every 3 rounds
- Open doors: once a match
- Roulette: once a minute

Change any of it. **Use the defaults** next to **What friends can use** puts it all back.

## Limits

Under **What friends can use**, click **Add a limit**. Pick a button, a group or every command, then set any of these:

- **Once every N seconds**
- **Once every N rounds**
- **N uses per match**

Each limit is shared by all friends, or counted for each friend. Uses start over each match.

![Adding a limit in Host controls](images/host-limits.png)

## Setups

Set things up how you like, type a name under **Setups** and click **Save**. A setup keeps what friends can use, the limits, the wait, the spawn size, events, the simulated friend and the eye color.

- **Load** puts it all back. Events, the simulated friend and the eye color go in once a match is running.
- **Share** copies a code that starts with `TB1-`. Send it to a friend. They paste it under **Add a friend's setup**.
- To change one, load it, change things, then save it under the same name.
- **Rename** and **Delete** do what they say.

## Good to know

- Skipping rounds and killing everything are **off** for friends until you turn them on.
- With Points off, the bounties friends set are worth 0 points.
- Roulette never lands on what you've turned off for friends.
- Each friend can have 8 commands waiting at a time, so one fast clicker can't hold everyone up.
- Friends only see the matches played since the last **New link**.
- When your game is paused, friends' buttons wait in line and run when you're back.

---

## The settings file

For tinkerers. Host controls change most of these for you.

The file is `%LOCALAPPDATA%\Toy Box\settings.json`, made on first run.

| Setting | Default | What it does |
|---|---|---|
| `key` | random | The secret part of the link. **New link** makes a new one |
| `port` | 8787 | Local port. The next free one is used if it's taken |
| `tunnel` | `auto` | `auto` uses cloudflared when it's there. `none` never makes a public link |
| `lan` | `false` | `true` also gives a link for your home network, with no tunnel |
| `copy_link` | `true` | Copies the link when a match loads |
| `cooldown_seconds` | 0 | Wait between each friend's commands. 0 is off |
| `allow_get_commands` | `false` | `true` lets a plain link send a command (Stream Deck, bots). Chat apps preview links, so a pasted command link would run itself |
| `max_spawn` | 10 | Most enemies one `spawn` can ask for. 0 is no limit |
| `limits` | the defaults above | The limits from Host controls. Each has `what`, `each` (each friend, not shared), `seconds`, `rounds` and `uses` |
| `blocked` | `compat`, `remote`, `panic`, `bot`, `simulate`, `round`, `killall`, `eyes`, `god`, `events` | Commands friends can't use. A `later` command is checked for what it schedules too |
| `setups` | none | Your saved setups |
| `host_key` | random | The key for host controls. Never part of a friend link |
| `friends_off` | `false` | Pause friends. Joining still works |
| `notifications` | `true` | Pop-ups by the clock when the link is ready and when a friend joins |
