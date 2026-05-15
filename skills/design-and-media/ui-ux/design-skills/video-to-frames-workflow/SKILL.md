---
name: video-to-frames-workflow
description: Converts AI-generated videos into image frame sequences for web animations. Use when the user needs to extract frames from video, create scroll animations, or convert MP4 to image sequences.
---

# Video to Frames Workflow

Convert videos into frame sequences for scroll-based web animations.

## When to use this skill
- User needs to convert video to frames
- User wants scroll-based animations from video
- User mentions EZGif or frame extraction
- User has AI-generated video for web use

## Why Convert to Frames

MP4 on scroll = laggy, choppy experience
Frame sequence on scroll = smooth, Apple-quality animations

## Workflow

### Using EZGif (Recommended)
- [ ] Go to ezgif.com/video-to-jpg
- [ ] Upload video file
- [ ] Set FPS (25-30 recommended)
- [ ] Click "Convert to JPG"
- [ ] Download frames as ZIP

### Frame Settings by Use Case

| Use Case | FPS | Est. Frames (10s video) |
|----------|-----|-------------------------|
| Smooth scroll | 30 | 300 |
| Standard scroll | 25 | 250 |
| Lightweight | 15 | 150 |

## Quick Reference

### EZGif Steps
1. Upload video (MP4, WebM, etc.)
2. Set output FPS in settings
3. Convert to JPG
4. Scroll to bottom → "Download frames as ZIP"

### Frame Organization
```bash
# Extract ZIP to project
unzip frames.zip -d ./sequence

# Rename folder for consistency
mv extracted_folder sequence
```

### Expected Output
```
sequence/
├── frame_001.jpg
├── frame_002.jpg
├── frame_003.jpg
└── ... (200-300 frames)
```

## Integration with Anti-Gravity

After extracting frames:

1. **Create project folder** on desktop
2. **Move sequence folder** into project
3. **Open in Anti-Gravity**
4. **Prompt for scroll animation**:

```
The frames for the animation are in the sequence folder. 
Build a sticky scroll component that maps scroll position to these frames.
Use Next.js. Preload frames. Map 0-100% scroll to frame 1-N.
```

## Alternative Tools

| Tool | Pros | Cons |
|------|------|------|
| EZGif | Free, fast, web-based | Limited file size |
| FFmpeg | Powerful, local | Requires CLI |
| VLC | Already installed | Manual process |

### FFmpeg Command (Alternative)
```bash
ffmpeg -i input.mp4 -vf fps=30 sequence/frame_%03d.jpg
```

## Optimization Tips

### Reduce File Size
- Use WebP instead of JPG
- Compress with quality 80-85
- Resize to max needed resolution

### Faster Loading
- Lazy load frames beyond viewport
- Use intersection observer
- Preload first 10 frames immediately

## Resources
- [EZGif Video to JPG](https://ezgif.com/video-to-jpg)
- [EZGif Video to WebP](https://ezgif.com/video-to-webp)
