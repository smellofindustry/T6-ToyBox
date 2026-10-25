[← Back to Toy Box](../README.md)

# Installing without the exe

The release also has a **mod-only zip**, for people who'd rather not run an exe.

Without ToyBox.exe there's **no friend link**. Everything else works: console commands, a simulated friend, eye colors, random events and the settings tab.

## Install

1. Press **Win + R**, type `%LOCALAPPDATA%\Plutonium\storage\t6\mods` and press Enter.
2. Unzip the mod-only zip there. You should have a `zm_toybox` folder with `mod.json`, `mod.iwd` and `scripts` inside.
3. In the game: **Mods > Toy Box**.

You can run ToyBox.exe later to add the friend link. It updates this same folder.

---

## Running on top of another mod

Plutonium loads one mod at a time. Scripts in the global scripts folder load under any mod, so Toy Box can run there too.

1. Open `%LOCALAPPDATA%\Plutonium\storage\t6\scripts\zm`. Make the folders if they're missing.
2. From the mod-only zip, copy every `toybox*.gsc` from `zm_toybox\scripts\zm` into it.
3. Also copy the four map folders (`zm_prison`, `zm_tomb`, `zm_highrise`, `zm_buried`) with the file inside each one.
4. Load the other mod as usual. ToyBox.exe finds the game under any mod.

Good to know:

- The settings tab and eye colors need the zm_toybox mod itself. Under another mod, use the console: `set tb remote link`, `set tb remote off`, `set tb simulate fair`.
- If Toy Box is installed both ways, it only starts once.
- To remove the global copy, delete those files.
