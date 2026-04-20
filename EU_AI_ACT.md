# EU AI Act Transparency Statement

**Last updated: April 15, 2026**
**Regulation (EU) 2024/1689 — Artificial Intelligence Act**

Creative Mayhem UG ("the developer") publishes this transparency statement in accordance with the EU AI Act to provide clear, accessible information about the AI systems incorporated in rAIdio.bot ("the Software").

---

## 1. AI Systems Overview

rAIdio.bot incorporates the following AI systems. All systems run entirely on the user's local hardware. No AI processing occurs on remote servers.

| AI System | Function | Model Architecture | License |
|-----------|----------|-------------------|---------|
| ACE-Step 1.5 | Music generation from text | Diffusion transformer (3.5B / 5B params) | Apache 2.0 |
| ACE-Step 1.5 XL | Higher-quality music generation | Diffusion transformer (5B params) | Apache 2.0 |
| Qwen3-TTS | Text-to-speech synthesis | Autoregressive transformer (0.6B / 1.7B params) | Apache 2.0 |
| Seed-VC | Voice conversion | DiT + wavenet vocoder | MIT |
| RVC | Retrieval-based voice conversion | HuBERT + pitch extraction | MIT |
| Meta Demucs | Audio source separation (stems) | Hybrid transformer/waveform U-Net | MIT |
| OpenAI Whisper | Speech-to-text transcription | Encoder-decoder transformer | MIT |
| Spotify basic-pitch | Audio-to-MIDI transcription | Neural network (ONNX) | Apache 2.0 |
| BigVGAN v2 | Neural vocoder (waveform synthesis) | GAN | MIT |
| CAMPPlus | Speaker embedding / verification | CNN | MIT |
| RMVPE | Pitch extraction | CNN | MIT |

**Risk classification:** All AI systems in the Software fall under the general-purpose AI (GPAI) category. None constitute high-risk AI systems as defined in Annex III of the Regulation. The Software does not perform biometric identification, social scoring, emotion recognition for enforcement purposes, or any prohibited practice under Article 5.

---

## 2. Training Data Provenance

### Music Generation (ACE-Step 1.5)

ACE-Step 1.5 is trained exclusively on licensed and public domain audio. The model developer (ACE-Step) has documented a transparent and legally sound training methodology. The training dataset does not include copyrighted commercial recordings obtained without license.

We selected ACE-Step specifically because the provenance of the training data is clean and documented. If a user's AI-generated content is ever challenged, the model's training data provenance is part of their defense.

### Text-to-Speech (Qwen3-TTS)

Qwen3-TTS is developed by Alibaba Cloud and released under Apache 2.0. Training data documentation is maintained by the model developer.

### Voice Conversion (Seed-VC, RVC)

These models are trained on publicly available speech datasets. They perform voice transformation on user-provided input audio — they do not generate speech from text independently.

### Speech Recognition (Whisper)

OpenAI Whisper is trained on 680,000 hours of multilingual audio from the internet. Model documentation is maintained by OpenAI.

### Source Separation (Demucs)

Meta Demucs is trained on the MUSDB18 dataset (licensed for research) and additional internal Meta datasets. Model documentation is maintained by Meta.

---

## 3. AI-Generated Content Marking

### C2PA Content Credentials

Every file created by rAIdio.bot can carry a C2PA (Coalition for Content Provenance and Authenticity) content credential — a cryptographically signed, tamper-evident record that documents:

- That the content was created with rAIdio.bot
- Which AI model was used to generate or process it
- When the content was created
- The creator's identity (as provided by the user)
- The full chain of tools and transformations applied

C2PA is the same open standard backed by Adobe, Microsoft, the BBC, and major digital camera manufacturers. It provides machine-readable disclosure of AI-generated content as contemplated by Article 50(2) of the EU AI Act.

### User Control

- C2PA signing is enabled by default and can be disabled by the user in Settings > Provenance
- Users control what identity information (name, email, URL) is embedded in credentials
- Users may use pseudonyms or leave identity fields blank
- The developer strongly recommends keeping C2PA enabled

---

## 4. No Data Collection

The Software collects no personal data, usage data, telemetry, or analytics of any kind. All AI processing occurs locally on the user's hardware. No audio, text, voice recordings, or generated content is transmitted to any server operated by the developer.

This is a structural design choice, not merely a policy promise. There is no server infrastructure to receive user data. Full details are documented in the [Privacy Policy](PRIVACY.md).

This design satisfies the data minimization principle under GDPR Article 5(1)(c) by eliminating data collection entirely.

---

## 5. User Rights and Controls

### Transparency

- Users are informed that AI models power the generation features through in-app documentation, the setup wizard, and this statement
- The specific model used for each operation is logged in the application's local log file
- C2PA credentials provide per-file transparency about AI involvement

### Human Oversight

- All AI generation is user-initiated — the Software does not generate content autonomously
- Users review, edit, and approve all outputs before saving or exporting
- The Editor and Mixer provide full manual control over AI-generated audio
- Users can modify, remix, or discard any AI output at any time

### Opt-Out and Control

- All AI features are tools activated by the user, not automatic processes
- Voice cloning and conversion require explicit user action and consent acknowledgment
- No AI feature runs without the user's direct instruction
- Users may use the Software's manual editing tools without engaging AI features

---

## 6. Synthetic Media Safeguards

### Voice Consent

The Software requires users to acknowledge consent requirements before using voice cloning or conversion features. The consent dialogue appears each session and cannot be permanently dismissed.

### Content Policy

The [Content Policy](CONTENT_POLICY.md) prohibits:
- Creating deepfakes intended to deceive or harm
- Non-consensual voice cloning
- Impersonation of real individuals
- Circumventing platform detection systems

### Disclosure Support

C2PA content credentials provide the machine-readable AI disclosure mechanism anticipated by Article 50 of the EU AI Act. Platforms and tools that support C2PA can automatically detect and label AI-generated content created with rAIdio.bot.

---

## 7. Open-Source Transparency

All AI models distributed with the Software are open-source or open-weight, released under permissive or copyleft licenses. Users have full access to:

- Model weights (distributed with the Software)
- Model source code (available at the URLs listed in the [Third-Party Notices](THIRD_PARTY_NOTICES.md))
- This transparency documentation

GPL-licensed components (ComfyUI and related nodes) run as separate processes and communicate with the proprietary application via localhost API. Source code for all GPL components is publicly available. Users may modify these components freely.

---

## 8. Environmental Impact

All AI inference runs on the user's local GPU. The developer does not operate data centers or cloud GPU infrastructure for inference. Energy consumption is determined by the user's hardware and usage patterns. Typical music generation (2-minute song) requires approximately 40-60 seconds of GPU computation on a modern consumer GPU.

---

## 9. Ongoing Compliance

The developer monitors the implementation timeline of the EU AI Act and will update this statement and the Software's documentation as specific obligations come into force. Key dates:

- **February 2, 2025**: Prohibited practices provisions apply
- **August 2, 2025**: GPAI model obligations apply
- **August 2, 2026**: Full application of remaining provisions

The developer commits to maintaining compliance with all applicable provisions as they take effect.

---

## 10. Contact

For questions about AI systems, training data, or EU AI Act compliance:

**info@rAIdio.bot**

---

*Creative Mayhem UG — Berlin, Germany*

© 2026 Creative Mayhem UG (haftungsbeschränkt). rAIdio.bot® is a registered trademark. AI-generated audio outputs carry C2PA provenance metadata. All other trademarks are property of their respective owners.
