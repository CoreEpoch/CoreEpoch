# Core Epoch

**Systems software in pure Rust: model quantization and multi-camera vision.**

Core Epoch builds systems software in pure Rust. We optimize and deploy computer vision models to run fast and efficiently on standard CPUs, eliminating the need for dedicated GPUs or cloud inference.

Our production source is proprietary; however, we offer verified INT8 models here and on [Hugging Face](https://huggingface.co/CoreEpoch). Technical packages, benchmark evaluations, and source licensing are available under NDA: **contact@coreepoch.dev**.

---

## Products

### Kenosis: Computer Vision Model Optimization · [coreepoch.dev/kenosis](https://coreepoch.dev/kenosis/)

Kenosis makes computer vision models smaller, faster, and cheaper to run, retaining near-lossless accuracy without retraining. It produces portable INT8 for ONNX vision models where the same artifact runs on stock ONNX Runtime and OpenVINO.

At its default calibration, the INT8 quantizer built into ONNX Runtime loses 20% to 91% of these models' accuracy. Kenosis keeps 95.0% to 99.96% of it, with no retraining. Speeds are ONNX Runtime on one thread of an Intel Core i5-13420H:

- RT-DETRv2-S (COCO val2017): 45.7 AP (95.0% retained vs 48.1 AP baseline), 81 MB to 32.7 MB (60% smaller), 512 ms to 301 ms (70% faster)
- EdgeNeXt-S (ImageNet-1K): 81.535% top-1 (99.96% retained vs 81.565% baseline), 22.5 MB to 7.16 MB (68% smaller), 62 ms to 47 ms (32% faster)
- XCiT-Tiny-12-p8 (ImageNet-1K): 81.16% top-1 (99.93% retained vs 81.22% baseline), 27.0 MB to 8.59 MB (68% smaller), 131 ms to 96 ms (36% faster)
- Research publication: [Fusion-Aware QDQ Placement](https://coreepoch.dev/research/kenosis-fusion-aware-qdq-placement.html) (DOI: [10.5281/zenodo.20657989](https://doi.org/10.5281/zenodo.20657989))

Published models with empirical accuracy tables are available on [Hugging Face](https://huggingface.co/CoreEpoch).

### Cryphex: Multi-Camera Computer Vision · [cryphex.dev](https://cryphex.dev)

Cryphex combines Kenosis model quantization with a Rust pipeline to run continuous multi-camera vision directly on standard CPUs. By eliminating dedicated GPUs and cloud inference, it unlocks computer vision on smaller hardware budgets with zero ongoing cloud fees:

- Hardware: Standard host CPU; no dedicated GPU or add-in accelerator required
- Cadence: Detection runs on every camera at all times, 5 times per second each at 12 cameras, while video keeps its full frame rate
- Multi-Stream Density: 12 streams on CPU (59 det/s, 730 MB RAM)
- Pipeline: Pure Rust, powered by Kenosis INT8
- Deployment: Background service daemon or desktop application
- Operation: Fully offline or online with zero cloud dependency

### Urim Lens: Real-Time Depth-Driven Video Processing

Real-time depth estimation and video effect processing application for playback and live streams.

---

## Open source

| Repo | What it is |
|---|---|
| [int8-models](https://github.com/CoreEpoch/int8-models) | Index of our published INT8 ONNX models. |
| [mcp-soundfx](https://github.com/CoreEpoch/mcp-soundfx) | Local text-to-SFX MCP server running Stable Audio Open 1.0. |

---

<p align="center">
  <a href="https://coreepoch.dev">coreepoch.dev</a> · <a href="https://cryphex.dev">cryphex.dev</a> · <a href="mailto:contact@coreepoch.dev">contact@coreepoch.dev</a> · Charles Town, WV
</p>
