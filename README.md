<p align="center"><img src="assets/dylotts_logo.png" width="180"></p>

<h1 align="center">DYLO TTS</h1>

<p align="center">A browser based text to speech studio for Unreal Engine, with voice cloning and voice design, exporting SoundWave and SoundCue assets directly into your project.</p>

---

DYLO TTS runs entirely on your own machine. Generate speech with built in voices, clone voices from your own audio, design brand new voices from a text description, and export everything straight into your project as SoundWave and SoundCue assets.

## Contents

- [Requirements](#requirements)
- [Getting Started](#getting-started)
  - [Install](#install)
  - [First Launch](#first-launch)
  - [Your First Generation](#your-first-generation)
- [The Studio](#the-studio)
  - [Custom Voice](#custom-voice)
  - [Voice Clone](#voice-clone)
  - [Voice Design](#voice-design)
  - [Output Panel](#output-panel)
- [Voice Library and Voice Packs](#voice-library-and-voice-packs)
- [Importing to Unreal](#importing-to-unreal)
- [Standalone Mode](#standalone-mode)
- [Where Things Are Stored](#where-things-are-stored)
- [FAQ](#faq)
- [Troubleshooting](#troubleshooting)
- [Change Log](#change-log)
- [Support](#support)

## Requirements

| | |
|---|---|
| **OS** | Windows 10 or 11, 64 bit |
| **Engine** | Unreal Engine 5.0, 5.5, 5.6, or 5.7 |
| **Disk** | About 20 GB free for the one time studio install |
| **GPU** | NVIDIA GPU strongly recommended (generation runs on your GPU) |
| **Browser** | Any modern browser (Chrome, Edge, Firefox) |

## Getting Started

### Install

1. Install DYLO TTS from Fab into your engine, or place the `DYLOTTS` folder into your project's `Plugins` folder.
2. Open your project. Make sure the plugin is enabled under **Edit, Plugins, Audio**.

### First Launch

1. Click the **DYLO TTS** button in the main toolbar.
2. The first launch installs the studio: an **Installing DYLO TTS** window appears and downloads the studio and voice models (about 9.5 GB, two steps). You can minimize it and keep working.
3. When the install finishes, your browser opens the studio at `127.0.0.1:5050`.

That is it. Every later click on the toolbar button launches (or reconnects to) the studio instantly.

### Your First Generation

1. In the studio, pick a voice in the **Custom Voice** tab.
2. Type a line of dialogue and press **Generate**.
3. The clip appears in the **Output** panel on the right. Click the waveform to play it.
4. Right click the clip and choose **Create SoundWaves** to import it into your project under `Content/DYLOTTS/`.

## The Studio

The studio runs in your browser and has three generation tabs plus the Output panel.

### Custom Voice

Generate speech with built in speakers or any voice from your Voice Library. Pick a voice, type text, and Generate. Modifiers (emotion, delivery, accent, age, and more) shape the read without changing the voice.

### Voice Clone

Clone a voice from your own reference audio.

1. Upload one or more reference clips (a clean 10 to 30 second sample works well) and the spoken text of the sample.
2. Generate with any text. Save voices you like to the Voice Library with their own name.

The Voice Library inside this tab lists your saved voices: search, rename, set descriptions, favorite, and right click for more actions.

### Voice Design

Describe a voice in plain language ("a gravelly old sea captain, slow and warm") and generate candidates. Save the ones you like to the Voice Library and use them anywhere.

### Output Panel

Every generation lands here, newest first, grouped by prompt.

- **Play**: click a waveform to play from that position, or use the play button.
- **Select**: click a clip to select it. Ctrl click toggles individual clips, Shift click selects a range, clicking an entry header selects that whole generation. Holding Ctrl or Shift while clicking a waveform selects without playing.
- **Right click** a clip (or selection) for actions: create Unreal assets, adjust volume, auto balance, save as a new voice, copy text, and more.
- **Volume**: right click, Adjust volume gives a live preview with clipping warnings. Auto balance levels a clip (or every selected clip) automatically.
- **Like** generations with the heart to mark keepers.

## Voice Library and Voice Packs

Saved voices live in the Voice Library, shared by every project on your machine.

- **Save** a voice from the Voice Clone tab, or right click any Output clip and choose **Save as new voice**.
- **Preview** a voice with its play button or waveform strip.
- **Rename** (including case only renames), **edit descriptions** (right click), and **favorite** voices to pin them at the top of pickers.
- Voices are grouped (Built In, Demo, Saved) in the Custom Voice dropdown, with search.

**Voice packs** are folders of voices you can share or back up.

- Open the packs folder from the Custom Voice dropdown footer.
- Export a group of voices to a pack, or drop a pack folder in and refresh to load it.

## Importing to Unreal

With your project open, the studio talks to the editor directly. The connection dot in the right click menu shows **Unreal connected** when the editor is reachable.

### Create SoundWaves and SoundCues

Right click any Output clip (or a multi selection) and choose:

- **Create SoundWaves**: imports each selected clip as a `SW_` SoundWave asset.
- **Create SoundCues**: also creates a `SC_` SoundCue per clip that plays its wave.
- **Create Both**: waves plus cues.

Assets land under `Content/DYLOTTS/Characters/<Voice>/`, grouped into a folder per phrase, with spoken text attached as asset metadata.

### Single Cue (one cue, many takes)

Select two or more clips, right click, and choose **Create Single Cue**. This builds ONE SoundCue where every selected take feeds a **Random** node, perfect for bark variations that should play randomly at runtime.

- A naming pop up suggests the next free name (`CombinedCue_01`, `02`, ...), so repeat runs never overwrite. `SC_` is added automatically.
- If all selected takes are from the same generation, the cue lands in that phrase's folder. Mixed selections land in `CombinedCues/01`, `02`, ... with each cue and its waves in their own numbered folder.

### Unreal Content Panel

The **Unreal Content** panel inside the studio mirrors your `Content/DYLOTTS` folder:

- Browse folders, search, and play imported assets without leaving the browser.
- Rename (F2), delete files or whole folders (folders are removed completely), and jump to an asset in the Content Browser.
- Right click folders for expand and collapse, clear all generations in a folder, rename, and delete.

## Standalone Mode

DYLO TTS works without the Unreal editor.

After the first install, a Start Menu shortcut is created: **DYLO Gaming, DYLO TTS**. Launching it starts the studio in your browser, no editor needed.

Everything works the same: generate, clone, design, manage your Voice Library, and adjust output. Anything that needs the editor (creating SoundWave or SoundCue assets, the Unreal Content panel) simply waits until a project with the plugin is open. The right click menu shows **Unreal not reachable** until then.

Generations made standalone land in the same `Documents\DYLO TTS\output\` and are right there the next time you open the studio from inside Unreal.

## Where Things Are Stored

| What | Where |
|---|---|
| Saved voices | `Documents\DYLO TTS\voices\` |
| Generations | `Documents\DYLO TTS\output\` |
| Voice packs | `Documents\DYLO TTS\Voice Packs\` |
| Studio install | `%LOCALAPPDATA%\DYLOGaming\DYLOTTS\` |
| Imported Unreal assets | `Content/DYLOTTS/` inside your project |

## FAQ

**Does it run locally? Is anything sent to the cloud?**
Everything runs on your machine. Speech generation happens on your own GPU. The only network use is the one time download of the studio and models on first launch.

**Do I need an internet connection?**
Only for the first launch download (about 9.5 GB). After that, DYLO TTS works fully offline.

**What hardware do I need?**
Windows 10 or 11 (64 bit), about 20 GB of free disk space, and an NVIDIA GPU is strongly recommended for generation speed. The studio itself runs in your default browser.

**Which engine versions are supported?**
Unreal Engine 5.0, 5.5, 5.6, and 5.7 on Windows.

**Where do my generations and voices live?**
In `Documents\DYLO TTS\` (outputs, saved voices, editor projects). The studio install itself lives in `%LOCALAPPDATA%\DYLOGaming\DYLOTTS\`.

**Can I use the generated audio commercially?**
Yes, audio you generate is yours to use in your projects. When cloning a voice, make sure you have the rights to the source audio you use.

**Why is the first launch slow?**
The first click downloads and installs the studio (about 9.5 GB) and the first generation loads the model into your GPU. Every launch after that is fast.

**Do multiple projects share one install?**
Yes. The studio installs once per machine and every project with the plugin uses the same install and the same voice library.

**How do I uninstall?**
Use the Uninstall action in the plugin's toolbar dropdown inside Unreal. It removes the studio install and the Start Menu shortcut. Your generations in `Documents\DYLO TTS\` are kept unless you delete them yourself.

## Troubleshooting

**The first launch download fails or stalls**
Check your connection and disk space (about 20 GB free), then click the toolbar button again, the installer resumes with a fresh attempt. If a firewall prompt appears, allow it: the studio serves your own browser on `127.0.0.1` only.

**The browser opens but shows nothing or an old looking page**
Hard refresh the tab with `Ctrl+Shift+R`.

**"Unreal not reachable" in the right click menu**
The editor with the plugin must be running. The studio talks to it on local port `5051`; the studio itself runs on `5050`. Both are localhost only. If another app occupies these ports, close it and relaunch.

**Generation is slow or fails**
The first generation after a launch loads the model into your GPU and takes the longest. Without an NVIDIA GPU, generation may be very slow. Check the studio's system panel for VRAM usage.

**The studio closed by itself**
The studio shuts down shortly after the browser tab and editor are both closed. This is by design. Launch it again from the toolbar button or the Start Menu shortcut.

**A second editor or machine**
One studio install serves the whole machine; a second editor instance attaches to the same studio rather than starting another.

**Reinstall from scratch**
Delete `%LOCALAPPDATA%\DYLOGaming\DYLOTTS\` and click the toolbar button: the studio re downloads cleanly. Your voices and outputs in `Documents\DYLO TTS\` are untouched.

**Still stuck?**
Email dylogamingofficial@gmail.com with your `Saved/Logs/<Project>.log` and a short description.

## Change Log

### 1.0.0

Initial release.

- Browser based studio with three generation modes: Custom Voice, Voice Clone, and Voice Design
- Voice Library with favorites, search, descriptions, and voice packs
- Output panel with per clip waveforms, volume adjust, auto balance, likes, and tagging
- One click export to Unreal as SoundWave and SoundCue assets
- Single Cue: combine multiple takes into one SoundCue with a Random node
- Unreal Content panel inside the studio: browse, play, rename, and delete your generated assets without leaving the browser
- Standalone mode via a Start Menu shortcut, no editor required
- Supported engine versions: 5.0, 5.5, 5.6, 5.7 (Windows 64 bit)

## Support

Questions or issues: dylogamingofficial@gmail.com
