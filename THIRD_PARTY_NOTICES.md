# rAIdio.bot — Third-Party Notices

**Version 20260415**

This product includes open-source software components. Each component is subject to its own license terms. The complete machine-readable Software Bill of Materials (SBOM) with all 783 components is available in-app at **Settings > Licenses**.

---

## rAIdio.bot Original Code

| Component | License | Source |
|-----------|---------|--------|
| rAIdio.bot application (Rust/Tauri/Svelte) | Proprietary | Copyright (c) 2025-2026 Christopher Neitzert and Creative Mayhem UG |
| rAIdio_nodes (SaveAudioWAV) | Apache 2.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| ComfyUI-ChordMidi (ChordDetect, MidiTranscribe) | Apache 2.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| 00_rAIdio_rvc_patch | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| 00_rAIdio_torchaudio_patch | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| rAIdio_whisper_patch | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| rAIdio_xl_patch (RaidioXLLoader) | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |

---

## GNU General Public License v3.0

The following components are licensed under GPL-3.0. They run as separate processes and communicate with the rAIdio.bot application via localhost HTTP/WebSocket API. The proprietary Rust binary does not link to, embed, or compile any GPL-3.0 code. Users may freely modify all GPL-3.0 components. Source code is available at the URLs below.

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI | AI inference backend | [comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI) |
| ComfyUI-QwenTTS | Qwen3-TTS ComfyUI integration | [AIFSH/ComfyUI-QwenTTS](https://github.com/AIFSH/ComfyUI-QwenTTS) |
| SeedVC-ComfyUI | Seed-VC voice conversion node | [AIFSH/SeedVC-ComfyUI](https://github.com/AIFSH/SeedVC-ComfyUI) |
| ffmpeg | Multimedia framework (static build) | [ffmpeg.org](https://ffmpeg.org) |

Full GPL-3.0 text: https://www.gnu.org/licenses/gpl-3.0.html

---

## Apache License 2.0

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI_ACE-Step | ACE-Step ComfyUI integration | [ace-step/ComfyUI_ACE-Step](https://github.com/ace-step/ComfyUI_ACE-Step) |
| ACE-Step 1.5 model weights | Generative music model (Standard + XL) | — |
| Qwen3-TTS model weights | Text-to-speech (all variants) | Alibaba Cloud |
| Spotify basic-pitch | Audio-to-MIDI transcription (ONNX) | [spotify/basic-pitch](https://github.com/spotify/basic-pitch) |
| Tauri | Application framework | [tauri.app](https://tauri.app) |
| cpal | Cross-platform audio output | [RustAudio/cpal](https://github.com/RustAudio/cpal) |

Full Apache 2.0 text: https://www.apache.org/licenses/LICENSE-2.0

---

## MIT License

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI-RVC | RVC voice conversion node | [RVC-Project](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI) |
| ComfyUI-Demucs-AudioSeparator | Demucs stem separation node | [Meisoftcoltd](https://github.com/Meisoftcoltd/ComfyUI-Demucs-AudioSeparator) |
| Meta Demucs | Source separation model | [facebookresearch/demucs](https://github.com/facebookresearch/demucs) |
| OpenAI Whisper | Speech recognition model | [openai/whisper](https://github.com/openai/whisper) |
| faster-whisper | CTranslate2-based Whisper inference | [SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper) |
| BigVGAN v2 | Neural vocoder (22kHz + 44kHz) | [NVIDIA/BigVGAN](https://github.com/NVIDIA/BigVGAN) |
| CAMPPlus | Speaker embedding model | [modelscope/FunASR](https://github.com/modelscope/FunASR) |
| RMVPE | Pitch extraction model | — |
| RVC pretrained models | HuBERT, discriminators | [lj1995/VoiceConversionWebUI](https://huggingface.co/lj1995/VoiceConversionWebUI) |
| Seed-VC model weights | Zero-shot voice conversion | [Plachtaa/seed-vc](https://github.com/Plachtaa/seed-vc) |
| rubato | Audio resampling (sinc interpolation) | [HEnquist/rubato](https://github.com/HEnquist/rubato) |
| realfft | Real-to-complex FFT | [HEnquist/realfft](https://github.com/HEnquist/realfft) |
| Svelte | Frontend framework | [svelte.dev](https://svelte.dev) |

---

## BSD-3-Clause License

| Component | Description | Source |
|-----------|-------------|--------|
| WaveSurfer.js | Waveform visualization | [katspaugh/wavesurfer.js](https://github.com/katspaugh/wavesurfer.js) |
| PyTorch / torchaudio | ML framework | [pytorch.org](https://pytorch.org) |

---

## Other Licenses

| Component | License | Source |
|-----------|---------|--------|
| Python (CPython, embedded) | PSF License | [python.org](https://www.python.org) |
| Symphonia | MPL-2.0 | [pdeljanov/Symphonia](https://github.com/pdeljanov/Symphonia) |
| soundfile / libsndfile | BSD-3-Clause / LGPL-2.1 | — |
| 7-Zip | LGPL-2.1 / BSD-3-Clause | [7-zip.org](https://www.7-zip.org) |

---

## Full Component List

The complete list of **783 components** with versions, licenses, and homepage URLs is available:

- **In-app**: Settings > Licenses
- **On disk**: `src-tauri/assets/sbom_licenses.json`

---

*Copyright (c) 2025-2026 Creative Mayhem UG. All rights reserved.*
