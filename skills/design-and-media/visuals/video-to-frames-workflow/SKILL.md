---
name: Video to Frames Workflow
description: Extract and process video frames for scroll-animations, sprites, and AI training
---

# Video to Frames Workflow

Extract frames from videos using FFmpeg for use in scroll-triggered animations, sprite sheets, image sequences, and AI/ML training datasets.

## Overview

Converting video to frames enables:
- Scroll-driven video playback (canvas-based)
- Sprite sheet generation for game/web animations
- Training data extraction for ML models
- Thumbnail generation and video analysis
- Stop-motion style web animations

## Prerequisites

```bash
# Install FFmpeg
# Windows (chocolatey)
choco install ffmpeg

# macOS
brew install ffmpeg

# Linux
sudo apt install ffmpeg

# Verify installation
ffmpeg -version
```

## Basic Frame Extraction

### Extract All Frames

```bash
# Extract every frame as PNG
ffmpeg -i input.mp4 -q:v 2 frames/frame_%04d.png

# Extract every frame as JPG (smaller files)
ffmpeg -i input.mp4 -q:v 2 frames/frame_%04d.jpg
```

### Extract at Specific FPS

```bash
# Extract 1 frame per second
ffmpeg -i input.mp4 -vf fps=1 frames/frame_%04d.png

# Extract 10 frames per second
ffmpeg -i input.mp4 -vf fps=10 frames/frame_%04d.png

# Extract 24 frames per second (cinematic)
ffmpeg -i input.mp4 -vf fps=24 frames/frame_%04d.png
```

### Extract Specific Frame Range

```bash
# Extract frames from 10s to 20s at 30fps
ffmpeg -i input.mp4 -ss 00:00:10 -to 00:00:20 -vf fps=30 frames/frame_%04d.png

# Extract first 100 frames only
ffmpeg -i input.mp4 -vframes 100 frames/frame_%04d.png
```

## Optimization for Web

### Resize During Extraction

```bash
# Scale to specific width (maintain aspect ratio)
ffmpeg -i input.mp4 -vf "fps=24,scale=1280:-1" frames/frame_%04d.jpg

# Scale to specific dimensions
ffmpeg -i input.mp4 -vf "fps=24,scale=1920:1080" frames/frame_%04d.jpg

# Scale to max dimension (fit within bounds)
ffmpeg -i input.mp4 -vf "fps=24,scale='min(1280,iw)':'min(720,ih)':force_original_aspect_ratio=decrease" frames/frame_%04d.jpg
```

### Optimize Quality & Size

```bash
# High quality JPG (2-5, lower = better quality)
ffmpeg -i input.mp4 -vf fps=24 -q:v 2 frames/frame_%04d.jpg

# Medium quality (good balance)
ffmpeg -i input.mp4 -vf fps=24 -q:v 5 frames/frame_%04d.jpg

# WebP format (best compression)
ffmpeg -i input.mp4 -vf fps=24 frames/frame_%04d.webp
```

## Scroll Animation Workflow

### 1. Extract Frames

```bash
# For a 10-second video, extract 120 frames (12fps)
ffmpeg -i product_rotation.mp4 -vf "fps=12,scale=1280:-1" -q:v 3 frames/frame_%04d.jpg
```

### 2. Generate Frame Manifest

```bash
# Create JSON manifest of frames
ls frames/ | node -e "
const fs = require('fs');
const frames = [];
require('readline').createInterface({
  input: process.stdin
}).on('line', (line) => {
  frames.push('/frames/' + line);
}).on('close', () => {
  fs.writeFileSync('frames.json', JSON.stringify(frames, null, 2));
});
"
```

### 3. Implement Scroll-Driven Playback

```javascript
// Load frames and bind to scroll
const frames = await fetch('/frames.json').then(r => r.json())
const images = await Promise.all(frames.map(src => {
  return new Promise(resolve => {
    const img = new Image()
    img.onload = () => resolve(img)
    img.src = src
  })
}))

const canvas = document.getElementById('video-canvas')
const ctx = canvas.getContext('2d')

window.addEventListener('scroll', () => {
  const scrollPercent = window.scrollY / (document.body.scrollHeight - window.innerHeight)
  const frameIndex = Math.floor(scrollPercent * (images.length - 1))
  ctx.drawImage(images[frameIndex], 0, 0)
})
```

## Sprite Sheet Generation

```bash
# Create sprite sheet from frames
ffmpeg -i input.mp4 -vf "fps=10,scale=200:-1,tile=10x10" spritesheet.png

# Vertical strip for scroll animations
ffmpeg -i input.mp4 -vf "fps=30,scale=400:-1,tile=1x90" vertical_strip.png
```

## Batch Processing Script

```bash
#!/bin/bash
# process_video.sh - Complete workflow

INPUT=$1
OUTPUT_DIR=${2:-"frames"}
FPS=${3:-24}
WIDTH=${4:-1280}

mkdir -p "$OUTPUT_DIR"

echo "Extracting frames at ${FPS}fps..."
ffmpeg -i "$INPUT" \
  -vf "fps=$FPS,scale=$WIDTH:-1" \
  -q:v 3 \
  "$OUTPUT_DIR/frame_%04d.jpg"

echo "Creating manifest..."
ls "$OUTPUT_DIR"/*.jpg | sed 's|^|/|' > "$OUTPUT_DIR/manifest.txt"

echo "Done! Extracted $(ls "$OUTPUT_DIR"/*.jpg | wc -l) frames"
```

## Common Use Cases

### Product 360° View
```bash
# 360° turntable video → scroll-driven rotation
ffmpeg -i turntable.mp4 -vf "fps=36,scale=800:-1" -q:v 2 frames/frame_%03d.jpg
# Result: 36 frames = 10° per frame
```

### Scroll Animation (Apple-style)
```bash
# Cinematic reveal video → scroll-bound playback
ffmpeg -i reveal.mp4 -vf "fps=24,scale=1920:-1" -q:v 2 frames/frame_%04d.webp
# Preload all frames, swap on scroll
```

### Training Data Extraction
```bash
# Extract diverse frames for ML training
ffmpeg -i video.mp4 -vf "fps=1,scale=512:512" -q:v 2 training/sample_%04d.jpg
```

## Performance Tips

1. **Preload frames** before scroll interaction begins
2. **Use WebP** format for 25-35% smaller files
3. **Implement lazy loading** for long sequences
4. **Consider progressive JPEG** for faster initial display
5. **Cache frames** in memory after first load

## Quality Checklist

- [ ] Frame count appropriate for animation smoothness
- [ ] Resolution optimized for target display
- [ ] File sizes reasonable for web delivery
- [ ] Naming convention consistent (zero-padded)
- [ ] All frames extracted without corruption

## Resources

- [FFmpeg Documentation](https://ffmpeg.org/documentation.html)
- [FFmpeg Filters](https://ffmpeg.org/ffmpeg-filters.html)
- [WebP Encoding Guide](https://developers.google.com/speed/webp)
