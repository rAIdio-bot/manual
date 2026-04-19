## Simple

### What is the Mixer?

The Mixer is where you layer multiple tracks together into a finished piece. Think of it like a recording studio mixing board: each track gets its own volume, pan position, and effects. You control how they blend together, and the result is your final mix.

You have 6 channels. Drag audio files from the Assets panel into any channel, or use Extract Stems to automatically separate a song into vocals, drums, bass, and more. Projects load all channels in parallel for fast startup.

### Channel Controls

Each channel has:

- **Volume slider** — How loud this track is in the mix.
- **Pan** — Move the sound to the left or right speaker.
- **Mute (M)** — Silence this track without removing it.
- **Solo (S)** — Listen to only this track. Multiple solos stack.
- **FX** — Toggle the channel's audio effects on or off.

### The Timeline

The bottom area shows your tracks on a timeline. Each clip appears as a waveform block. You can see where each track starts and ends, and how they overlap.

Click on a waveform to select that channel. Use the zoom buttons to zoom in and out. Right-click a clip for options like copy, paste, loop, and per-clip effects. All edits are non-destructive: your original files are never modified.

### Effects

Click the **FX** button on any channel to toggle its effects. Each channel has 10 effects (the same ones as the Editor). There is also a **Master** section with EQ, Compressor, Saturation, and Stereo Width that processes the final combined output.

You can also add effects to individual clips: right-click a clip and choose **Add Clip FX**. Clips with effects show a green FX badge.

### Loop Clip

Right-click a clip and choose **Loop for…** to fill a duration with tiled copies. Enter a target length in seconds (e.g. 60) and the clip is repeated end-to-end. All copies are independent, so you can edit or add effects to each one separately. Ctrl+Z undoes the entire loop in one step.

### Exporting
When your mix sounds right, click **Export** to save it as a WAV or MP3 file. You can also export each channel as a separate stem file.

The export includes metadata about every track and effect used, plus C2PA content credentials.

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Space | Play/Pause |
| L | Toggle Loop |
| Ctrl+Z / Ctrl+Y | Undo / Redo |
| Ctrl+C / Ctrl+X / Ctrl+V | Copy / Cut / Paste |
| Ctrl+A | Select All |
| Delete | Delete Selection |

## Advanced

### Mixer Architecture

6-channel mixer with per-channel effects, gain, pan, mute, and solo. Each channel can hold multiple clips on a shared timeline. Audio is rendered in real time at your audio device's native sample rate.

Signal flow: clips mixed with channel gain applied, then mono FX chain (gate, HPF, EQ, compressor, saturation, bitcrusher), then stereo panning, then stereo FX chain (widener, delay, reverb), then summed to stereo bus, then master gain, then transparent limiting (signals below 0 dB pass through untouched; peaks above 0 dB are gently compressed to prevent harsh clipping).

### Channel Controls

- Fader: -60 dB to +12 dB gain.
- Pan: -1.0 (full left) to +1.0 (full right). Center is 0.
- Mute (M): Silences the channel without affecting other state.
- Solo (S): Solos stack: enabling Solo on multiple channels plays all soloed channels together.
- FX: Toggles all effects on the channel. Individual effect enabled states are remembered when toggling off and back on.

VU meters show stereo peak levels with 14 segments. Green up to -12 dB, amber from -12 to -3 dB, red above -3 dB.

### Timeline and Clips

Each channel displays clips as waveform blocks positioned by start time. Multiple clips per channel are supported.

- Click a clip to select it.
- Alt+drag to reposition a clip on the timeline.
- Triple-click to select a clip's entire time range.
- Right-click for context menu: trim, cut, copy, paste, normalize, delete, loop, and per-clip FX.
- Delete key removes the selected clip.
- Scroll to zoom the timeline, Shift+scroll to pan.
- Zoom buttons: In, Out, Fit to view.
- Snap toggle: Aligns operations to beat grid (based on project BPM).

Editing operations (Trim, Cut, Fade, Normalize) apply to the selected region within a clip. All edits are non-destructive.

### Master Bus

The master section processes the summed output of all channels.

- Master Fader: -60 dB to +12 dB.
- Master VU: Stereo peak meters.
- Clipping Indicator: Lights red when output peaks above 0 dB.
- Master FX: Four effects on the output bus: Three-Band EQ, Compressor, Soft Saturation, and Stereo Widener.

### Per-Channel Effects

Each channel has the same 10-effect chain as the Editor:

Mono: Volume Envelope, Noise Gate, High Pass Filter, Three-Band EQ, Compressor, Soft Saturation, Bitcrusher.

Stereo: Stereo Widener, Delay, Reverb.

Mono effects process per-sample before stereo panning. Stereo effects process per-frame after panning. This means EQ and compression apply to the source signal, while reverb and delay operate on the panned stereo output.

### Per-Clip Effects

Apply effects to individual clips within a channel. Right-click a clip and choose Add Clip FX to open a 7-effect mono rack:

Volume Envelope, Noise Gate, High Pass Filter, Three-Band EQ, Compressor, Soft Saturation, Bitcrusher.

Stereo effects (Widener, Delay, Reverb) remain at channel level because they apply after panning. Per-clip FX are processed before the channel FX chain, so you can shape individual clips before they are summed and processed together.

Clips with active FX show a green FX badge. Right-click to edit or remove. Per-clip FX are saved in project files and support undo/redo.

### Loop Clip

Right-click a clip and choose Loop for... to tile copies across a target duration. Enter seconds (e.g. 60) and the clip is repeated end-to-end as independent copies.

Each copy has its own sample data, so you can add per-clip FX to individual repetitions (e.g. add reverb only to the last beat of a drum loop). With Snap enabled, copy positions align to the beat grid.

The entire loop operation is a single undo step: Ctrl+Z removes all copies at once. Looped clips are saved and restored in project files.

### Projects

- Save Project: Stores all channels, clips (including multi-clip timelines from loop and paste), positions, gain, pan, channel FX, per-clip FX, and master state as a .raidio file.
- Load Project: Opens a saved project. All clips are restored at their correct positions with per-clip FX settings. Projects use relative paths, so they work if you move the rAIdio.bot output folder.
- New Project: Clears the mixer to a clean state.

The project name appears in the header. An asterisk (*) indicates unsaved changes.

### Export
Export renders the full mix offline (not real-time) for sample-accurate output.

- Export WAV: Lossless stereo PCM16 at the project sample rate.
- Export MP3: V0 VBR (~245 kbps) via ffmpeg's libmp3lame encoder.
- Export Stems: Each channel rendered as a separate stereo WAV file.

All exports use atomic writes (write to .tmp, then rename) to prevent partial files. Metadata sidecars and C2PA credentials are generated for every export.

### Keyboard Shortcuts

- Space: Play/Pause
- L: Toggle Loop
- Ctrl+Z: Undo | Ctrl+Y: Redo
- Ctrl+C: Copy | Ctrl+X: Cut | Ctrl+V: Paste
- Ctrl+A: Select All
- Alt+Drag: Reposition Clip
- Scroll: Zoom | Shift+Scroll: Pan Timeline
- Delete: Delete Selected Clip
