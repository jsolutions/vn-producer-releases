# VN Producer user guide

VN Producer lets you plan a branching story, write its conversations, connect them to places and characters in Duke Nukem 3D–style maps, and play the result in EDuke32.

## Getting started

1. **First run:** the setup wizard asks where EDuke32, Mapster32 (the map editor) and the game data (`DUKE3D.GRP`) are. The free shareware data works. You can change these later in **Settings**.
2. **Try the sample:** on the start screen, choose **New from sample** and pick an empty folder. It is a short story on the first level with every feature in use.
3. **Play it:** press **▶ Export & Play** at the top. EDuke32 opens on the first level.
4. **Start your own:** **New project** creates an empty project in a folder you choose. A project is an ordinary folder of files, so you can copy it, back it up or share it.

Everything saves automatically. **Undo** (Ctrl+Z) and **Redo** (Ctrl+Y) work everywhere, and the app keeps rolling backups inside the project folder.

## The tabs

### Systems: stats, items and decisions
- **Stats** are numbers (or yes/no, or a named choice) that the story tracks, such as *Karma* or *Trust*.
  - A stat is **global** (one value) or **per character** (each character has their own, e.g. *Trust with Mira*).
  - Tick **Show in the game's stats readout** to see it in the corner of the screen while playing. A whole-game switch below it turns the readout off.
  - **Named ranges** give parts of a number stat a name, e.g. Karma 50 to 100 = "Saint". The readout shows the name ("Karma: 60 (Saint)"), and prerequisites can test it: choose **is in range** as the comparison.
- **Items** are things the player carries, such as a keycard or medkits (with a maximum stack).
- **Decisions** are choices the story remembers, such as *Spared Dax*.

### Cast: characters and things
- **Characters** have a name, a colour for their name in dialogue, and portraits for different expressions.
- **Things** are what the story touches in the game world:
  - **NPCs** and **enemies** (optionally with health)
  - **pickups** (which can give an item)
  - **props**
  - **triggers** (areas)
- Give a Thing its own **sprite image**, and in the game it takes the place of whatever map sprite it's linked to. That's how a custom character appears in a map.
- **Behaviour in the game** switches how a Thing acts as the story changes:
  - **Acts normally** (enemies attack)
  - **Stands still** (won't move or attack)
  - **Gone** (hidden from the map)

  Set what it does normally, then add rules such as "if Karma is Shady, it acts normally". The first rule that holds wins.

### Story: the branching map
- **Events** are the beats of your story. Drag them around, and zoom with the mouse wheel.
  - **Main story** events branch.
  - **Side stories** are boxes of stages; use **+ Stage** to add the next one.
  - **Anytime** events can happen whenever their prerequisites pass.
- Each event has:
  - **outcomes** (e.g. *Helped her* / *Left her*)
  - **prerequisites** (e.g. *Karma ≥ 10 AND has Keycard*)
  - **effects** when it finishes
  - **scenarios**: how it starts in the game, such as talking to someone, walking into an area, picking something up, defeating something, a map starting, or automatically. Each scenario can name the conversation that plays.
- An event with **no scenarios** happens on its own as soon as it's available.
- **Paths:** drag from an outcome to another event to say what comes next. Click a path to give it an extra condition.
- **Chapters** are the coloured bands behind the map.
  - An event's chapter is the band it sits in.
  - You can't remove a chapter that still has events in it.
  - Side stories can be locked inside a chapter.

### Dialogue: conversations
- Drag pieces from the palette:
  - **Line**
  - **Choice** (choices can have conditions and effects)
  - **Condition branch**
  - **Effect**
  - **Jump** to another conversation
  - **End**
- An **End** can name an outcome (e.g. *Helped her*). If the event that played the conversation has an outcome with that name, it finishes with it.
- Drag a character onto a line to make them speak it. **Cast slots** let you reuse one conversation with different characters.
- Choose **Overlay** (a text box over the game) or **Full screen** (a visual-novel scene with a background).
- **Text limits:**
  - A line holds about 3 rows of 50 characters.
  - A question plus its choices must fit in 5 rows.
  - The editor warns you when something is too long.

### Scene: maps
- Add a map with **+ Map file**, or pick one of the game's own levels. Your maps appear in the game's first episode in the order listed here, and the game starts on the first one.
- Click a sprite or an area on the map, then link it to a Thing.
- **Open in Mapster32** to edit the map. When you save there, the Scene tab reloads, keeps links that moved, and flags any it can't find.

### Music: music and sounds
- Add music (OGG, WAV, FLAC or MIDI) and sounds (WAV, OGG, FLAC or VOC) to the library, and preview them with the play buttons (MIDI only plays in the game).
- Set where music plays:
  - **A map:** its music starts when the level begins (instead of the game's own).
  - **A chapter:** its music starts with each of the chapter's events.
  - **An event:** its own music overrides the chapter's.
- Give a dialogue line a **Sound** in the Dialogue tab; it plays when the line appears.
- In Playtest, tick **Play music and sounds** to hear them while you test.

### Playtest and Checks
- **Playtest** plays your story inside the editor.
  - Start from the beginning, or use **▶ Play from here** on any event or conversation.
  - Change stat values in the side panel to test "what if".
- **Checks** lists problems:
  - events nothing can reach
  - conditions that can never be true
  - conversations that dead-end
  - Things not placed on a map
  - and more

  Each one has a **Show** button that takes you to it.

## Exporting and playing

- **▶ Export & Play** builds the game and starts EDuke32. If EDuke32 reports a script problem, it's listed in the window.
- **Export…** lets you export without playing, and open the export folder (`export/eduke32` inside the project).
- The export lists anything it had to change, such as text that was too long or links it couldn't find on the map.

### Exporting to GZDoom (second engine)
- In the export window, choose **GZDoom**. The same story, conversations, stats, music and HUD export to a GZDoom mod in `export/gzdoom`.
- To play it, set up **GZDoom** and its game data (the free **Freedoom**, `freedoom2.wad`) in Settings, then press **▶ Export & Play**.
- Doom maps are made with Doom map editors (e.g. Ultimate Doom Builder), not Mapster32, so the Scene tab's links don't apply. Instead:
  - Give each map thing the **TID** shown on its Thing in the Cast tab (1000 + its number).
  - Give a walk-in area's sector a **tag** with the same number.
  - A Thing with its own sprite image replaces the map thing with its TID when the map starts, so any thing can stand in for a custom character.
  - The project's maps are **MAP01, MAP02, …** in the order of the Scene tab.
- Press **I** in GZDoom for the inventory screen.
- GZDoom is open source, which matters if you plan to sell the game.

### Controls in the game
- Walk up to someone, face them and press **Use** (E) to talk.
- **Use**, **Fire** or **Jump** shows the next line. **Forward/Back** (W/S) or the arrow keys pick a choice.
- While a conversation is open, the world is paused: enemies don't move or attack, and you can't be hurt.
- Press **Inventory** (Enter) to see what you're carrying; press it or **Use** again to close. The world pauses while it's open.
- Story progress is kept in ordinary EDuke32 save games.

## Tips
- **Images:**
  - Portraits and backgrounds can be PNG or JPEG.
  - EDuke32's classic look uses 256 colours, so images may look slightly different in the game. The OpenGL renderer shows them in full colour.
  - Keep images modest in size (e.g. portraits around 200 pixels tall, backgrounds 640×400).
- **NPC placeholders:** to place an NPC, put any sprite in your map with Mapster32 where they should stand, link it to the NPC in the Scene tab, and give the NPC a sprite image. Pick a sprite that stays in the level (not an effect or debris).
- **Selling the game:** the Build engine's licence doesn't allow commercial use without permission. VN Producer keeps your story engine-neutral, so it can be exported to other engines later.

## Troubleshooting
- **"Couldn't read its log":** EDuke32 probably started, but VN Producer couldn't confirm the scripts loaded. Look at the EDuke32 window.
- **A conversation doesn't start:**
  - Check the event's prerequisites in Playtest (is it in "Can happen now"?).
  - Check that the Thing is linked on the map (the Checks tab says so if it isn't).
- **A tool moved:** the banner at the top tells you. Fix the path in Settings.
