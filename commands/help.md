---
description: Quick reference for Gemini image generation
---

# Gemini Imagen Help

## Commands

| Command | Description |
|---------|-------------|
| `/imagen` | Generate an image |
| `/imagen:setup` | Setup API key |
| `/imagen:help` | This help |

## Models

| Model | Speed | Use For |
|-------|-------|---------|
| `gemini-2.5-flash-image` | 2-5s | Drafts, iterations |
| `gemini-3-pro-image-preview` | 5-15s | Quality, text |

## Quick Generate

```bash
python3 ~/.claude/plugins/gemini-imagen/skills/gemini-imagen/scripts/generate_image.py \
  --prompt "A cute cartoon cat" \
  --output cat.png
```

## Options

| Flag | Description |
|------|-------------|
| `--prompt` | Text prompt |
| `--output` | Output file (.png) |
| `--model` | Model selection |
| `--remove-watermark` | Clean corner watermarks |
| `--transparent-bg` | Transparent background |
| `--batch` | Prompts file |

## Troubleshooting

| Error | Fix |
|-------|-----|
| API key missing | `/imagen:setup` |
| Rate limited | Wait 60s |
| No Pillow | `pip install Pillow` |
