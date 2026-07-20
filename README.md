# Core Epoch

**Systems software in pure Rust — model quantization, real-time computer vision, and edge AI.**

Core Epoch LLC is an independent software and IP company. Our main work centers on quantization — running computer vision models smaller and faster than full precision on CPUs, with no GPU or cloud service required.

Our production source is proprietary; however, we offer some of our models here and on [Hugging Face](https://huggingface.co/CoreEpoch). Technical write-ups, benchmark packages, and source access are available under NDA: **contact@coreepoch.dev**.

---

## Products

### Kenosis — portable INT8 quantization for ONNX

Kenosis is a pure-Rust quantizer for ONNX computer vision models. Every model it produces runs on both ONNX Runtime and OpenVINO from the same file.

- ImageNet classification: 81.53% top-1 in a 7.2 MB file, down from 22.5 MB at full precision, within 0.03 of the FP32 baseline
- COCO detection: 45.7 AP in a 32.7 MB file, down from 81.0 MB — 95% of FP32 retained (RT-DETRv2-S)
- RF-DETR transformer: 48.4 mAP against 28.9 for ONNX Runtime's own static quantizer at its default calibration
- Research published with DOI: [10.5281/zenodo.20657989](https://doi.org/10.5281/zenodo.20657989)

Four quantized models are published on [Hugging Face](https://huggingface.co/CoreEpoch), each with its measured accuracy table.

### Cryphex — multi-camera video analytics · [cryphex.dev](https://cryphex.dev)

Cryphex runs continuous object detection and tracking across multiple camera feeds, using Kenosis-quantized INT8 models, with no GPU required.

- Twelve 720p cameras with the detector gated to 5 fps each: 29.8 fps of video per camera, 59 detections per second, 6.4 CPU cores, 722–730 MB of engine memory
- With the detector gate removed — every arriving frame detected — the same 320 px tier holds two cameras at full rate, and 90–97 detections per second aggregate across four to six streams
- Six cameras on the 640 px accuracy tier, on OpenVINO: 24.2 fps aggregate at ~7 CPU cores; the full-precision model manages 13.1 on the same budget
- The 640 file scores the same 40.6 COCO mAP on ONNX Runtime and OpenVINO

Measured headless on a single entry-level CPU; the twelve-camera row is the default configuration, the mean of three repeated steady-state passes. A zero-loss configuration is also available — in repeated measured passes, nothing taken in was lost between intake and output — at about 34% more CPU. Deployments are calibrated on your own hardware: frames are sampled on site, the model is re-quantized on the box, and nothing is uploaded.

### Urim Lens — real-time depth-driven video rendering

Urim Lens is a real-time depth estimation and video effect processing application for playback and live streams.

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
