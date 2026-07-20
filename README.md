# Core Epoch

**Systems software in pure Rust: model quantization and multi-camera vision.**

## Kenosis · [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/)

Kenosis quantizes ONNX computer vision models to 8-bit integers (INT8) without retraining, and the same file runs on ONNX Runtime and OpenVINO. These models are free on [Hugging Face](https://huggingface.co/CoreEpoch), each quantized with Kenosis by Core Epoch and measured against its FP32 original:

| Model | Task | INT8 vs FP32 | Size | Speed vs FP32 |
|---|---|---|---|---|
| [RF-DETR Base](https://huggingface.co/CoreEpoch/rfdetr-base-int8-onnx) | COCO detection | 53.12 vs 53.32 AP | 115.1 → 41.9 MB | 67% faster |
| [RT-DETRv2-S](https://huggingface.co/CoreEpoch/rtdetrv2-s-int8-onnx) | COCO detection | 45.67 vs 48.13 AP | 81.0 → 32.7 MB | 70% faster |
| [EdgeNeXt-S](https://huggingface.co/CoreEpoch/edgenext-small-int8-imagenet) | ImageNet | 81.535% vs 81.565% top-1 | 22.5 → 7.16 MB | 32% faster |
| [XCiT-Tiny-12/P8](https://huggingface.co/CoreEpoch/xcit-tiny12-p8-int8-imagenet) | ImageNet | 81.16% vs 81.22% top-1 | 27.0 → 8.59 MB | 36% faster |
| [TinyViT-5M](https://huggingface.co/CoreEpoch/tinyvit-5m-int8-imagenet) | ImageNet | 80.53% vs 80.87% top-1 | 22.1 → 9.23 MB | about the same |

Speeds are ONNX Runtime on one CPU thread. Index of the published files: [int8-models](https://github.com/CoreEpoch/int8-models). We also quantize customers' models for a flat fee per model, and license Kenosis to teams that want to run it themselves: [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/#licensing).

## Cryphex · [cryphex.dev](https://cryphex.dev)

Cryphex runs object detection on every camera feed at once on a standard CPU, with no GPU and no cloud service. Measured on one CPU: 12 cameras with 5 detections per second on each while the video keeps its full frame rate, 59 detections per second in total, in 730 MB of memory. It runs as a background service or a desktop app.

## Urim Lens

Real-time depth estimation and video effects for playback and live streams.

---

<p align="center">
  <a href="https://coreepoch.dev">coreepoch.dev</a> · <a href="https://cryphex.dev">cryphex.dev</a> · <a href="mailto:contact@coreepoch.dev">contact@coreepoch.dev</a> · Charles Town, WV
</p>
