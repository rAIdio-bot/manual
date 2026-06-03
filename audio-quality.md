## Simple

### Lossless by default

Music is generated and saved as 16-bit WAV at 44.1 kHz. No lossy compression is applied to generated audio — what you hear is exactly what the model produced.

### Clean playback

When your audio device runs at a different sample rate than a track — for example a 96 kHz optical/S-PDIF or high-resolution DAC output playing 44.1 kHz music — audio is converted to your device's rate with a high-quality sinc filter. The conversion is transparent, with no audible artifacts, and is prepared when the file loads so playback itself stays perfectly smooth.

### No brick-wall clipping

The master output uses a threshold-based limiter that passes signals below 0 dB through untouched. Only peaks above the threshold are gently compressed to prevent harsh clipping.

### Export options

Export your mixes as lossless WAV or MP3 (V0 VBR ~245 kbps via ffmpeg).

## Advanced

### Signal chain

All internal mixing, effects, and gain staging is performed in 32-bit floating point for maximum headroom. Signal flow from channel to master: clip → channel gain → mono FX chain → stereo pan → stereo FX chain → sum to stereo bus → master gain → transparent limiter.

### Generation format

Music is generated and saved as lossless 16-bit WAV at 44.1 kHz. No lossy compression is applied to generated audio.

### Resampling

When your audio device's native sample rate differs from a track's, audio is converted to the device rate with a high-quality sinc interpolation filter: 256 taps, a Blackman-Harris window, 256x oversampling, and 64-bit internal precision. The heavy oversampling is what keeps the conversion transparent even at large ratios — for example up-sampling 44.1 kHz material to a 96 kHz optical/S-PDIF or high-resolution DAC output — with no aliasing and no audible artifacts.

Two things follow from this design:

- **Quality.** The filter is deliberately high-order, and the conversion is identical whether you play to a basic 48 kHz output or a high-end 96 kHz path — so what reaches your DAC is a faithful reconstruction of the source.
- **Playback performance.** The conversion runs once, when a file is loaded, and never during playback. The real-time playback engine does not resample, so playback stays glitch-free and perfectly timed on any output device. The trade-off is a brief one-time preparation as a file opens: most files are instant, while a very long track played to a high output rate (for example an hour-plus to a 96 kHz device) can take a few moments to prepare.

### Transparent limiting

The master output uses a threshold-based limiter that passes signals below 0 dB through untouched. Only peaks above the threshold are gently compressed to prevent harsh clipping. This protects the output without imposing an "always on" compression character.

### Export options

- Export WAV: Lossless stereo PCM16 at the project sample rate.
- Export MP3: V0 VBR (~245 kbps) via ffmpeg's libmp3lame encoder.
- Export Stems: Each mixer channel rendered as a separate stereo WAV file.

All exports use atomic writes (write to .tmp, then rename) so partial files never appear on disk.
