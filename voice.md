## Simple

### What is the Voice Tab?

The Voice tab is your complete voice toolkit. You can make a computer voice say anything you type, clone a real voice from a recording, convert singing voices, transcribe speech to text, and even train a custom voice model from your own recordings. Everything runs on your machine: no audio is ever uploaded anywhere.

### Text to Speech

The simplest mode. Pick a speaker from the list (Aiden, Serena, Dylan, and others), type what you want them to say, and click Generate. The result sounds like natural speech, not a robotic voice. Great for narration, podcasts, or adding spoken intros to your music.

### Custom Voice

Use any voice you have saved or trained. The dropdown shows three types of voices:

- **Built-in speakers** — The same voices available in Text to Speech.
- **Saved voices** — Voices you created with Voice Clone and saved.
- **Trained models** — Shown with `[Trained]` prefix. These are custom voice models you trained from your own recordings. They produce the highest quality and most consistent results.

### Voice Conversion

Take an existing vocal recording, like a singing voice, and transform it into a different voice while keeping the melody, timing, and emotion. Load a vocal track, pick a target voice (either a trained model or a short reference recording), and click Convert.

Use the Pitch Shift slider if you are changing between male and female voices: +12 for male to female, -12 for female to male.

### Transcribe

Load any audio or video file and get a text transcription. The text is saved alongside the file and powers the timed lyrics display in the Play tab. If your file has music in the background, turn on **Isolate Vocals** for much better accuracy.

### Clone Your Voice
Want the AI to speak in your voice? There are two ways to do it:

**The quick way (Voice Clone):** Record a short clip of yourself speaking (even 10–30 seconds works). Switch to Voice Clone mode, load your recording, type what you want to say, and click Generate. You get results in seconds. The voice will sound like you, but it is an approximation.

**The best way (Voice Train):** Gather clean recordings of your voice — at least 5 minutes, ideally 30+ minutes across many clips. Switch to Advanced mode, open Voice Train, check **Train from directory**, and select your folder of recordings. Name your model, set epochs to 150–300, and click Generate Speech. Training takes 1–3 hours depending on data size. When it finishes, your model appears as `[Trained]` in Custom Voice and Voice Convert.

The more clean speech data you provide, the better the clone. Podcast recordings, voiceovers, and audiobook readings work great. Avoid noisy recordings.

Start with Voice Clone to hear your voice right away. If you like the result and want it to be better, invest the time in training.

### Voice Consent & Provenance

When using someone else's voice (Clone, Conversion, or Training), rAIdio.bot invites you to document:

1. **Voice owner's name** (or "myself" if it's your own voice)
2. **Intended use** (e.g. "podcast intro", "personal project")
3. **Consent note** indicating you have permission

This consent record is embedded in the **C2PA provenance signature** of every generated audio file. It creates a verifiable audit trail linking each voice clone to a consent attestation with a timestamp. If someone misuses the tool, this record establishes that they attested to having permission.

The consent data is stored locally in the audio file's metadata — it is never transmitted to any server. A future version of rAIdio.bot will offer an opt-in setting to refuse playback of unsigned or tampered voice models.

**Ctrl+Enter**: Start generating from anywhere on this tab.

## Advanced

### Text to Speech

Generate natural speech from text using Qwen3-TTS.

Speaker: 9 built-in voices (Aiden, Dylan, Eric, Ono_Anna, Ryan, Serena, Sohee, Uncle_Fu, Vivian). Each has distinct vocal characteristics.

Style Instruction: Free text that guides tone, pace, and emotion. Examples: "speak slowly and warmly", "excited and energetic", "whispered, intimate". This field is optional but significantly affects output quality.

Model Size: 0.6B (faster, lower VRAM) or 1.7B (higher quality, more VRAM). 1.7B recommended for final output; 0.6B for quick previews.

Language: 21 languages supported. Set explicitly for best results; auto-detection can misidentify, especially for short text.

Expressiveness (Top-K): 1 to 200. Higher values produce more varied, expressive speech. Lower values are more consistent and predictable. Set to 0 to disable sampling entirely (greedy decoding).

Approximate Duration (Max Tokens): 256 to 4096 tokens. Controls the maximum output length. At default 2048, output is roughly 24 seconds. Actual duration depends on text length and speaking pace.

### Voice Design

Create a completely new voice from a text description. Describe pitch (high, low, baritone), tone (warm, bright, nasal), age (young, elderly), accent (British, Southern US), and pace (fast, measured). The AI synthesizes a unique voice matching your description.

Combine with Style Instruction for fine control: Voice Design sets the voice identity, Style Instruction sets the delivery.

### Voice Clone

Clone a voice from a reference audio clip.

Reference Audio: A recording of the voice to clone. Longer, clearer clips produce better results.

Reference Text: What the speaker says in the clip. Providing accurate text improves alignment significantly. Leave blank to use x-vector extraction (faster but less accurate).

Target Text: What you want the cloned voice to say.

The clone is a one-shot approximation. For higher quality and consistency, train a dedicated model using Voice Train.

### Custom Voice

Unified voice selector combining all available voices:

Built-in speakers: Standard Qwen3-TTS voices. Route to standard TTS.

Saved voices: CosyVoice embeddings from Voice Clone, stored in models/voices/. Route to custom voice TTS.

Trained models: RVC .pth files from Voice Train, shown with [Trained] prefix. Route to a chained TTS+RVC workflow: Qwen3-TTS generates speech with a base speaker, then RVC rewrites the voice characteristics using the trained model. This produces the highest quality output.

### Voice Conversion: Trained Model (RVC)

Convert a vocal recording using a trained RVC model.

Source Audio: An isolated vocal stem works best. Full mixes with background music cause artifacts.

Target Voice: A [Trained] .pth model from Voice Train. The app automatically finds and uses the matching .index file (generated during training) for higher quality speaker-specific matching.

Index Rate: 0 to 1.0. Controls timbre matching via the index file. Higher values match the trained voice more closely.

Pitch Shift: -12 to +12 semitones. +12 for male-to-female, -12 for female-to-male. Smaller adjustments (3-5 semitones) fine-tune without introducing artifacts.

You can delete models with the Delete Model button below the voice dropdown.

Internal defaults: RMVPE pitch detection, RMS mix rate 0.5, consonant protection 0.5, filter radius 3.

### Voice Conversion: Reference Audio (SeedVC)

Zero-shot voice conversion using a reference recording instead of a trained model.

Source Audio: An isolated vocal stem.

Reference Voice: A short recording (30 seconds ideal) of the target voice. The AI matches this timbre while preserving melody and timing.

Diffusion Steps: 10 to 100. Quality vs speed tradeoff. Default 25 is a good balance. Higher values (50+) improve subtle detail but take longer.

Pitch Shift: Same as RVC mode.

First use downloads SeedVC models from HuggingFace (~1-3 GB).

### Voice Train
Train a reusable RVC voice model from recordings. A trained model produces faster, more consistent, and higher quality results than Voice Clone because the model has learned the voice deeply from many samples.

Training Audio: 5+ minutes of clean voice audio (10+ minutes recommended, 30+ ideal). Use 'Train from directory' to load a folder of clips — the more clean speech data, the better the result. Silent files and background noise degrade quality.

Model Name: Alphanumeric characters, dots, dashes, and underscores only.

Epochs: 50 to 500. At 50 epochs you get a usable but rough voice. 100-200 produces good quality. 300-500 for high fidelity. Over-training can cause artifacts — if quality degrades, use a lower epoch checkpoint.

Batch Size: 2 to 16 (default 8). Higher values train faster and more stably but use more VRAM. If training crashes with out-of-memory errors, reduce batch size.

Sample Rate: 48000 (default, recommended) or 40000. Higher captures more voice detail.

Training time depends on data size and epochs. With ~500 clips at 150 epochs: roughly 2-3 hours on a modern GPU. 50 epochs takes about 1 hour. The progress overlay stays visible until training completes.

After training, the model (.pth) and its index file (.index) appear in Custom Voice and Voice Conversion immediately. The index file significantly improves voice quality by matching speaker-specific features. You can delete bad models with the Delete button next to the voice dropdown.

Tip: Clean, isolated speech recordings produce the best models. Podcast audio, voiceovers, and audiobook readings work well. Phone calls, noisy environments, and music in the background produce poor models.

### Using Your Own Voice: Two Paths
Voice Clone (zero-shot): Provide a single recording and get results immediately. The AI approximates your voice from one sample. Quality is reasonable for short text but degrades on longer output: the voice may drift, lose characteristic detail, or sound generic. This is a one-shot inference with no learning; the model sees your voice once and does its best.

Voice Train (trained model): Provide 5+ minutes of recordings and wait 12-24 hours. The AI builds a dedicated model of your voice by learning from hundreds of samples across your recordings. The result is dramatically better: consistent timbre across any text, natural inflection, and reliable output even on long passages. The trained .pth model can be used in both Custom Voice (TTS) and Voice Conversion (singing).

Recommendation: Use Voice Clone to test whether the voice pipeline works for your use case. If it does, train a model for production quality. The trained model will always outperform the zero-shot clone.

### Transcribe

Speech-to-text transcription powered by Whisper.

Model Size: tiny (fastest, least accurate) through large-v3-turbo (best balance of speed and accuracy). large-v3 is the most accurate overall. small (default) is fast but may mishear lyrics.

Task: Transcribe preserves the original language. Translate always outputs English regardless of the source language.

Language: Set explicitly when you know it. Auto-detection can misidentify, especially for short clips or accented speech.

Isolate Vocals: The single biggest accuracy improvement for music files. Runs Demucs stem separation first so Whisper only hears the voice. Also saves the voiceless version.

Output: A timestamped transcription saved as .transcript.json alongside the audio. This powers timed lyrics in the Play tab (Lines and Words display modes).

### Backend: Qwen3-TTS, RVC, SeedVC, Whisper, Demucs
Voice features use multiple AI models, each selected for its specific strength:

Qwen3-TTS: Text-to-speech with multi-speaker, multi-language support. Handles voice cloning, design, and custom voice generation.

RVC (Retrieval-based Voice Conversion): Singing voice conversion using trained models. Fast inference, high quality when well-trained.

SeedVC: Zero-shot voice conversion from a reference recording. No training required.

Whisper: OpenAI's speech recognition model. Multi-language transcription and translation.

Demucs: Meta's source separation model. Splits audio into vocals, drums, bass, and other instruments.

### Keyboard Shortcut

Ctrl+Enter: Start generating from anywhere on this tab.
