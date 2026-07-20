# Core Epoch

**Systems software written in Rust: INT8 ONNX quantization, encrypted model runtime, and multi-camera computer vision.**

## Kenosis · [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/)

Kenosis quantizes ONNX models to INT8 without retraining. Quantized models ship as encrypted `.cepk` files that load straight into memory in C, C++, and Python through our `kenosis_cepk` Rust library, so the raw ONNX graph and weights are never sitting on disk.

We measured each model against its FP32 original and the public INT8 version on Hugging Face, timing on a standard CPU at 4 threads:

| Model | Kenosis file size | CPU speed vs. public INT8 | Accuracy |
|---|---|---|---|
| Pocket-TTS 2m, 7m, 18m | 71% to 74% smaller than FP32 | 1.5x to 2.2x faster | Within measurement error of FP32 and the public INT8 |
| Piper (3 voices) | 71% to 74% smaller than FP32 | 5.2x to 5.7x faster | Within measurement error of FP32 and the public INT8 |
| Kokoro-82M | 75% smaller than FP32 | 3.8x faster | Within measurement error of FP32 and the public INT8 |
| MOSS-TTS-Nano | 70% smaller than FP32 | 2.0x faster | Within measurement error of FP32 and the public INT8 |
| NeMo Conformer-CTC (speech-to-text) | 45% smaller than FP32 | 2.8x faster | 3.92% word error rate (FP32 3.58%, public INT8 3.80%) |
| CREPE Tiny (pitch) | 74% smaller than FP32 | 23x faster | 99% of tones within 50 cents, same as FP32 |
| Parallel WaveGAN (vocoder) | 71% smaller than FP32 | 8.6x faster | Within measurement error of FP32 and the public INT8 |
| MODNet (portrait matting) | 74% smaller than FP32 | 2.3x faster | 0.755 mask IoU (FP32 0.759, public INT8 0.596) |
| UVDoc, PP-OCRv4 detection, SLANet (documents) | 51% to 75% smaller than FP32 | No public INT8 exists | Close to FP32; full figures on the site |

Full figures, test data and method: [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/#benchmarks). For model bundles, custom quantization, or licensing: [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/#licensing) · licensing@coreepoch.dev

## Cryphex · [cryphex.dev](https://cryphex.dev)

Cryphex runs object detection on multiple camera feeds at once on a standard CPU, with no GPU and no cloud service. Measured on one CPU: 12 cameras with 5 detections per second on each while the video stays at full frame rate, 59 detections per second in total, in 730 MB of memory. It runs as a background service or a desktop app.

## Urim Lens

Real-time depth estimation and 3D video effects for playback and live streams.

---

<p align="center">
  <a href="https://coreepoch.dev">coreepoch.dev</a> · <a href="https://cryphex.dev">cryphex.dev</a> · <a href="mailto:licensing@coreepoch.dev">licensing@coreepoch.dev</a> · Charles Town, WV
</p>
