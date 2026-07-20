# Core Epoch

**Systems software written in Rust: ONNX model quantization, multi-camera computer vision, and real-time video effects.**

## Kenosis · [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/)

Kenosis is a Rust quantizer. Quantized models often shrink file size at the cost of accuracy or speed. Kenosis models are smaller than the originals, keep accuracy near the original, and run **faster** on CPU with no retraining. Each ships as a standard `.onnx` file that runs on CPU in both ONNX Runtime and OpenVINO.

Published open-weight Kenosis models: [Hugging Face](https://huggingface.co/CoreEpoch) · [CoreEpoch/int8-models](https://github.com/CoreEpoch/int8-models).

Quantizer benchmarks below compare Kenosis outputs against FP32 and public INT8 on Hugging Face. Speeds are median ONNX Runtime CPU time at 4 threads.

| Model | Size vs. FP32 | Speed vs. FP32 | Speed vs. public INT8 | Accuracy |
|---|---|---|---|---|
| Kokoro-82M (voice synthesis) | 74% smaller | 1.43x faster | 4.1x faster | 2.74% WER (FP32 2.05%, public INT8 2.74%) |
| [tiny-voca](https://huggingface.co/CoreEpoch/tiny-voca-kenosis) (voice synthesis, published) | 75% smaller | 1.80x faster | - | 1.12% WER (FP32 1.00%) |
| NeMo Conformer-CTC Small (speech) | 45% smaller | 1.07x faster | 2.8x faster | 3.92% WER (FP32 3.58%, public INT8 3.80%) |
| MODNet (portrait matting) | 74% smaller | 1.37x faster | 2.3x faster | 0.755 mask IoU (FP32 0.759, public INT8 0.596) |
| UVDoc (page unwarping) | 75% smaller | 1.46x faster | - | 17.00 dB PSNR (FP32 16.99 dB) |

Full figures, test data, and method: [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/#benchmarks). Contact: contact@coreepoch.dev

## Cryphex · [cryphex.dev](https://cryphex.dev)

Cryphex runs object detection on multiple camera feeds at once on a standard CPU, with no GPU or cloud service. Measured on one CPU: 12 cameras at about 5 detections per second each. That is 59 detections per second in total, in about 730 MB of memory. It runs as a background service or a desktop app.

## Urim Lens

Real-time depth estimation and 3D video effects for playback and live streams.

---

<p align="center">
  <a href="https://coreepoch.dev">coreepoch.dev</a> · <a href="https://cryphex.dev">cryphex.dev</a> · <a href="mailto:contact@coreepoch.dev">contact@coreepoch.dev</a> · Charles Town, WV
</p>
