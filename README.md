# ⚡ Qwen-Image 2.1 (Text-to-Image & Multi-Image Edit) in Google Colab

This repository provides a ready-to-use Google Colab notebook for running **Qwen-Image 2.1** (both **Turbo 8-Step** and **Base 25-Step** checkpoints) powered by ComfyUI. Using T4-friendly `int8_convrot` quantized models, you can generate high-resolution images, create native transparent RGBA PNGs, and edit single or multiple images (up to 10 references at once)—completely free on a Google Colab T4 GPU.

**🎥 Watch the Tutorial:** [How to Use](https://www.youtube.com/watch?v=soon)

**🚀 Run in Colab:** [Open Google Colab Notebook](https://colab.research.google.com/drive/1gAfG7L7XHl_1pxSu5BZVppIuiInrAlSQ?usp=sharing)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/salman02-12/Qwen-Image-2.1-in-Google-Colab/blob/main/Qwen_Image_2_1_CoinNoin.ipynb)
[![Get Pro](https://img.shields.io/badge/Get%20Pro-PayPal-blue?logo=paypal)](https://www.paypal.com/ncp/payment/LKHUDLL9U3N6J)

---
<img src="./thumbnail.png" width="100%" />

## ✨ Features Supported in this Notebook

This notebook packages the complete Qwen-Image 2.1 ComfyUI workflow into 4 automated cells:

1. **⚙️ Setup Environment**: Automatically installs the latest ComfyUI, `aria2`, `uv`, and `xformers` optimized for Google Colab T4 GPUs.
2. **📥 High-Speed Model Downloader**: Uses Aria2c to rapidly fetch T4-friendly `int8_convrot` models:
   * **Turbo (Fast 8-Step):** `qwen_image_2.1_turbo_int8_convrot.safetensors` using the official 8-step `ManualSigmas` schedule.
   * **Base (25-Step / BG Removal):** `qwen_image_2.1_int8_convrot.safetensors` for standard 25-step sampling and background removal.
   * **Core Components:** Qwen3-VL 8B (`int8_convrot`) text encoder and Qwen-Image 2.1 VAE (`bf16`).
   * **Optional Prompt Enhancers (8.82 GB each):** Dedicated Qwen 3.5 9B models for Text-to-Image (`pe_t2i`) and Image Edit (`pe_i2i`).
3. **🎨 Text to Image (Cell 3)**:
   * Switch between **Turbo (Fast 8-Step)** and **Base (25-Step)** modes.
   * **Native Transparent PNGs (RGBA):** Generate images with real alpha channels directly from your prompt.
   * **Built-in Resolution Selector:** Choose popular aspect ratios (`1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `21:9`) and target megapixels (`1`–`4` MP).
   * **Optional Prompt Enhancer & Thinking Mode:** Automatically expand short prompts into rich, detailed descriptions using Qwen 3.5.
   * **KV Cache & OOM Control:** Adjust `CACHE_DEVICE` (`auto`, `gpu`, `cpu`, `off`) and `CACHE_DTYPE` (`default`, `int8`, `int4`) to stay comfortably within T4 VRAM limits, with 8-bit/16-bit PNG output and auto-download.
4. **🖌️ Single & Multi-Image Edit (Cell 4)**:
   * Upload **1 image** for standard editing or select **up to 10 images at once** for multi-image compositing and style/object transfers.
   * Reference uploaded images directly in your prompt using `<image1>`, `<image2>`, etc. (`<image1>` acts as the main edit target).
   * Reuse previously uploaded images without re-uploading by unchecking `UPLOAD_NEW_IMAGES`.
   * Includes optional **I2I Prompt Enhancer + Thinking Mode**, custom output dimensions, KV cache controls, and automatic download.

## 🛠️ How to Use

1. Click the **Open in Colab** badge above.
2. Go to **Runtime > Change runtime type** in the top menu and ensure **T4 GPU** is selected.
3. Run **Cell 1 (Setup Environment)** to install ComfyUI and all dependencies.
4. Go to **Cell 2 (Download Models)**:
   * Select `Turbo (Fast 8-Step)` (recommended for speed), `Base (25-Step / BG Removal)`, or `Both (Turbo + Base)`.
   * *(Optional)* Check `DOWNLOAD_PE_T2I` or `DOWNLOAD_PE_I2I` if you want to use the built-in Qwen 3.5 Prompt Enhancer.
   * Click **Play** and wait for the downloads to finish.
5. **To Generate Images (Cell 3 - Text to Image):**
   * Select your `MODEL_MODE`, enter your `PROMPT`, pick an `ASPECT_RATIO`, and keep `MEGAPIXELS = 1` for smooth T4 performance.
   * *(Tip for Transparent PNGs)* Format your prompt as: `This is an RGBA format image with transparency. [your subject]. The image has an alpha channel and a transparent background.`
   * Click **Play** to generate and automatically download your image.
6. **To Edit Images (Cell 4 - Image Edit):**
   * Keep `UPLOAD_NEW_IMAGES` checked to upload 1 to 10 images (or uncheck it to reuse your last uploaded images).
   * Write your edit instructions in `PROMPT` (for multiple images, refer to them as `<image1>`, `<image2>`, etc.).
   * Click **Play**, select your image(s) when prompted, and wait for the edited output.
   * *(Tip)* If you hit an Out of Memory (OOM) error on T4, lower `RESOLUTION` to `1024` or `768`, and/or change `CACHE_DEVICE` to `cpu` or `off`.

## 🤝 Credits

* **Notebook Creator:** [@CoinNoin](https://www.youtube.com/@CoinNoin)
* **Built with Qwen:** [QwenLM / Qwen-Image-2.1](https://github.com/QwenLM/Qwen-Image-2.1) *(Check the Qwen Research License before commercial use)*
* **ComfyUI Repackaged Models:** [Comfy-Org / Qwen-Image-2.1](https://huggingface.co/Comfy-Org/Qwen-Image-2.1)
