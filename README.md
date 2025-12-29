# Accessibility Plus

Accessibility Plus is a RuneLite plugin that improves accessibility and readability in Old School RuneScape by enhancing dialog UI and adding optional high-quality text-to-speech.

---

## Features

### Dialog Accessibility
- Large, readable dialog overlay
- Reliable detection of NPC and player dialog
- Full support for “Select an option” menus (NPCs, bankers, Grand Exchange)
- Collects and orders all dialog options correctly
- Overlay dynamically resizes and grows upward to prevent clipping
- Filters out:
  - Player chat (`Name: message`)
  - System messages (`Press Enter to Chat`)
  - Numeric junk, timers, and On/Off UI elements

### Minimap Accessibility
- Optional minimap shapes and indicators
- Does not recolor or modify the game itself, only draws overlays

### Text-to-Speech (Optional)
- Uses **Piper** for high-quality offline TTS
- Embedded local speech bridge starts automatically when TTS is enabled
- No dependency on other RuneLite plugins
- Fully offline once installed

---

## Text-to-Speech Overview (Important)

Accessibility Plus uses **Piper**, which is an offline text-to-speech engine.

Piper itself:
- Is a command-line program
- Does **not** run on a port
- Does **not** run in the background on its own

Accessibility Plus automatically starts an internal local “speech bridge” that:
- Listens on `127.0.0.1` (default port `59125`)
- Launches `piper.exe` when speech is requested
- Plays the generated audio

You only need to configure:
1. The path to `piper.exe`
2. The path to a Piper voice model (`.onnx`)

---

## Installing Piper (Windows)

1. Download Piper from:
   https://github.com/rhasspy/piper/releases

2. Extract the archive somewhere permanent, for example:
   `C:\piper\`

3. Confirm that this file exists:
   `C:\piper\piper.exe`

Piper does **not** need to be started manually.

---

## Voice Models

A Piper voice model is a file ending in `.onnx`.

Most voices require **two files** in the same folder:
- `<voice>.onnx`
- `<voice>.onnx.json`

Both files must remain together.

Voice models can be downloaded from:
https://github.com/rhasspy/piper/blob/master/VOICES.md

---

## Configuration

### Piper Executable Path
Full path to `piper.exe`.

Example:
`C:\piper\piper.exe`

### Voice Model Path
Full path to a `.onnx` file.

Example:
`C:\piper\models\en_US-lessac-medium.onnx`

The matching `.onnx.json` file must exist in the same directory.

---

## Enabling TTS

1. Enable **Enable TTS**
2. Set **TTS Backend** to **Bridge**
3. Set Piper executable path and voice model path
4. The embedded speech bridge starts automatically

---

## Troubleshooting

- Ensure `piper.exe` exists and is executable
- Ensure the `.onnx` and `.onnx.json` files both exist
- Ensure another plugin is not using the same bridge port

---

If Piper works from the command line, Accessibility Plus TTS will work.
