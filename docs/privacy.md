[← Back to Toy Box](../README.md)

# Privacy and safety

## The friend link

- It holds a random secret key.
- Anyone with it can control your match. Nothing more.
- **New link** makes the old one stop working.
- Friends on a new link can't see matches from before it.

## What Toy Box sends

- It doesn't collect or send anything about you.
- The friend link goes through a free Cloudflare Quick Tunnel, with no account.
- The tunnel runs only while the game is open, and stops a minute after you close it.
- The friend page loads everything, fonts too, from ToyBox.exe. A friend's browser only talks to your link.

## On your PC

- Settings, the log and match history stay in `%LOCALAPPDATA%\Toy Box`.
- Host controls only answer your own PC, never the link.
- It installs just for your Windows user. No administrator prompt.
- It starts with Windows. Switch that off in the teddy bear menu.

## Antivirus warnings

Antivirus or SmartScreen may warn about ToyBox.exe:

- The alpha isn't code-signed yet.
- It includes Cloudflare's tunnel tool, cloudflared.

The release page lists each file's SHA-256, so you can check your download.
