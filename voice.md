## Simple

### What is the Voice Tab?

The Voice tab is your complete voice toolkit. You can make a computer voice say anything you type, clone a real voice from a recording, convert singing voices, transcribe speech to text, and even train a custom voice model from your own recordings. Everything runs on your machine: no audio is ever uploaded anywhere.

### Text to Speech

The simplest mode. Pick a speaker from the list (Aiden, Serena, Dylan, and others), type what you want them to say, and click Generate. The result sounds like natural speech, not a robotic voice. Great for narration, podcasts, or adding spoken intros to your music.

### Custom Voice

Use any voice you have saved. The dropdown shows three types of voices:

- **Built-in speakers** — The same voices available in Text to Speech.
- **Saved voices** — Shown with `[Saved]` prefix. Voices you created with Voice Clone and saved with the "Save as reusable voice" option. Same engine and quality as Voice Clone but persistent across sessions.
- **Trained models** *(legacy)* — Shown with `[Trained]` prefix if you have any imported or pre-existing RVC `.pth` files in your library. RVC is a voice converter, not a voice cloner — chained through TTS it inherits the base speaker's pitch. The `[Trained]` route is retained for back-compat. **Use Saved Voices for TTS use cases**; use Voice Conversion mode to transform existing vocal recordings (singer-swap).

### Voice Conversion

Take an existing vocal recording, like a singing voice, and transform it into a different voice while keeping the melody, timing, and emotion. Load a vocal track, pick a target voice (either a trained model or a short reference recording), and click Convert.

Use the Pitch Shift slider if you are changing between male and female voices: +12 for male to female, -12 for female to male.

### Transcribe

Load any audio or video file and get a text transcription. The text is saved alongside the file and powers the timed lyrics display in the Play tab. If your file has music in the background, turn on **Isolate Vocals** for much better accuracy.

### Clone Your Voice
Want the AI to speak in your voice? Two paths, same engine:

**Once (Voice Clone):** Record a short clip of yourself speaking (even 10–30 seconds works). Switch to Voice Clone mode, load your recording, type what you want to say, and click Generate. You get results in seconds. Good for one-off generations.

**Reusable (Voice Clone + Save):** In Voice Clone mode, check **Save as reusable voice (signed)** and give the voice a name before clicking Generate. The cloned voice is persisted as a signed `.pt` file. From then on, pick `[Saved] <name>` from Custom Voice mode's dropdown to speak any text in that voice — no need to re-load the reference clip every time. Same engine, same quality, just persistent across sessions.

**What "clean" means:** one speaker, no music, no heavy reverb, recorded with the same microphone in a quiet room. The clone captures whatever is in your audio — room tone, mic colour, background noise — so consistency matters more than total minutes.

**How much is enough?** A clean 10–30 second reference clip is plenty for Voice Clone. Longer is fine but doesn't help much past about a minute — the cloning engine extracts a speaker prompt, not a fine-tune.

Start with Voice Clone to hear it. When you have one you like, repeat with **Save as reusable voice** checked to pin it for future generations.

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

Save as reusable voice (signed): Optional. When checked, supply a Voice Name and the cloned voice prompt is persisted as a `.pt` file in `Library/qwen3-tts_voices/`. The voice is signed with your consent attestation using the same provenance contract used for trained RVC models — embedded in the `.pt`'s archive plus a `.consent.json` sidecar. Saved voices appear in the Custom Voice dropdown as `[Saved] <name>` and can be reused for any future TTS without re-loading the reference clip. This is the recommended path to "personalise a voice for TTS" — same engine and quality as Voice Clone, but persistent across sessions.

### Custom Voice

Unified voice selector combining all available voices:

Built-in speakers: Standard Qwen3-TTS voices. Route to standard TTS.

Saved voices: Persistent voice prompts created from Voice Clone via the "Save as reusable voice" option. Stored as `.pt` files in `Library/qwen3-tts_voices/`. Routed to the Qwen3-TTS voice-clone engine — same engine that produces Voice Clone output, just loaded from the saved prompt instead of a fresh reference clip. Captures both timbre and prosody.

Trained models: RVC `.pth` files (legacy / imported), shown with `[Trained]` prefix. RVC is a voice converter, not a voice cloner — chained through TTS it inherits the base speaker's pitch, so the trained voice's natural pitch is lost. The `[Trained]` route in Custom Voice exists for back-compat with existing .pth files. For TTS use cases, use Saved Voices instead. For converting an existing vocal recording (e.g. a singer-swap), use Voice Conversion mode.

### Voice Conversion: Trained Model (RVC)

Convert a vocal recording using a trained RVC model.

Source Audio: An isolated vocal stem works best. Full mixes with background music cause artifacts.

Target Voice: A `[Trained]` .pth model in your library, or a `[Saved]` voice from Voice Clone (which routes through SeedVC zero-shot mode using the saved reference clip). For .pth files, the app automatically finds and uses the matching .index file for higher quality speaker-specific matching.

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

### Using Your Own Voice
Two paths, same engine — pick based on whether you'll re-use the voice:

**One-off (Voice Clone):** Provide a 10–30 second reference recording, type your text, click Generate. The AI extracts a speaker prompt and synthesizes the target text in that voice. Captures both timbre and prosody. Reference clip stays only for this generation.

**Reusable (Voice Clone + Save):** Same flow, but check **Save as reusable voice (signed)** and give the voice a name before generating. The cloned voice is persisted as a signed `.pt` file in `Library/qwen3-tts_voices/`. From then on, pick `[Saved] <name>` from Custom Voice mode's dropdown to speak any new text in that voice — no need to re-load the reference clip every time. Same engine, same quality, just persistent across sessions.

**Reference clip quality:** A clean 10–30 second clip is plenty. Past about a minute, more reference doesn't materially improve the clone — the engine extracts a speaker prompt, not a fine-tune. What matters is **consistency**: one speaker, no music or background noise, no heavy reverb, recorded with the same microphone in a quiet room. The clone captures whatever is in your reference, so room tone and mic colour follow through.

**Saved voice signing:** when you save a voice, the consent attestation you fill in (voice owner's name, intended use, attestation checkbox) is embedded into the `.pt` file's archive plus written as a `.consent.json` sidecar. Every audio file generated from that saved voice carries a C2PA assertion chained to that attestation, signed by your install's certificate — a verifiable provenance trail back to "the user who saved this voice attested to having permission for this use."

**Managing saved voices:** Pick a saved voice in Custom Voice mode to see its signature badge ("Signed by you" / "Signed (imported)" / "Unsigned" / "Tampered"). The Delete Voice button removes the `.pt` + sidecar + the reference clip used for SeedVC voice conversion.

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
