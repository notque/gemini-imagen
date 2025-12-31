<p align="center">
  <img src="assets/logo.png" alt="Gemini Imagen" width="200">
</p>

# Gemini Imagen

A Claude Code plugin that adds AI image generation using Google Gemini's image generation APIs.

## What This Does

Install this plugin to give Claude Code the ability to generate images. Just ask Claude to create an image and it will use the Gemini API to generate it.

**Example:**
```
> Generate an image of a mountain landscape at sunset
```

Claude will run the generation script and save the image for you.

## Features

- **Text-to-image generation** using Gemini's latest models
- **Watermark removal** - automatically clean up generated images
- **Background transparency** - perfect for sprites and icons
- **Batch generation** - generate multiple images from a prompts file
- **Fast and quality modes** - choose speed or quality

## Installation

### Option 1: Plugin Marketplace (Recommended)

```bash
# Add this repository as a plugin marketplace
/plugin marketplace add notque/gemini-imagen

# Install the plugin
/plugin install gemini-imagen@notque-gemini-imagen
```

### Option 2: Direct Clone

```bash
git clone https://github.com/notque/gemini-imagen.git ~/.claude/plugins/gemini-imagen
```

## Setup

### Step 1: Get Your Gemini API Key

1. Visit [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Sign in with your Google account
3. Click "Create API Key"
4. Copy the key

### Step 2: Set the Environment Variable

**macOS / Linux:**
```bash
echo 'export GEMINI_API_KEY="your_key_here"' >> ~/.zshrc && source ~/.zshrc
```

**Windows PowerShell:**
```powershell
[Environment]::SetEnvironmentVariable("GEMINI_API_KEY", "your_key_here", "User")
```

### Step 3: Install Python Dependencies

```bash
pip install google-genai Pillow
```

## Usage

Once installed, just ask Claude to generate images:

```
Generate an image of a cute cartoon cat
Create a pixel art sprite of a knight
Make a product photo of a smartphone
```

Or use the commands directly:

| Command | Description |
|---------|-------------|
| `/imagen` | Generate an image |
| `/imagen:setup` | Setup guide for API key |
| `/imagen:help` | Quick reference |

## Post-Processing

### Watermark Removal

```bash
python3 generate_image.py --prompt "..." --output out.png --remove-watermark
```

Removes bright pixels from corners that may contain watermarks.

### Background Transparency

```bash
python3 generate_image.py --prompt "Character on gray background" --output char.png --transparent-bg
```

Converts solid backgrounds to transparent - great for game sprites.

## Models

| Model | Speed | Best For |
|-------|-------|----------|
| `gemini-2.5-flash-image` | Fast (2-5s) | Iterations, drafts |
| `gemini-3-pro-image-preview` | Slower | Quality, text rendering |

## Plugin Structure

```
gemini-imagen/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   ├── setup.md
│   └── help.md
├── skills/
│   └── gemini-imagen/
│       ├── SKILL.md
│       └── scripts/
│           └── generate_image.py
├── assets/
│   └── logo.png
├── examples/
│   └── .env.example
├── README.md
└── LICENSE
```

## Requirements

- Python 3.8+
- `google-genai` package
- `Pillow` package (for post-processing)
- Gemini API key

## License

MIT
