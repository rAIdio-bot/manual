## Simple

### What is the Editor?

The Editor is where you fine-tune any audio clip. Trim the start and end, cut out sections you do not want, add fades, boost the volume, and apply real-time effects like reverb or EQ. Think of it as the place where you polish your audio before it goes into a mix or out into the world.

### Loading Audio

There are several ways to load audio into the Editor:

- Double-click any file in the Assets panel.
- Use **Open in Editor** from the Music tab after generating a song.
- Drag and drop a file onto the Editor waveform.

The Editor supports WAV, MP3, OGG, FLAC, AIFF, M4A, and WMA files.

### Selecting and Editing

Click and drag on the waveform to select a region. The selected area lights up. Then use the toolbar buttons:

| Tool | What it does |
|------|--------------|
| Trim | Keep only the selected part, remove everything else |
| Cut | Remove the selected part, keep the rest |
| Fade In | Gradually bring the volume up from silence |
| Fade Out | Gradually bring the volume down to silence |
| Normalize | Make the audio as loud as possible without distortion |
| Delete | Remove the selection |

Every edit can be undone with **Undo** and redone with **Redo**.

### Effects

The FX sidebar has 10 audio effects. Click the dot next to an effect to turn it on or off. Click the effect name to expand its controls and adjust the settings.

The effects are: Envelope, Gate, High Pass, EQ, Compressor, Saturation, Bitcrusher, Stereo Width, Delay, and Reverb. You do not need to know what all of these do right away. Experiment and listen to what changes.

### Speed and Pitch

Above the transport controls, you will find Speed and Pitch sliders.

- **Speed** changes how fast the audio plays without changing the pitch.
- **Pitch** shifts the audio up or down without changing the speed.

Adjust them and listen in real time, then click **Apply** to make the change permanent. Click **Reset** to go back to normal.

### Saving Your Work

- **Save** — Saves an edited copy to your Music folder. Your original file is never overwritten.
- **Save As** — Pick a name and location.
- **Send to Mixer** — Load the clip into the next empty mixer channel.
- **Send to Playlist** — Add it to the Play tab's playlist.

### Chord Detection

Chords are detected automatically when you extract stems, or you can right-click any audio file in the Assets panel and choose **Detect Chords**. A colored bar above the waveform shows the detected chord progression. Toggle it on or off with the Chords button in the toolbar. Chord detection takes under 10 seconds on CPU for a 3-minute stem.

### MIDI Export (Early Access)

Click **Export MIDI** to convert the current clip to a MIDI file using Spotify basic-pitch, a neural music transcription model. You can also right-click any audio file in Assets and choose **Export MIDI**. Accuracy is highest on isolated melody and bass stems. MIDI files appear in the Assets panel under the MIDI category.

*This feature is incomplete for Early Access. Output is approximate and may require cleanup in a DAW.*

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Space | Play/Pause |
| L | Toggle Loop |
| Ctrl+A | Select All |
| Ctrl+Z / Ctrl+Y | Undo / Redo |
| Ctrl+C / Ctrl+X / Ctrl+V | Copy / Cut / Paste |
| Ctrl+S | Save |
| Home / End | Jump to Start / End |
| ← / → | Jog playhead 0.01s |
| Shift+← / → | Jog playhead 0.1s |
| + / − | Zoom In / Out |
| F | Zoom Fit |
| Delete | Delete Selection |
| Esc | Clear Selection |

## Advanced

### Waveform Display

Stereo waveform with left channel above the center line and right channel below. Click anywhere to move the playhead. Click and drag to create a selection. Drag the selection handles to resize.

The time ruler scales with zoom. Playback position is shown as a vertical line that tracks in real time.

### Editing Tools

All operations work on the current selection:

- Trim: Removes everything outside the selection.
- Cut: Removes the selection and closes the gap.
- Fade In: Applies a linear volume ramp from silence to full over the selected region.
- Fade Out: Applies a linear volume ramp from full to silence.
- Normalize: Peak-normalizes the entire clip to -3 dB headroom.
- Delete: Removes the selection or clears the clip if nothing is selected.
- Copy/Paste: Standard clipboard operations on selected audio.
- Undo/Redo: Full edit history. Each operation is a separate undo step.

### Effects Chain (13 Effects)

Effects are processed in two stages:

Mono chain (applied first, per-sample):
1. Volume Envelope: ADSR-style gain modulation over time.
2. Noise Gate: Mutes audio below a threshold. Use to remove background noise between phrases.
3. High Pass Filter: Cuts frequencies below the cutoff. Removes low-frequency rumble and mud.
4. Three-Band EQ: Shelving EQ with low, mid, and high bands. Each band has gain control.
5. Compressor: Reduces dynamic range. Threshold sets the level where compression starts; ratio controls how much.
6. Soft Saturation: Adds harmonic warmth. Subtle at low drive, distorted at high drive.
7. Bitcrusher: Reduces bit depth for lo-fi effect. Lower values produce more extreme quantization.

Stereo chain (applied after, per-frame):
8. Stereo Widener: Widens or narrows the stereo image.
9. Delay: Echo effect with feedback, delay time, and LR pan.
10. Reverb: Room ambience with decay time and wet/dry mix.

Click the LED dot to enable/disable. Click the name to expand. Effects apply in real time during playback.

### Speed and Pitch

- Speed: 0.25x to 2.0x. Uses ffmpeg's atempo filter (preserves pitch).
- Pitch: -12 to +12 semitones. Uses rubberband filter (preserves duration).
- When both are set, rubberband handles both in a single pass.

Click Apply to process with ffmpeg. A new file is created with an _edited suffix; the original is preserved. Click Reset to return sliders to neutral (1.0x speed, 0 semitones).

### Playback

The Editor plays your clip in isolation. Use the channel strip (fader, pan, mute, VU meter) to adjust how it sounds. When you're happy, send it to the Mixer for further processing.

### Saving and Export

- Save: Creates a copy in your Music folder (Documents/rAIdio.bot/Music/). The original file is never overwritten.
- Save As: Choose a custom name and location.
- Send to Mixer: Loads the clip into the next empty mixer channel.
- Send to Playlist: Adds to the Play tab's playlist.
- Extract and Mix: Runs Demucs stem separation and loads all stems into the Mixer on separate channels.

All saved files receive metadata sidecars and C2PA signatures.

### Chord Detection

Chord progression detection runs automatically after stem extraction, or you can right-click any audio file in the Assets panel and choose Detect Chords. Results are displayed as a 24px bar between the time ruler and the waveform canvas. Each chord segment uses alternating purple shades so boundaries are readable without hard dividers. The bar scrolls and zooms in sync with the waveform.

Chord data is persisted as a .chords.json sidecar alongside the audio file, so it survives app restarts without re-analysis. Toggle the overlay with the Chords toolbar button.

For best accuracy, run chord detection on the full mix or individual stems rather than the residual "Other" stem, which may produce suspended chord variants due to missing harmonic context.

Performance: under 10 seconds on CPU for a 3-minute stem.

### MIDI Export (Early Access)

Click Export MIDI to transcribe the current clip to a MIDI file. You can also right-click any audio file in the Assets panel and choose Export MIDI. Uses Spotify basic-pitch, a neural polyphonic music transcription model (Apache 2.0, ONNX backend). Accuracy is highest on isolated melody and bass stems; complex harmonic or heavily reverbed material may produce less accurate results.

If a MIDI file already exists for the current clip, you can open the existing file or regenerate it. MIDI files are saved to Documents/rAIdio.bot/Library/Midi/ and appear in the Assets panel under the MIDI category.

This feature is incomplete for Early Access. MIDI output is approximate and will likely require manual cleanup in a DAW. Both chord detection and MIDI transcription run automatically in the background after stem extraction.

### Keyboard Shortcuts

- Space: Play/Pause
- L: Toggle Loop
- Ctrl+A: Select All
- Ctrl+Z: Undo | Ctrl+Y / Ctrl+Shift+Z: Redo
- Ctrl+C: Copy | Ctrl+X: Cut | Ctrl+V: Paste
- Ctrl+S: Save
- Home: Jump to Start | End: Jump to End
- Left/Right Arrow: Jog playhead 0.01s
- Shift+Left/Right Arrow: Jog playhead 0.1s
- +/-: Zoom In/Out | F: Zoom Fit
- Delete: Delete Selection | Esc: Clear Selection
