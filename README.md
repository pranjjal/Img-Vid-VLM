# VLM on Image and Video (Qwen2.5-VL)

## Project Description

This project is a hands-on multimodal AI demo that uses the `Qwen2.5-VL-3B-Instruct` vision-language model to understand both images and videos from natural-language prompts. The notebook shows a complete inference workflow: loading the model, preparing visual inputs, generating textual responses, and tuning video sampling settings (`fps`, `max_pixels`) to balance quality and GPU usage. It is designed as a practical starter for tasks like visual captioning, scene understanding, and step-by-step video event summarization.

This notebook demonstrates how to run a vision-language model on both:
- a single image
- a short video

It uses `Qwen/Qwen2.5-VL-3B-Instruct` from Hugging Face with the `transformers` library.

## File

- Notebook: `VLM_on_img_and_vid.ipynb`

## What the notebook does

1. Installs required dependencies.
2. Loads the Qwen2.5-VL model and processor.
3. Sends an image + prompt to generate a description.
4. Installs video dependency (`av`).
5. Sends a video + prompt to generate step-by-step events.

## Requirements

- Python 3.10+
- Jupyter environment (VS Code notebook, Jupyter Lab, or Colab)
- A GPU with CUDA support is strongly recommended

The notebook currently moves tensors to CUDA (`.to("cuda")`), so it expects a CUDA-enabled environment.

## Dependencies

Install inside the notebook or environment:

```bash
pip install -q transformers accelerate qwen-vl-utils[decord] av
```

## How to run

1. Open `VLM_on_img_and_vid.ipynb`.
2. Run cells top to bottom.
3. Wait for model loading (first run can take time).
4. Check output printed after each generation block.

## Customize inputs

- Image task:
  - Update the `image` URL in the image `messages` block.
  - Edit the text prompt (for example: `"Describe what is happening in this image."`).

- Video task:
  - Update `video_url` to any public URL or local file path.
  - Tune sampling and quality:
    - `fps`: lower for less compute, higher for more detail
    - `max_pixels`: lower for less VRAM use

## Notes and tips

- If you do not have CUDA:
  - replace `.to("cuda")` with `.to("cpu")`
  - expect slower generation

- If VRAM is limited:
  - reduce `max_new_tokens`
  - reduce `fps` and `max_pixels` for video

- In the first code cell, Python comments should use `#`, not `//`.
  - Example fix:
    - from `from PIL import Image //...`
    - to `from PIL import Image  # ...`

## Example outputs

- Image: natural-language description of scene and objects.
- Video: step-by-step narrative of events across sampled frames.

## License and model usage

This notebook uses a third-party model from Hugging Face:
- `Qwen/Qwen2.5-VL-3B-Instruct`

Please check and follow the model license and usage terms on its model page before production use.
