# Core Epoch

**Systems software in pure Rust — model quantization, real-time computer vision, and edge AI.**

Core Epoch LLC is an independent software and IP company. We build software across a range of industries, but our main work centers on quantization — running computer vision models smaller and faster than full precision, and more accurately than ONNX Runtime's own static quantizer, on CPUs without a GPU or a cloud service.

Our production source is proprietary; however, we offer some of our models for free here and on [Hugging Face](https://huggingface.co/CoreEpoch). Technical write-ups, benchmark packages, and source access are available under NDA: **contact@coreepoch.dev**.

---

## Products

### Kenosis — portable INT8 quantization for ONNX

Kenosis is a pure-Rust quantizer producing .onnx computer vision models that are smaller and faster than FP32 while maintaining high accuracy. Every model it produces runs on both ONNX Runtime and OpenVINO from the same file.

- ImageNet classifiers: 1.5–2.4× faster on stock ONNX Runtime, 4.4–9.5× on OpenVINO
- COCO detection: 93–94% of FP32 mAP retained, at 1.6–2.0× (PP-YOLOE+)
- RF-DETR transformer: 48.4 mAP against 28.9 for ONNX Runtime's own static quantizer at its default calibration
- Research published with DOI: [10.5281/zenodo.20657989](https://doi.org/10.5281/zenodo.20657989)

Measured on an Intel i5-13420H. Four quantized models are published on Hugging Face, including an ImageNet-1K classifier that scores 81.53% top-1 in a 7.2 MB file.

### Cryphex — multi-camera video analytics · [cryphex.dev](https://cryphex.dev)

Cryphex runs continuous object detection and tracking across multiple camera feeds, using Kenosis-quantized INT8 models, with no GPU required.

- Two 720p streams on the 320 px density tier: 30 fps per camera, full rate, on 2.5 CPU cores
- Four to six streams on the same tier: 90–97 detections per second aggregate
- Six cameras on the 640 px accuracy tier, on OpenVINO: 24.2 fps aggregate at ~7 CPU cores; the full-precision model manages 13.1 on the same budget
- The 640 file scores the same 40.6 COCO mAP on ONNX Runtime and OpenVINO

Measured headless on an Intel i5-13420H. Deployments are calibrated on the customer's own hardware: frames are sampled on site, the model is re-quantized on the box, and nothing is uploaded.

### Urim Lens — real-time depth-driven video rendering

Urim Lens turns any 2D video into a depth-driven 3D scene as it plays, in real time on the GPU.

---

## Open source

| Repo | What it is |
|---|---|
| [int8-models](https://github.com/CoreEpoch/int8-models) | Index, measurement protocol, and baseline-reproduction scripts for our published INT8 ONNX models. |
| [mcp-soundfx](https://github.com/CoreEpoch/mcp-soundfx) | Local text-to-SFX MCP server — Stable Audio Open 1.0 on your own NVIDIA GPU. |

---

<p align="center">
  <a href="https://coreepoch.dev">coreepoch.dev</a> · <a href="https://cryphex.dev">cryphex.dev</a> · <a href="mailto:contact@coreepoch.dev">contact@coreepoch.dev</a> · Charles Town, WV
</p>
