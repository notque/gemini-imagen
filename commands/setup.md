---
description: Set up Gemini API credentials for image generation
---

# Gemini Imagen Setup

## Step 1: Get Your API Key

1. Go to [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Sign in with Google
3. Click "Create API Key"
4. Copy the key

## Step 2: Set Environment Variable

**macOS / Linux (zsh):**
```bash
echo 'export GEMINI_API_KEY="your_key_here"' >> ~/.zshrc && source ~/.zshrc
```

**macOS / Linux (bash):**
```bash
echo 'export GEMINI_API_KEY="your_key_here"' >> ~/.bashrc && source ~/.bashrc
```

**Windows PowerShell:**
```powershell
[Environment]::SetEnvironmentVariable("GEMINI_API_KEY", "your_key_here", "User")
# Restart terminal
```

**Windows CMD:**
```cmd
setx GEMINI_API_KEY "your_key_here"
:: Restart terminal
```

## Step 3: Install Dependencies

```bash
pip install google-genai Pillow
```

## Step 4: Verify

```bash
echo "GEMINI_API_KEY is ${GEMINI_API_KEY:+set}"
```

Should output: `GEMINI_API_KEY is set`

## Troubleshooting

**Key not found after setting:**
- Restart your terminal
- Check the correct shell config file (.zshrc vs .bashrc)

**Invalid API key error:**
- Verify the key was copied correctly (no extra spaces)
- Ensure the key is for Gemini API (not Vertex AI)

**pip install fails:**
- Try `pip3 install google-genai Pillow`
- Or use `python3 -m pip install google-genai Pillow`
