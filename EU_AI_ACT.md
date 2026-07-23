# EU AI Act Transparency Statement

**Last updated: June 7, 2026**
**Regulation (EU) 2024/1689 — Artificial Intelligence Act, as amended by the AI Omnibus (Council ST-9247-2026-INIT, 13 May 2026)**

Creative Mayhem UG ("the developer") publishes this transparency statement in accordance with the EU AI Act to provide clear, accessible information about the AI systems incorporated in rAIdio.bot ("the Software").

---

## 1. AI Systems Overview and Classification

rAIdio.bot incorporates the following AI systems. All systems run entirely on the user's local hardware. No AI processing occurs on remote servers.

| AI System | Function | Architecture | License | Classification |
|-----------|----------|--------------|---------|----------------|
| ACE-Step 1.5 | Music generation from text | Diffusion transformer (3.5B / 5B params) | Apache 2.0 | Potentially GPAI |
| ACE-Step 1.5 XL | Higher-quality music generation | Diffusion transformer (5B params) | Apache 2.0 | Potentially GPAI |
| ACE-Step v1 3.5B | Studio-quality music generation from text (APG guidance) | Diffusion transformer (3.5B params) | Apache 2.0 | Potentially GPAI |
| Qwen3-TTS | Text-to-speech synthesis | Autoregressive transformer (0.6B / 1.7B params) | Apache 2.0 | Narrow-task |
| Seed-VC | Voice conversion | DiT + wavenet vocoder | MIT | Narrow-task |
| RVC | Retrieval-based voice conversion | HuBERT + pitch extraction | MIT | Narrow-task |
| Meta Demucs | Audio source separation (stems) | Hybrid transformer/waveform U-Net | MIT | Narrow-task |
| OpenAI Whisper | Speech-to-text transcription | Encoder-decoder transformer | MIT | Narrow-task |
| Spotify basic-pitch | Audio-to-MIDI transcription | Neural network (ONNX) | Apache 2.0 | Narrow-task |
| BigVGAN v2 | Neural vocoder (waveform synthesis) | GAN | MIT | Component (not standalone) |
| CAMPPlus | Speaker embedding / verification | CNN | MIT | Narrow-task |
| RMVPE | Pitch extraction | CNN | MIT | Narrow-task |
| SilentCipher | Neural audio watermarking (AI-provenance mark) | Encoder + message-decoder DNN (STFT-domain) | MIT | Narrow-task |
| Prompt Enhancer | On-device prompt rewriting (text-to-text writing assist) | Autoregressive transformer (1.5B params) | Apache 2.0 | Potentially GPAI |

**Classification notes:**

- *ACE-Step 1.5 / XL / v1 3.5B* may meet the variety-of-tasks test for general-purpose AI (GPAI) under Article 3(63) of Regulation (EU) 2024/1689 because they can generate music across a wide range of styles and structures from free-form natural-language prompts. We do not independently verify whether the upstream training compute reached the 10²³ FLOP presumption threshold under Article 51(2); that determination rests with the upstream model provider (ACE-Studio / StepFun).
- *Prompt Enhancer (Qwen2.5-1.5B-Instruct)* is a general instruction-tuned language model and may meet the variety-of-tasks test for GPAI. rAIdio.bot constrains it to a single function — rewriting the user's rough prompt into a stronger music/voice generation prompt — via a fixed system prompt, and it runs entirely on-device under a bundled local inference server (no prompt or output leaves the machine). As with ACE-Step, any GPAI obligations rest with the upstream model provider (Alibaba Cloud / Qwen team), not Creative Mayhem UG (see §1.1); we do not independently verify whether upstream training compute reached the Article 51(2) systemic-risk threshold.
- All other bundled models perform a single, narrowly defined task (transcription, separation, pitch extraction, voice conversion, etc.) and do not meet the variety-of-tasks test for GPAI.

### 1.1. System provider vs model provider

rAIdio.bot is an **AI system provider**, not a GPAI **model provider**. We integrate pre-trained third-party models (listed above) into a system; we do not train GPAI models, fine-tune them at scale, or place GPAI models on the Union market.

The GPAI obligations in Articles 53–55 of Regulation (EU) 2024/1689 apply to model providers. They are therefore not directly applicable to Creative Mayhem UG. ACE-Step's potential GPAI status would place its upstream providers (ACE-Studio / StepFun) under those obligations, not us.

### 1.2. Not a high-risk AI system

rAIdio.bot is not a high-risk AI system. It does not implement any of the use cases enumerated in Annex III of Regulation (EU) 2024/1689: no biometric identification or categorisation, no education access or grading, no employment screening or performance evaluation, no creditworthiness or essential-services scoring, no law-enforcement or border-control use, no administration-of-justice or democratic-process use. It is also not covered by Annex I (it is not a safety component of any regulated product).

Accordingly, the obligations of Chapter III of Regulation (EU) 2024/1689 (Sections 1, 2 and 3) do not apply.

### 1.3. Article 5 prohibited practices

The Software does not implement any of the practices prohibited under Article 5, including biometric categorisation for sensitive inferences, real-time remote biometric identification, social scoring, or emotion recognition in the workplace or educational settings.

The AI Omnibus introduces two additional prohibitions, applicable from 2 December 2026:

- **Article 5(1a)** — AI systems that generate or manipulate non-consensual intimate material.
- **Article 5(1b)** — AI systems that generate or manipulate child sexual abuse material.

rAIdio.bot is not intended for either purpose. For systems where such generation is not intended, recital (6b) of the Omnibus requires "reasonable and adequate technical safety measures and other safeguards" against reasonably foreseeable misuse. The Software's safeguards include:

- **Usage restrictions.** EULA §4 and Content Policy §3 and §6 prohibit generating sexual content involving minors, non-consensual sexual content, deepfakes intended to deceive or harm, and voice cloning without documented consent from the voice owner.
- **Output controls.** Every audio output is signed with C2PA Content Credentials identifying it as AI-generated (see §3 below). Signing is mandatory and cannot be disabled.
- **Prompt-level content gate (always-on).** Text prompts submitted to the on-device Prompt Enhancer are screened by a compiled-in gate that refuses any prompt pairing minor-referencing terms with sexual terms before the prompt reaches the model. The refusal cannot be disabled.
- **Abuse detection (voice).** A cryptographic voice-consent verifier in the Voice panel checks every loaded `.pth` voice model against an embedded ES256 signature and the consent attestation recorded at training time. Unsigned or tampered models are flagged.
- **Notice and action.** The in-app crash-and-bug submission flow includes explicit abuse-report routing to chris@neitzert.com.

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

## 3. AI-Generated Content Marking (Article 50(2))

### Mandatory C2PA signing

Every audio file created by rAIdio.bot carries a C2PA (Coalition for Content Provenance and Authenticity) content credential — a cryptographically signed, tamper-evident record that documents:

- That the content was created with rAIdio.bot
- Which AI model was used to generate or process it
- When the content was created
- The creator's identity (as provided by the user)
- The full chain of tools and transformations applied

C2PA is the same open standard backed by Adobe, Microsoft, the BBC, and major digital camera manufacturers. The European Commission's Draft Code of Practice on AI transparency identifies C2PA as a satisfactory mechanism for compliance with Article 50(2) of Regulation (EU) 2024/1689.

**Signing is mandatory and cannot be disabled.** This satisfies Article 50(2)'s machine-readable-marking obligation directly, rather than relying on the user to opt in.

### In-signal neural watermarking (multi-layer marking)

In addition to the C2PA metadata layer, every AI-generated audio output carries an inaudible neural watermark embedded directly in the audio signal (SilentCipher, an open-source method released by Sony under the MIT licence). Where a C2PA credential is metadata that can be stripped when a file is re-encoded or re-uploaded, the in-signal watermark is carried by the audio samples themselves and survives common transformations (format conversion, MP3/FLAC encoding, resampling).

The two layers together — cryptographic C2PA credentials and an in-signal watermark — implement the multi-layer marking approach that the European Commission's Draft Code of Practice on AI transparency describes as best practice for Article 50(2), going beyond metadata alone.

The watermark is applied only to AI-generated output (music and synthetic speech). Audio that the user imports, or that is otherwise not AI-generated, is not watermarked, so the mark is never falsely asserted on a user's own material. The file Properties view in the application displays both layers — C2PA status and watermark detection — so a user, or a downstream platform, can verify the provenance of any file.

A neural watermark is a high-confidence indicator of AI origin, not a cryptographic proof: like all in-signal watermarks it can be degraded by deliberate adversarial processing or heavy neural recompression. It complements, and does not replace, the C2PA credential. Together they provide defence-in-depth for AI-content disclosure.

### Compliance deadline

Article 50(2) compliance deadline for rAIdio.bot is **2 December 2026** under Article 111(4) as inserted by the AI Omnibus (Council ST-9247-2026-INIT, 13 May 2026), because our first placement on the Union market is scheduled before 2 August 2026 and the Omnibus provides a four-month transitional period for providers in that position.

### User identity in credentials

Users control what identity information (name, email, URL, organisation) is embedded in credentials at sign-up time and via Settings → Identity. Users may use pseudonyms or leave optional identity fields blank; the signing certificate itself is per-install and self-issued.

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

The Software requires users to acknowledge consent requirements before using voice cloning or conversion features. The consent dialogue appears each session and cannot be permanently dismissed. In addition, a cryptographic verifier checks every loaded voice model (`.pth`) against an embedded ES256 signature and the consent attestation recorded at training time; the Voice panel surfaces Signed / Unsigned / Tampered / Invalid status for each model.

### Content Policy

The [Content Policy](CONTENT_POLICY.md) prohibits:
- Creating deepfakes intended to deceive or harm
- Non-consensual voice cloning
- Impersonation of real individuals
- Generation of sexual content involving minors
- Generation of non-consensual intimate content
- Circumventing platform detection systems

### Disclosure Support

AI-generated content carries two complementary machine-readable disclosure mechanisms anticipated by Article 50(2): C2PA content credentials (cryptographic metadata) and an inaudible in-signal neural watermark (see §3). Platforms and tools that support C2PA can automatically detect and label content created with rAIdio.bot; the in-signal watermark remains detectable even where the C2PA metadata has been stripped on re-upload or re-encoding.

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

## 9. Applicable Dates

The dates below reflect the AI Omnibus amendments (Council ST-9247-2026-INIT, 13 May 2026) to Regulation (EU) 2024/1689.

- **2 February 2025** — Article 5 prohibitions in force. The new Article 5(1a) (non-consensual intimate material) and 5(1b) (CSAM) prohibitions apply from 2 December 2026.
- **2 August 2025** — GPAI model provider obligations (Articles 53–55) applicable to *new* GPAI models placed on the Union market. Existing models: until 2 August 2027. *Not directly applicable to rAIdio.bot — we are a system provider, not a model provider.*
- **2 August 2026** — Article 50 transparency obligations apply to providers placing AI systems on the market on or after this date.
- **2 December 2026** — Article 50(2) compliance deadline for providers who placed systems on the market before 2 August 2026 (four-month grace per amended Article 111(4)). **rAIdio.bot target.**
- **2 December 2026** — New Article 5(1a) and 5(1b) prohibitions apply.
- **2 December 2027** — Chapter III high-risk obligations apply to Annex III systems. *Not applicable to rAIdio.bot (we are not a high-risk system).*
- **2 August 2028** — Chapter III high-risk obligations apply to Annex I systems. *Not applicable to rAIdio.bot.*

The developer commits to maintaining compliance with all applicable provisions as they take effect, and will update this statement when further amendments or implementing acts are adopted.

---

## 10. Contact

For questions about AI systems, training data, or EU AI Act compliance:

**info@rAIdio.bot**

---

## Sources

- Regulation (EU) 2024/1689 of the European Parliament and of the Council of 13 June 2024 (Artificial Intelligence Act). ELI: http://data.europa.eu/eli/reg/2024/1689/oj
- Council document ST-9247-2026-INIT, 13 May 2026 (Proposal for a Regulation amending Regulations (EU) 2024/1689 and (EU) 2018/1139 — the "Digital Omnibus on AI", 2025/0359 (COD)). https://data.consilium.europa.eu/doc/document/ST-9247-2026-INIT/en/pdf
- Legal review by JBViniol Rechtsanwälte (Dr. Lisa Käde), 22 May 2026.

---

*Creative Mayhem UG — Berlin, Germany*

© 2026 Creative Mayhem UG (haftungsbeschränkt). rAIdio.bot® is a registered trademark. AI-generated audio outputs carry C2PA provenance metadata. All other trademarks are property of their respective owners.
