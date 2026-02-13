# Nano Banana Pro

Generate or edit images using Google's Gemini 3 Pro Image API (Nano Banana Pro).

## Features

- **Text-to-Image Generation**: Create images from text descriptions
- **Image Editing**: Modify existing images with natural language instructions
- **Multi-Image Composition**: Combine up to 14 images into a single scene
- **Flexible Resolutions**: Support for 1K, 2K, and 4K output

## Requirements

- `uv` package manager (install via Homebrew: `brew install uv`)
- API Key (one of):
  - `AI_GATEWAY_API_KEY` (recommended - uses Anthropic AI Gateway)
  - `GEMINI_API_KEY` (direct Google Gemini API access)

## Usage

### Generate a new image

```bash
uv run ~/.claude/skills/nano-banana-pro/scripts/generate_image.py \
  --prompt "a serene mountain landscape at sunset" \
  --filename "sunset-mountains.png" \
  --resolution 2K
```

### Edit an existing image

```bash
uv run ~/.claude/skills/nano-banana-pro/scripts/generate_image.py \
  --prompt "add northern lights to the sky" \
  --filename "edited-mountains.png" \
  --input-image sunset-mountains.png \
  --resolution 2K
```

### Combine multiple images

```bash
uv run ~/.claude/skills/nano-banana-pro/scripts/generate_image.py \
  --prompt "create a collage of these vacation photos" \
  --filename "vacation-collage.png" \
  -i photo1.png -i photo2.png -i photo3.png
```

## Configuration

The skill supports multiple API key sources, checked in priority order:

### Option 1: AI Gateway (Recommended)
```bash
export AI_GATEWAY_API_KEY="your-ai-gateway-key"
```

This routes requests through Anthropic's AI Gateway for unified management and cost efficiency.

### Option 2: Direct Gemini API
```bash
export GEMINI_API_KEY="your-gemini-api-key"
```

### Option 3: OpenClaw Config File
Configure in `~/.openclaw/openclaw.json`:

```json
{
  "skills": {
    "nano-banana-pro": {
      "apiKey": "your-api-key-here"
    }
  }
}
```

## Installation

```bash
# Install to Claude Code skills directory
mkdir -p ~/.claude/skills
cp -r nano-banana-pro ~/.claude/skills/
```

## Notes

- Supported resolutions: `1K` (default), `2K`, `4K`
- Use timestamp-based filenames for organization: `2026-02-04-14-30-00-description.png`
- The script automatically handles image format conversion to PNG
- On supported platforms, generated images are automatically attached to the chat

## Original Source

[openclaw/openclaw](https://github.com/openclaw/openclaw/tree/main/skills/nano-banana-pro)
