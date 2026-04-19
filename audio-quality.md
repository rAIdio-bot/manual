## Simple

### Lossless by default

Music is generated and saved as 16-bit WAV at 44.1 kHz. No lossy compression is applied to generated audio — what you hear is exactly what the model produced.

### Clean playback

When your audio device runs at a different sample rate (e.g. 48 kHz), audio is resampled using a 256-tap sinc interpolation filter. The conversion is transparent with no audible artifacts.

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

When your audio device runs at a different sample rate (e.g. 48 kHz), audio is resampled using a 256-tap sinc interpolation filter for transparent conversion with no audible artifacts.

### Transparent limiting

The master output uses a threshold-based limiter that passes signals below 0 dB through untouched. Only peaks above the threshold are gently compressed to prevent harsh clipping. This protects the output without imposing an "always on" compression character.

### Export options

- Export WAV: Lossless stereo PCM16 at the project sample rate.
- Export MP3: V0 VBR (~245 kbps) via ffmpeg's libmp3lame encoder.
- Export Stems: Each mixer channel rendered as a separate stereo WAV file.

All exports use atomic writes (write to .tmp, then rename) so partial files never appear on disk.
