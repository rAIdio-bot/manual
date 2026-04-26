# rAIdio.bot — Third-Party Notices

**Version 20260426**

This product includes open-source software components. Each component is subject to its own license terms. The complete machine-readable Software Bill of Materials (SBOM) with all 803 components is available in-app at **Settings > Licenses** and online at [github.com/rAIdio-bot/sbom](https://github.com/rAIdio-bot/sbom).

---

## rAIdio.bot Original Code

| Component | License | Source |
|-----------|---------|--------|
| rAIdio.bot application (Rust/Tauri/Svelte) | Proprietary | © 2026 Creative Mayhem UG (haftungsbeschränkt) |
| rAIdio_nodes (SaveAudioWAV) | Apache 2.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| ComfyUI-ChordMidi (ChordDetect, MidiTranscribe) | Apache 2.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| 00_rAIdio_rvc_patch | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| 00_rAIdio_torchaudio_patch | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| 00_rAIdio_safe_load_patch | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| rAIdio_whisper_patch | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| rAIdio_xl_patch (RaidioXLLoader) | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |

---

## GNU General Public License v3.0

The following components are licensed under GPL-3.0. They run as separate processes and communicate with the rAIdio.bot application via localhost HTTP/WebSocket API. The proprietary Rust binary does not link to, embed, or compile any GPL-3.0 code. Users may freely modify all GPL-3.0 components. Source code is available at the URLs below.

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI | AI inference backend | [comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI) |
| ComfyUI-QwenTTS | Qwen3-TTS ComfyUI integration | [1038lab/ComfyUI-QwenTTS](https://github.com/1038lab/ComfyUI-QwenTTS) |
| SeedVC-ComfyUI | Seed-VC voice conversion node — wraps Seed-VC (GPL-3.0) and is distributed under GPL-3.0 by inheritance | [AIFSH/SeedVC-ComfyUI](https://github.com/AIFSH/SeedVC-ComfyUI) |
| Seed-VC | Zero-shot voice conversion model | [Plachtaa/seed-vc](https://github.com/Plachtaa/seed-vc) |
| ffmpeg | Multimedia framework (static build, GPL-3.0-or-later effective via `--enable-gpl --enable-version3` and bundled GPL libraries) | [ffmpeg.org](https://ffmpeg.org) |

Full GPL-3.0 text: <https://www.gnu.org/licenses/gpl-3.0.html>

---

## Apache License 2.0

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI_ACE-Step | ACE-Step ComfyUI integration | [billwuhao/ComfyUI_ACE-Step](https://github.com/billwuhao/ComfyUI_ACE-Step) |
| ACE-Step 1.5 model weights | Generative music model (Standard + XL) | [ace-step/ACE-Step](https://github.com/ace-step/ACE-Step) |
| Qwen3-TTS model weights | Text-to-speech (all variants) | Alibaba Cloud |
| Spotify basic-pitch | Audio-to-MIDI transcription (ONNX) | [spotify/basic-pitch](https://github.com/spotify/basic-pitch) |
| RMVPE | Pitch extraction model | [Dream-High/RMVPE](https://github.com/Dream-High/RMVPE) |
| OpenCV (C++ runtime, embedded in opencv-python-headless wheel) | Computer vision library | [opencv/opencv](https://github.com/opencv/opencv) |
| Tauri | Application framework | [tauri.app](https://tauri.app) |
| cpal | Cross-platform audio output | [RustAudio/cpal](https://github.com/RustAudio/cpal) |

Full Apache 2.0 text: <https://www.apache.org/licenses/LICENSE-2.0>

---

## MIT License

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI-RVC | RVC voice conversion node | [RVC-Project](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI) |
| ComfyUI-Demucs-AudioSeparator | Demucs stem separation node — thin wrapper over Meta Demucs (MIT); treated as MIT through the underlying library | [Meisoftcoltd](https://github.com/Meisoftcoltd/ComfyUI-Demucs-AudioSeparator) |
| Meta Demucs | Source separation model | [facebookresearch/demucs](https://github.com/facebookresearch/demucs) |
| OpenAI Whisper | Speech recognition model | [openai/whisper](https://github.com/openai/whisper) |
| faster-whisper | CTranslate2-based Whisper inference | [SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper) |
| BigVGAN v2 | Neural vocoder (22kHz + 44kHz) | [NVIDIA/BigVGAN](https://github.com/NVIDIA/BigVGAN) |
| CAMPPlus | Speaker embedding model | [modelscope/FunASR](https://github.com/modelscope/FunASR) |
| RVC pretrained models | HuBERT, discriminators | [lj1995/VoiceConversionWebUI](https://huggingface.co/lj1995/VoiceConversionWebUI) |
| opencv-python (Python wrapper portion of opencv-python-headless wheel) | Python bindings for OpenCV | [opencv/opencv-python](https://github.com/opencv/opencv-python) |
| picklescan | Pickle-file static analyzer | [mmaitre314/picklescan](https://github.com/mmaitre314/picklescan) |
| rubato | Audio resampling (sinc interpolation) | [HEnquist/rubato](https://github.com/HEnquist/rubato) |
| realfft | Real-to-complex FFT | [HEnquist/realfft](https://github.com/HEnquist/realfft) |
| Svelte | Frontend framework | [svelte.dev](https://svelte.dev) |

---

## BSD-3-Clause License

| Component | Description | Source |
|-----------|-------------|--------|
| WaveSurfer.js | Waveform visualization | [katspaugh/wavesurfer.js](https://github.com/katspaugh/wavesurfer.js) |
| PyTorch / torchaudio | ML framework | [pytorch.org](https://pytorch.org) |
| torchcodec | Audio codec wrapper | [pytorch/torchcodec](https://github.com/pytorch/torchcodec) |

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

The complete list of **803 components** with versions, licenses, and homepage URLs is available:

- **In-app**: Settings > Licenses
- **Online (per release)**: [github.com/rAIdio-bot/sbom/releases](https://github.com/rAIdio-bot/sbom)

---

© 2026 Creative Mayhem UG (haftungsbeschränkt). rAIdio.bot® is a registered trademark. AI-generated audio outputs carry C2PA provenance metadata. All other trademarks are property of their respective owners.
