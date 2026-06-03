# rAIdio.bot — Third-Party Notices

**Version 20260603**

This product includes open-source software components. Each component is subject to its own license terms. The complete machine-readable Software Bill of Materials (SBOM) with all 996 components is available in-app at **Settings > Licenses** and online at [github.com/rAIdio-bot/sbom](https://github.com/rAIdio-bot/sbom).

---

## Distribution form

For more information about copyright and licensing, please refer to the source files included in this distribution.

---

## Written offer for source code

rAIdio.bot contains software components that are licensed by the copyright holders as Free Software or Open Source software under the GNU General Public License, version 2 and/or 3, and/or GNU Lesser General Public License, version 2.1 and/or 3.0. Anyone can obtain the source code for these software components from us on a data carrier (e.g. USB memory stick). This offer is valid within three years after the most recent conveyance of the object code by us, and valid for as long as we offer spare parts or customer support for the respective product. Please send your request to the following email address `legal@creativemayhem.com` or via regular mail to the following address:

> Creative Mayhem UG (haftungsbeschränkt)  
> Attn: Source Request — rAIdio.bot  
> Alte Jakobstrasse 92  
> 10179 Berlin Germany

Please specify the address to which you wish us to send the source code. Additional product information (e.g. version number) will help us to identify the corresponding source code for you. The source code will be sent to the given address after reimbursement of the expenses actually incurred for providing the data carrier and shipping.

As a convenience, the corresponding source code for the components under licenses requiring source code availability is also available without charge at:

- <https://github.com/memescreamer/> — Creative Mayhem UG's vendor mirror of the upstream FOSS components used in rAIdio.bot.
- <https://github.com/rAIdio-bot/rAIdio-nodes> — Creative Mayhem UG's own GPL-3.0 patches authored for rAIdio.bot.

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
| rAIdio_aimdo_reset | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| zz_rAIdio_rvc_bool_fix | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| zz_rAIdio_rvc_loadaudio_alias | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| zz_rAIdio_rvc_infer_audio_fix | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| zz_rAIdio_rvc_train_dir_fix | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| zz_rAIdio_rvc_train_quote_fix | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| _python_embeded_overrides/sitecustomize.py | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |
| _python_embeded_overrides/fairseq | GPL-3.0 | [rAIdio-nodes](https://github.com/rAIdio-bot/rAIdio-nodes) |

---

## GNU General Public License v3.0

The following components are licensed under GPL-3.0. They run as separate processes and communicate with the rAIdio.bot application via localhost HTTP/WebSocket API. The proprietary Rust binary does not link to, embed, or compile any GPL-3.0 code. Users may freely modify all GPL-3.0 components. Source code is available at the URLs below.

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI | AI inference backend | [comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI) |
| comfy-aimdo | GPU memory dynamic offloader for ComfyUI (native lib in python_embeded) | [Comfy-Org/comfy-aimdo](https://github.com/Comfy-Org/comfy-aimdo) |
| ComfyUI-QwenTTS | Qwen3-TTS ComfyUI integration | [1038lab/ComfyUI-QwenTTS](https://github.com/1038lab/ComfyUI-QwenTTS) |
| SeedVC-ComfyUI | Seed-VC voice conversion node — wraps Seed-VC (GPL-3.0) and is distributed under GPL-3.0 by inheritance | [AIFSH/SeedVC-ComfyUI](https://github.com/AIFSH/SeedVC-ComfyUI) |
| Seed-VC | Zero-shot voice conversion model | [Plachtaa/seed-vc](https://github.com/Plachtaa/seed-vc) |

Full GPL-3.0 text: <https://www.gnu.org/licenses/gpl-3.0.html>

---

## Apache License 2.0

| Component | Description | Source |
|-----------|-------------|--------|
| ComfyUI_ACE-Step | ACE-Step ComfyUI integration | [billwuhao/ComfyUI_ACE-Step](https://github.com/billwuhao/ComfyUI_ACE-Step) |
| ACE-Step 1.5 model weights | Generative music model (Standard + XL) | [ace-step/ACE-Step](https://github.com/ace-step/ACE-Step) |
| Qwen3-TTS model weights | Text-to-speech (all variants) | [QwenLM/Qwen3-TTS](https://github.com/QwenLM/Qwen3-TTS) |
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
| soundfile (Python wrapper) | Audio file I/O — Python bindings (ships libsndfile binary inside the wheel; see LGPL row below) | [memescreamer/python-soundfile](https://github.com/memescreamer/python-soundfile/tree/0.13.1) |
| libvorbis / libogg (statically linked in ffmpeg) | Ogg Vorbis codec + container | [xiph.org/vorbis](https://xiph.org/vorbis/) |
| opus (statically linked in ffmpeg) | Opus audio codec | [opus-codec.org](https://opus-codec.org/) |

---

## Other Licenses

| Component | License | Source |
|-----------|---------|--------|
| Python (CPython, embedded) | PSF License | [python.org](https://www.python.org) |
| Symphonia | MPL-2.0 | [pdeljanov/Symphonia](https://github.com/pdeljanov/Symphonia) |
| ffmpeg | LGPL-2.1-or-later — our own minimal **audio-only** build (no `--enable-gpl`/`--enable-version3`; no patent-encumbered video encoders). Runs as a separate process; the proprietary Rust binary does not link it. | [ffmpeg.org](https://ffmpeg.org) |
| LAME / libmp3lame (statically linked in ffmpeg) | LGPL-2.0-or-later | [lame.sourceforge.io](https://lame.sourceforge.io/) |
| zlib (statically linked in ffmpeg) | Zlib | [zlib.net](https://zlib.net) |
| libsndfile (C library, bundled in soundfile wheel) | LGPL-2.1 | [memescreamer/libsndfile](https://github.com/memescreamer/libsndfile/tree/1.2.2) |
| 7-Zip | LGPL-2.1 / BSD-3-Clause | [7-zip.org](https://www.7-zip.org) |

---

## Full Component List

The complete list of **996 components** with versions, licenses, and homepage URLs is available:

- **In-app**: Settings > Licenses
- **Online (per release)**: [github.com/rAIdio-bot/sbom/releases](https://github.com/rAIdio-bot/sbom)

---

© 2026 Creative Mayhem UG (haftungsbeschränkt). rAIdio.bot® is a registered trademark. AI-generated audio outputs carry C2PA provenance metadata. All other trademarks are property of their respective owners.
