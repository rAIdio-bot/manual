## Simple

### What is the Music Tab?

This is where you make music. Describe what you want to hear in plain English, and rAIdio.bot generates a full song for you. You do not need to play an instrument, read sheet music, or know any music theory. Just describe the vibe and click Generate.

### Tags and Caption

Tags are comma-separated words that tell the AI what kind of music to make: genre, instruments, mood, style. Put the genre first. Example: `pop, electric guitar, upbeat, female vocals`.

Caption is an optional paragraph describing the full sonic picture: production style, energy, instruments, and how the song should feel. The more detail you give, the closer the result will be to what you imagine.

### Adding Lyrics

Type your lyrics in the Lyrics box. You can organize them with tags like `[verse]`, `[chorus]`, and `[bridge]` to give the song structure. If you leave the lyrics box empty, you will get an instrumental track with no vocals.

### Wizard and Surprise Me

Not sure where to start? You have two options at the top of the Music tab:

**Wizard** walks you through five quick questions: what the music is for, what genre and mood you want, how long it should be, and whether you have lyrics. It fills in everything for you. First-time users see the Wizard automatically.

**Surprise Me** picks a random genre and style from a curated list of presets that produce good results. One click and you are ready to generate. Great for exploring what the AI can do.

Both fill in the Tags, Caption, Lyrics, Duration, and BPM fields. You can edit any of them before generating, or just hit Generate and see what happens.

### Generating

Click Generate to start. The first time is slow because the AI model needs to load into your GPU memory. After that, generation is much faster. Your song is saved as a lossless WAV file and appears in the Assets panel on the left when it is done. Double-click it to play, or use the buttons to open it in the Editor, send it to the Mixer, or extract its stems.

### Style Transfer

Switch to Style Transfer mode when you have an existing song and want to create something new inspired by it. Load a reference track, describe the style you want, and adjust the Strength slider. Low strength keeps more of the original feel; high strength gives the AI more creative freedom.

### Tips

After generating, you have quick actions below the waveform:

- **Make Another** — Same settings, new random seed. Every generation sounds different, so keep clicking until you hear something you love.
- **Save MP3** — One-click export to MP3 format, saved right next to the original.
- **Seed** — The number shown after generation controls the randomness. Copy it and share it — someone else with the same settings and seed gets the same song.
- **Open Folder** — Opens the file location in Windows Explorer.

Every song you generate gets a metadata file that records exactly how it was made, so you always have proof of authorship.

**Ctrl+Enter**: Start generating from anywhere on this tab.

### Stem Separation
Split any song into its individual parts: Vocals, Drums, Bass, Other (guitars, synths, keyboards, etc.), and an Instrumental mix (everything except vocals). Right-click any audio file in the Assets panel and choose **Extract Stems**, or use the Extract Stems button in the Music or Edit tabs after generating. Separated stems are saved in your Stems folder and loaded into the Mixer automatically.

If you generated an instrumental track (with `[instrumental]` in the lyrics), the Vocals stem is skipped because it would only contain silence and separation noise. You get four clean stems instead of five. If you later add your own vocals to the mix and export it, future stem extractions of that export will include all five stems.

The right-click menu also offers **Detect Chords** and **Export MIDI** for any audio file.

## Advanced

### Text to Music

The primary generation mode. Your tags, caption, and lyrics are sent to ACE-Step 1.5, which generates a full audio track on your GPU.

Tags: Comma-separated control signals. Lead with genre, then add instruments, mood, and style. Aim for 3 to 7 tags. Do not put BPM, key, or duration in tags; use the dedicated controls instead.

Caption: One dense prose paragraph describing the full sonic picture, production style, energy, and instrument evolution. Tags and caption must not contradict each other. Tags and caption are combined and sent to the model's text encoder together.

Lyrics: Free text with optional structural tags: [verse], [chorus], [bridge], [intro], [outro]. Leave blank for instrumental generation. The model handles English best; other languages work but with less reliable pronunciation.

Duration: 1 to 300 seconds. Stable ranges are 30 to 60 seconds and 2 to 4 minutes. Longer durations use more VRAM and take longer to generate. If you hit out-of-memory errors, reduce this first.

BPM: 60 to 200 beats per minute by default. Reference values: ballad ~70, pop ~120, dance/EDM ~140, drum and bass ~170. Click the lock icon next to BPM to unlock the full range up to 300. Higher values can work for certain genres but may reduce generation quality, so the safe range is locked by default.

Steps: 20 to 200 sampling steps. This is the quality vs speed tradeoff. 30 steps gives a quick preview. 65 is the sweet spot — clear output without overdoing it. Going much higher than 65 can actually introduce issues rather than improve quality. This applies to both the Standard and XL models.

Key: Musical key (C through B, major or minor). The default is C major. Choose the key that matches the mood you want — minor keys sound darker, major keys brighter.

Sampler: The diffusion sampling algorithm. er_sde is the default — it produces the cleanest, most musical output with the least distortion. The other samplers (euler, dpmpp_2m, dpmpp_sde, dpmpp_3m_sde, uni_pc) are experimental alternatives that may produce interesting textures but are more likely to introduce noise or artifacts. Start with er_sde and explore others if you want to experiment.

Scheduler: Controls the noise schedule during sampling. linear_quadratic is the default — it removes noise gradually then accelerates, which prevents crackling and rhythm instability. The other schedulers (simple, karras, exponential, beta) are experimental. They can produce different sonic characteristics but are less predictable. Pair linear_quadratic with er_sde for the most reliable results.

CFG Scale: Classifier-free guidance strength. Controls how closely the output follows your description. 4.0 is the default and produces clear, well-structured output. Lower values (1.0-2.0) give the model more creative freedom but may sound less focused. Going above 6.0 tends to produce distorted, compressed audio — keep it under 5.0 for best results.

Batch: Generate 1 to 8 variations with consecutive seeds. The model has inherent variance, so the same prompt can produce very different results. Batch generation lets you quickly explore variations and cherry-pick the best one. The others are deleted when you choose.

Seed: Controls the random number generator. Same seed with the same settings always produces the same output. Change it to explore variations. -1 or 0 picks a random seed.

### Wizard (Prompt Builder)

The Wizard button at the top of the Text to Music controls opens a guided prompt builder. It asks five questions and assembles your answers into properly formatted Tags, Caption, Lyrics, Duration, and BPM values.

Step 1 — Purpose: What the music is for (streaming, an original song, background audio, or exploration). This shapes the caption's tone.

Step 2 — Genre: Pick from preset genre clusters (Electronic, Hip-Hop/R&B, Rock/Metal, Organic, World) or type your own. Multiple selections are combined.

Step 3 — Feel: Choose a mood (Dark through Euphoric), tempo (Slow, Mid, Fast), and song structure sections (Intro, Verse, Chorus, Bridge, Outro).

Step 4 — Duration: Preset lengths from 30 seconds to 4 minutes, or type a custom value in seconds.

Step 5 — Lyrics: Choose instrumental (no vocals), describe a concept (the Wizard generates structure tags), or paste your own lyrics.

The Wizard handles contradictions gracefully. If you pick Background/Ambient as the purpose but choose a high-energy genre like Techno, the caption notes the energy is subdued for background use.

After building, all fields are editable. The Wizard gives you a starting point; you decide what stays.

### Lyric Writing Tips

Getting good vocal output requires well-structured lyrics.

Line length: Aim for 6 to 10 syllables per line. This matches the natural phrasing the model was trained on.

Structure tags: [verse], [chorus], [bridge], [intro], [outro] help the model organize the song into distinct sections with appropriate energy and dynamics.

Backing vocals: Wrap text in parentheses to create backing vocals or harmonies: (ooh, aah).

Extended vowels: Spell out held notes phonetically: 'heeere', 'noooow'. The model will sustain the note longer.

Emphasis: ALL CAPS adds vocal emphasis to specific words.

Word count: The model generates roughly 2 to 3 words per second. For a 47-second track, aim for 90 to 140 words of lyrics.

### Style Transfer

Generate new music that draws from a reference track.

Reference Audio: The source track. Can be any format (WAV, MP3, FLAC, etc.). It is converted to WAV internally.

Style Tags: Describe the style you want applied. Works like the normal description field.

Lyrics: Words for the new song. Leave blank to preserve the reference track's vocal content if any.

Strength: 0.05 to 1.0. Controls how much of the reference carries over. At low values (0.1-0.3), the output closely follows the reference. At high values (0.7+), the AI takes more creative liberty. 0.5 is a balanced starting point.

Duration, BPM, Steps, Key, Sampler, Scheduler, CFG, Batch, Seed: Same as Text to Music.

### Output Actions

After generation, you have several options:

Play: Preview the output in the mini player.

Open in Editor: Load into the Edit tab for trimming, effects, and fine-tuning.

Send to Mixer: Add to the next empty channel in the Mix tab.

Extract Stems: Decompose into vocals, drums, bass, other instruments, and an instrumental mix using Demucs AI. For instrumental tracks, the vocals stem is skipped automatically. Stems are saved to the Stems folder and loaded into the Mixer.

Every output automatically receives a metadata sidecar and C2PA content credential documenting the generation parameters, model version, and your creator identity.

### Stem Separation (Demucs)

Splits audio into 5 stems: vocals, drums, bass, other, and an instrumental mix (everything minus vocals). Available from:
- Right-click any audio file in the Assets panel
- Extract Stems button in the Music tab after generating
- Extract and Mix in the Edit tab

For instrumental tracks (generated with [instrumental] in the lyrics), the Vocals stem is automatically skipped. Demucs always produces a vocals stem, but for instrumental content it contains only separation artifacts — low-level noise with no musical value. Skipping it keeps your mixer clean and avoids subtle phase issues when the stems are summed back together. You get four stems instead of five.

If you later add your own vocals to the project and export the mix, that export has its own metadata. Extracting stems from it will produce all five stems, including the real vocals.

Extracted stems may sound different from the original mix. This is normal: individual stems can sound thinner because the original had master bus processing. Use the Editor's EQ and effects to shape each stem.

The right-click menu also offers Detect Chords and Export MIDI for any audio file.

### Backend: ACE-Step 1.5
Music generation is powered by ACE-Step 1.5, an open-source model (Apache 2.0 license) trained exclusively on licensed and public domain audio. The model runs locally on your GPU via ComfyUI. Two variants are available: HQ (streaming, requires more VRAM) and AIO (all-in-one, lower VRAM). rAIdio.bot selects the appropriate variant based on your GPU's available memory.

Generated audio is saved as lossless 16-bit WAV at 44.1 kHz — no lossy compression is applied. Audio is resampled to your device's native sample rate using a high-quality sinc interpolation filter for transparent playback.

### Keyboard Shortcut

Ctrl+Enter: Start generating from anywhere on this tab.
