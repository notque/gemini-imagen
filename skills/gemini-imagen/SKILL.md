---
name: gemini-imagen
description: >
  Generate images using Google Gemini's image generation APIs via Python CLI.
  Use for "generate image", "create image", "gemini image", "AI image",
  or when needing AI image generation in Claude Code.
version: 1.0.0
command: /imagen
routing:
  triggers:
    - generate image
    - create image
    - gemini image
    - AI image
    - text to image
  complexity: simple
  category: image-generation
---

# Gemini Imagen

Generate images from text prompts using Google's Gemini APIs. This plugin gives Claude Code the ability to generate images directly.

---

## Quick Start

```bash
# Generate an image
python3 ~/.claude/plugins/gemini-imagen/skills/gemini-imagen/scripts/generate_image.py \
  --prompt "A cute cartoon cat" \
  --output cat.png
```

---

## CRITICAL: Exact Model Names

**Use ONLY these exact model strings:**

| Model String | Speed | Best For |
|--------------|-------|----------|
| `gemini-2.5-flash-image` | Fast (2-5s) | Drafts, iterations |
| `gemini-3-pro-image-preview` | Slower (5-15s) | Quality, text rendering, 2K |

**Common mistakes:**
- `gemini-2.5-flash-preview-05-20` - WRONG (date suffixes are for text models)
- `gemini-2.5-pro-image` - WRONG (doesn't exist)
- `gemini-3-flash-image` - WRONG (doesn't exist)

---

## Instructions

### Step 1: Check API Key

```bash
echo "GEMINI_API_KEY is ${GEMINI_API_KEY:+set}"
```

If not set, tell the user to run `/imagen:setup`.

### Step 2: Install Dependencies

```bash
pip install google-genai Pillow
```

### Step 3: Generate Image

```bash
python3 ~/.claude/plugins/gemini-imagen/skills/gemini-imagen/scripts/generate_image.py \
  --prompt "YOUR PROMPT HERE" \
  --output /path/to/output.png
```

### Step 4: Verify Output

```bash
ls -la /path/to/output.png
```

---

## Model Selection

| Use Case | Model | Why |
|----------|-------|-----|
| Iterating on prompts | `gemini-2.5-flash-image` | Fast feedback (2-5s) |
| Final asset | `gemini-3-pro-image-preview` | Best quality |
| Game sprites | `gemini-2.5-flash-image` | Many images, consistent |
| Text in image | `gemini-3-pro-image-preview` | Better typography |
| Batch generation | `gemini-2.5-flash-image` | Cost effective |

---

## Post-Processing Options

### Remove Watermarks (`--remove-watermark`)

Removes bright pixels from image corners. Very useful for cleaning up generated images.

### Background Transparency (`--transparent-bg`)

Converts solid-color backgrounds to transparent. Great for sprites and icons.

```bash
python3 generate_image.py \
  --prompt "Character on gray background" \
  --output char.png \
  --remove-watermark \
  --transparent-bg
```

---

## Batch Generation

Generate multiple images from a file:

```bash
# prompts.txt (one per line)
python3 generate_image.py \
  --batch prompts.txt \
  --output-dir ./images/
```

---

## Error Handling

| Error | Solution |
|-------|----------|
| `GEMINI_API_KEY not set` | Run `/imagen:setup` |
| `Rate limit (429)` | Wait 60s, script auto-retries |
| `Content policy (400)` | Modify prompt |
| `No image in response` | Add more detail to prompt |
| `Pillow not installed` | Run `pip install Pillow` |

---

## Script Reference

**Location:** `scripts/generate_image.py`

| Argument | Required | Description |
|----------|----------|-------------|
| `--prompt` | Yes* | Text prompt |
| `--output` | Yes* | Output file path (.png) |
| `--model` | No | Model (default: gemini-3-pro-image-preview) |
| `--remove-watermark` | No | Remove corner watermarks |
| `--transparent-bg` | No | Make background transparent |
| `--bg-color` | No | Background hex color (default: #3a3a3a) |
| `--batch` | No | Prompts file (one per line) |
| `--output-dir` | No | Directory for batch output |

*Required unless using `--batch`

**Exit Codes:**
- 0: Success
- 1: Missing API key
- 2: Generation failed
- 3: Invalid arguments

---

## What This Plugin CAN Do

- Generate images from text prompts
- Select between fast and quality models
- Remove watermarks from images
- Make backgrounds transparent
- Batch generate multiple images

## What This Plugin CANNOT Do

- Use non-Gemini models (DALL-E, Midjourney, Stable Diffusion)
- Generate video or audio
- Bypass content policy restrictions
