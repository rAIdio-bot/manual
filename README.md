# rAIdio.bot Manual

**Version 20260420_57f1f8f-dirty**

Quick reference for all features. For the full in-app help, press **F1** from any tab inside rAIdio.bot.

> [EULA](EULA.md) &middot; [Privacy Policy](PRIVACY.md) &middot; [Content Policy](CONTENT_POLICY.md) &middot; [Third-Party Notices](THIRD_PARTY_NOTICES.md) &middot; [EU AI Act](EU_AI_ACT.md)

---

## Contents

- [Music](music.md)
- [Voice](voice.md)
- [Edit](edit.md)
- [Mix](mix.md)
- [Play](play.md)
- [Settings](settings.md)
- [Audio Quality](audio-quality.md)

---

## Music

#### What is the Music Tab?

This is where you make music. Describe what you want to hear in plain English, and rAIdio.bot generates a full song for you. You do not need to play an instrument, read sheet music, or know any music theory. Just describe the vibe and click Generate.

#### Tags and Caption

Tags are comma-separated words that tell the AI what kind of music to make: genre, instruments, mood, style. Put the genre first. Example: `pop, electric guitar, upbeat, female vocals`.

Caption is an optional paragraph describing the full sonic picture: production style, energy, instruments, and how the song should feel. The more detail you give, the closer the result will be to what you imagine.

#### Adding Lyrics

Type your lyrics in the Lyrics box. You can organize them with tags like `[verse]`, `[chorus]`, and `[bridge]` to give the song structure. If you leave the lyrics box empty, you will get an instrumental track with no vocals.

#### Wizard and Surprise Me

Not sure where to start? You have two options at the top of the Music tab:

**Wizard** walks you through five quick questions: what the music is for, what genre and mood you want, how long it should be, and whether you have lyrics. It fills in everything for you. First-time users see the Wizard automatically.

**Surprise Me** picks a random genre and style from a curated list of presets that produce good results. One click and you are ready to generate. Great for exploring what the AI can do.

Both fill in the Tags, Caption, Lyrics, Duration, and BPM fields. You can edit any of them before generating, or just hit Generate and see what happens.

#### Generating

Click Generate to start. The first time is slow because the AI model needs to load into your GPU memory. After that, generation is much faster. Your song is saved as a lossless WAV file and appears in the Assets panel on the left when it is done. Double-click it to play, or use the buttons to open it in the Editor, send it to the Mixer, or extract its stems.

#### Style Transfer

Switch to Style Transfer mode when you have an existing song and want to create something new inspired by it. Load a reference track, describe the style you want, and adjust the Strength slider. Low strength keeps more of the original feel; high strength gives the AI more creative freedom.

#### Tips

After generating, you have quick actions below the waveform:

- **Make Another** — Same settings, new random seed. Every generation sounds different, so keep clicking until you hear something you love.
- **Save MP3** — One-click export to MP3 format, saved right next to the original.
- **Seed** — The number shown after generation controls the randomness. Copy it and share it — someone else with the same settings and seed gets the same song.
- **Open Folder** — Opens the file location in Windows Explorer.

Every song you generate gets a metadata file that records exactly how it was made, so you always have proof of authorship.

**Ctrl+Enter**: Start generating from anywhere on this tab.

#### Stem Separation
Split any song into its individual parts: Vocals, Drums, Bass, Other (guitars, synths, keyboards, etc.), and an Instrumental mix (everything except vocals). Right-click any audio file in the Assets panel and choose **Extract Stems**, or use the Extract Stems button in the Music or Edit tabs after generating. Separated stems are saved in your Stems folder and loaded into the Mixer automatically.

If you generated an instrumental track (with `[instrumental]` in the lyrics), the Vocals stem is skipped because it would only contain silence and separation noise. You get four clean stems instead of five. If you later add your own vocals to the mix and export it, future stem extractions of that export will include all five stems.

The right-click menu also offers **Detect Chords** and **Export MIDI** for any audio file.

*For advanced controls, open the `Music` section in the app (F1 → Settings → Manual → Advanced), or read [music.md](music.md).*

---

## Voice

#### What is the Voice Tab?

The Voice tab is your complete voice toolkit. You can make a computer voice say anything you type, clone a real voice from a recording, convert singing voices, transcribe speech to text, and even train a custom voice model from your own recordings. Everything runs on your machine: no audio is ever uploaded anywhere.

#### Text to Speech

The simplest mode. Pick a speaker from the list (Aiden, Serena, Dylan, and others), type what you want them to say, and click Generate. The result sounds like natural speech, not a robotic voice. Great for narration, podcasts, or adding spoken intros to your music.

#### Custom Voice

Use any voice you have saved or trained. The dropdown shows three types of voices:

- **Built-in speakers** — The same voices available in Text to Speech.
- **Saved voices** — Voices you created with Voice Clone and saved.
- **Trained models** — Shown with `[Trained]` prefix. These are custom voice models you trained from your own recordings. They produce the highest quality and most consistent results.

#### Voice Conversion

Take an existing vocal recording, like a singing voice, and transform it into a different voice while keeping the melody, timing, and emotion. Load a vocal track, pick a target voice (either a trained model or a short reference recording), and click Convert.

Use the Pitch Shift slider if you are changing between male and female voices: +12 for male to female, -12 for female to male.

#### Transcribe

Load any audio or video file and get a text transcription. The text is saved alongside the file and powers the timed lyrics display in the Play tab. If your file has music in the background, turn on **Isolate Vocals** for much better accuracy.

#### Clone Your Voice
Want the AI to speak in your voice? There are two ways to do it:

**The quick way (Voice Clone):** Record a short clip of yourself speaking (even 10–30 seconds works). Switch to Voice Clone mode, load your recording, type what you want to say, and click Generate. You get results in seconds. The voice will sound like you, but it is an approximation.

**The best way (Voice Train):** Gather clean recordings of your voice — at least 5 minutes, ideally 30+ minutes across many clips. Switch to Advanced mode, open Voice Train, check **Train from directory**, and select your folder of recordings. Name your model, set epochs to 150–300, and click Generate Speech. Training takes 1–3 hours depending on data size. When it finishes, your model appears as `[Trained]` in Custom Voice and Voice Convert.

The more clean speech data you provide, the better the clone. Podcast recordings, voiceovers, and audiobook readings work great. Avoid noisy recordings.

Start with Voice Clone to hear your voice right away. If you like the result and want it to be better, invest the time in training.

#### Voice Consent & Provenance

When using someone else's voice (Clone, Conversion, or Training), rAIdio.bot requires you to:

1. **Enter the voice owner's name** (or "myself" if it's your own voice)
2. **State the intended use** (e.g. "podcast intro", "personal project")
3. **Check the attestation box** confirming you have permission

This consent record is embedded in the **C2PA provenance signature** of every generated audio file. It creates a verifiable audit trail linking each voice clone to a consent attestation with a timestamp. If someone misuses the tool, this record establishes that they attested to having permission.

The consent data is stored locally in the audio file's metadata — it is never transmitted to any server.

**Ctrl+Enter**: Start generating from anywhere on this tab.

*For advanced controls, open the `Voice` section in the app (F1 → Settings → Manual → Advanced), or read [voice.md](voice.md).*

---

## Edit

#### What is the Editor?

The Editor is where you fine-tune any audio clip. Trim the start and end, cut out sections you do not want, add fades, boost the volume, and apply real-time effects like reverb or EQ. Think of it as the place where you polish your audio before it goes into a mix or out into the world.

#### Loading Audio

There are several ways to load audio into the Editor:

- Double-click any file in the Assets panel.
- Use **Open in Editor** from the Music tab after generating a song.
- Drag and drop a file onto the Editor waveform.

The Editor supports WAV, MP3, OGG, FLAC, AIFF, M4A, and WMA files.

#### Selecting and Editing

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

#### Effects

The FX sidebar has 10 audio effects. Click the dot next to an effect to turn it on or off. Click the effect name to expand its controls and adjust the settings.

The effects are: Envelope, Gate, High Pass, EQ, Compressor, Saturation, Bitcrusher, Stereo Width, Delay, and Reverb. You do not need to know what all of these do right away. Experiment and listen to what changes.

#### Speed and Pitch

Above the transport controls, you will find Speed and Pitch sliders.

- **Speed** changes how fast the audio plays without changing the pitch.
- **Pitch** shifts the audio up or down without changing the speed.

Adjust them and listen in real time, then click **Apply** to make the change permanent. Click **Reset** to go back to normal.

#### Saving Your Work

- **Save** — Saves an edited copy to your Music folder. Your original file is never overwritten.
- **Save As** — Pick a name and location.
- **Send to Mixer** — Load the clip into the next empty mixer channel.
- **Send to Playlist** — Add it to the Play tab's playlist.

#### Chord Detection

Chords are detected automatically when you extract stems, or you can right-click any audio file in the Assets panel and choose **Detect Chords**. A colored bar above the waveform shows the detected chord progression. Toggle it on or off with the Chords button in the toolbar. Chord detection takes under 10 seconds on CPU for a 3-minute stem.

#### MIDI Export (Early Access)

Click **Export MIDI** to convert the current clip to a MIDI file using Spotify basic-pitch, a neural music transcription model. You can also right-click any audio file in Assets and choose **Export MIDI**. Accuracy is highest on isolated melody and bass stems. MIDI files appear in the Assets panel under the MIDI category.

*This feature is incomplete for Early Access. Output is approximate and may require cleanup in a DAW.*

#### Keyboard Shortcuts

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

*For advanced controls, open the `Edit` section in the app (F1 → Settings → Manual → Advanced), or read [edit.md](edit.md).*

---

## Mix

#### What is the Mixer?

The Mixer is where you layer multiple tracks together into a finished piece. Think of it like a recording studio mixing board: each track gets its own volume, pan position, and effects. You control how they blend together, and the result is your final mix.

You have 6 channels. Drag audio files from the Assets panel into any channel, or use Extract Stems to automatically separate a song into vocals, drums, bass, and more. Projects load all channels in parallel for fast startup.

#### Channel Controls

Each channel has:

- **Volume slider** — How loud this track is in the mix.
- **Pan** — Move the sound to the left or right speaker.
- **Mute (M)** — Silence this track without removing it.
- **Solo (S)** — Listen to only this track. Multiple solos stack.
- **FX** — Toggle the channel's audio effects on or off.

#### The Timeline

The bottom area shows your tracks on a timeline. Each clip appears as a waveform block. You can see where each track starts and ends, and how they overlap.

Click on a waveform to select that channel. Use the zoom buttons to zoom in and out. Right-click a clip for options like copy, paste, loop, and per-clip effects. All edits are non-destructive: your original files are never modified.

#### Effects

Click the **FX** button on any channel to toggle its effects. Each channel has 10 effects (the same ones as the Editor). There is also a **Master** section with EQ, Compressor, Saturation, and Stereo Width that processes the final combined output.

You can also add effects to individual clips: right-click a clip and choose **Add Clip FX**. Clips with effects show a green FX badge.

#### Loop Clip

Right-click a clip and choose **Loop for…** to fill a duration with tiled copies. Enter a target length in seconds (e.g. 60) and the clip is repeated end-to-end. All copies are independent, so you can edit or add effects to each one separately. Ctrl+Z undoes the entire loop in one step.

#### Exporting
When your mix sounds right, click **Export** to save it as a WAV or MP3 file. You can also export each channel as a separate stem file.

The export includes metadata about every track and effect used, plus C2PA content credentials.

#### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Space | Play/Pause |
| L | Toggle Loop |
| Ctrl+Z / Ctrl+Y | Undo / Redo |
| Ctrl+C / Ctrl+X / Ctrl+V | Copy / Cut / Paste |
| Ctrl+A | Select All |
| Delete | Delete Selection |

*For advanced controls, open the `Mix` section in the app (F1 → Settings → Manual → Advanced), or read [mix.md](mix.md).*

---

## Play

#### What is the Player?

The Player is where you listen to your music and explore your creations. Double-click any file in the Assets panel to start playing it. Songs are added to a playlist on the right side so you can queue up a listening session.

#### Display Modes

Three ways to view what is playing:

- **Waveform** — Animated FFT terrain visualizer inspired by Joy Division's Unknown Pleasures. Real-time frequency spectrum analysis driven by the actual audio playing.
- **Lines** — Timed lyrics as subtitles at the bottom of the screen. Only the current line is visible, like movie subtitles. Works great over video.
- **Sing Along** — Karaoke mode with word-by-word highlighting. The current line shows with each word changing color as it is sung. The next line previews below. Text has a black stroke outline and purple glow for readability over video.

Lyrics come from transcription files. Use **Sing Along** from the right-click menu to auto-generate them, or use the Voice tab's Transcribe mode.

#### Playlist

The sidebar on the right is your playlist. Click any item to jump to it. Use the X button to remove a track. Drag files from the Assets panel or use **Add File** to build your playlist.

**Shuffle** plays tracks in random order. **Repeat** starts over when the playlist ends. **Loop** repeats the current track.

#### Sing Along
Right-click any audio or video file and choose **Sing Along**. rAIdio.bot automatically separates the vocals from the instruments, transcribes the lyrics with word-level timing, and opens the Play tab in karaoke mode.

The instrumental plays while timed lyrics highlight word by word on screen. For video files, the original video plays in the background with lyrics overlaid. Toggle **Vocals On/Off** to switch between hearing the instrumental and the original.

Once you have run Sing Along on a track, the stems and lyrics are saved permanently. Next time you play that track, karaoke mode activates automatically without re-processing.

#### Generate Soundtrack

Right-click any video file and choose **Generate Soundtrack**. rAIdio.bot analyzes the video's energy and mood, then opens a dialogue with an AI music director who suggests tags, BPM, and style. Describe the vibe you want, and the director adjusts the parameters. When you are happy, confirm and the Music tab opens pre-filled, ready to generate a matching soundtrack.

Requires Ollama running locally with qwen2.5:3b. If Ollama is not available, the dialogue is skipped and you get direct analysis results.

*For advanced controls, open the `Play` section in the app (F1 → Settings → Manual → Advanced), or read [play.md](play.md).*

---

## Settings

#### Provenance and C2PA

Every file you create in rAIdio.bot can carry a signed record that proves you made it, when you made it, and what tools were used. This is your proof of authorship.

The Provenance page in Settings lets you turn this on or off. We recommend keeping it on. The signed records are small files saved alongside your audio. Keep them: they are the closest thing available right now to proof that your music is yours.

#### Creator Identity

Your name, email, website, and organization are embedded in every file you create. This is how the signed record knows who made the music. You can fill in as much or as little as you want.

Your display name defaults to your computer username. Change it to whatever you want to be credited as.

#### Licenses

The Licenses page lists every piece of open-source software that rAIdio.bot uses, along with each one's license type. This is here for transparency: you can see exactly what powers the app.

#### Global Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Ctrl+1 | Music tab |
| Ctrl+2 | Voice tab |
| Ctrl+3 | Edit tab |
| Ctrl+4 | Mix tab |
| Ctrl+5 | Play tab |
| F1 | Help (current tab) |
| F2 | Rename selected asset |
| Enter | Open selected asset |

*For advanced controls, open the `Settings` section in the app (F1 → Settings → Manual → Advanced), or read [settings.md](settings.md).*

---

## Audio Quality

#### Lossless by default

Music is generated and saved as 16-bit WAV at 44.1 kHz. No lossy compression is applied to generated audio — what you hear is exactly what the model produced.

#### Clean playback

When your audio device runs at a different sample rate (e.g. 48 kHz), audio is resampled using a 256-tap sinc interpolation filter. The conversion is transparent with no audible artifacts.

#### No brick-wall clipping

The master output uses a threshold-based limiter that passes signals below 0 dB through untouched. Only peaks above the threshold are gently compressed to prevent harsh clipping.

#### Export options

Export your mixes as lossless WAV or MP3 (V0 VBR ~245 kbps via ffmpeg).

*For advanced controls, open the `Audio Quality` section in the app (F1 → Settings → Manual → Advanced), or read [audio-quality.md](audio-quality.md).*

---

*Generated by tools/publish_manual.ps1 from rAIdio.bot-rust@57f1f8f.*
