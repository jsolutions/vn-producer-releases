# VN Producer

A Windows desktop editor for making branching story games (visual novel, RPG and shooter mixed) in a 2.5D, Build Engine-style world, and playing them in **EDuke32** or **GZDoom**.

> **Beta.** Version 0.9.0 is the first public build. Everything works end to end, but expect rough edges, and back up your projects.

## What you can do with it

- **Plan your story as a map.** Main story events branch, side stories run in stages, and anytime events can happen whenever their conditions are met. Coloured chapter bands sit behind it all.
- **Make up your own stats** (e.g. Karma, or Trust with each character), items and remembered decisions. Name parts of a scale, such as Karma 50+ = "Saint".
- **Use prerequisites and effects** without writing code, e.g. "Karma ≥ 10 AND has Keycard AND chose 'Spared Dax'".
- **Write conversations by drag and drop:** lines, choices, condition branches and effects, as overlay text boxes or full-screen visual-novel scenes with portraits and backgrounds.
- **Connect the story to real maps.** Open Duke Nukem 3D–style maps, click a sprite or an area, and say "this is Mira", "this is the keycard" or "walking in here starts the next event". Give characters their own sprite images.
- **Add music and sound** per map, chapter or event, and sounds on dialogue lines.
- **Playtest inside the editor**, with live stats you can change. A Checks panel catches dead ends, unreachable events and broken references.
- **Export & Play** in one click. While a conversation is on screen, the game world pauses. The exported games also include a stats readout, an inventory screen, and characters that change behaviour as the story goes on.

## Download and install

1. Download **VN-Producer-0.9.0-beta-windows-x64.zip** from the [Releases page](../../releases).
2. Unzip it to a folder you'll keep, e.g. `Documents\VN Producer`.
3. Run **VN Producer.exe**. Windows may warn about an unrecognised app, because the app isn't code-signed yet. Choose **More info → Run anyway**.

The first time it runs, a setup wizard helps you find the tools it uses. None of these come with VN Producer:

| For | You need | Where to get it |
|---|---|---|
| EDuke32 games | EDuke32 and Mapster32 (free) | [eduke32.com](https://www.eduke32.com/) |
| | Duke Nukem 3D game data (`DUKE3D.GRP`) | your own copy, or the free shareware version |
| GZDoom games (optional) | GZDoom (free, open source) | [zdoom.org](https://zdoom.org/downloads) |
| | Doom game data | the free [Freedoom](https://freedoom.github.io/download.html) (`freedoom2.wad`) or your own `DOOM2.WAD` |

Then choose **New from sample** on the start screen and press **▶ Export & Play** to see a short demo story in the game.

## Help

The full guide is in [USER-GUIDE.md](USER-GUIDE.md), and it's also built into the app (the **Help** button).

## A note on selling games

Games made for **EDuke32** run on the Build engine, which can't be used commercially without a licence from its author. If you want to sell a game, export it to **GZDoom**, which is open source. VN Producer keeps your story independent of the engine, so you can switch at any time.

## Licence

VN Producer is free to download and use, including for games you make with it. The app itself may not be redistributed or sold. See [LICENSE.md](LICENSE.md).

Duke Nukem 3D, EDuke32, Mapster32, GZDoom, Doom and Freedoom belong to their respective owners. They aren't part of VN Producer, and it isn't affiliated with or endorsed by any of them.
