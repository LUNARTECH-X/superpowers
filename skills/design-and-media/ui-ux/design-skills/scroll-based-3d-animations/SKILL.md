---
name: scroll-based-3d-animations
description: Creates Apple-style scroll-triggered 3D animations for product websites. Use when the user wants scroll-based frame animations, product exploded views, or premium interactive product pages like Apple's website.
---

# Scroll-Based 3D Animations

Build Apple-style scroll-triggered animations that reveal products through frame sequences.

## When to use this skill
- User wants Apple-style scroll animations
- User needs 3D product reveal effects
- User mentions scroll-based animations or frame sequences
- User wants interactive product pages

## Why Frames, Not Video

Video files on scroll:
- ❌ Lag and choppy playback
- ❌ Inconsistent across browsers

Frame sequences:
- ✅ Smooth scroll mapping
- ✅ Precise control
- ✅ Professional results

## Workflow

### Phase 1: Generate Keyframes (Whisk)
- [ ] Create start frame (assembled product)
- [ ] Create end frame (exploded view / final state)
- [ ] Ensure consistent style between frames

### Phase 2: Animate Transition (Veo Flow)
- [ ] Upload start frame and end frame to Google Flow
- [ ] Apply transition prompt
- [ ] Generate 8-10 second video at 30 FPS
- [ ] Download upscaled version

### Phase 3: Extract Frames (EZGif)
- [ ] Upload video to EZGif
- [ ] Set FPS to 25-30
- [ ] Convert to JPG
- [ ] Download frames as ZIP (expect ~240 frames)

### Phase 4: Build Scroll Animation (Anti-Gravity)
- [ ] Create project folder
- [ ] Add frames folder to public directory
- [ ] Apply scroll animation prompt
- [ ] Run npm install & npm run dev

## Key Prompts

### Google Flow Transition Prompt
```
Smoothly transition from the assembled product to exploded view. Slow motion professional internal tech showcase. Apple style animation. High quality professional 3D explosion. Show slow and professional disassembly of the parts before showing exploded view.
```

### Cinematic Assembly (Reverse Animation)
```
Cinematic assembly. Start with a clean high quality vibrant gradient background. Smoothly, a dynamic vortex appears. Professional camera movement. Parts assemble smoothly into final product.
```

### Anti-Gravity Website Prompt
```
Create a scroll-based frame animation website. Use the frames in the /sequence folder (or /public/sequence). Build a sticky scroll component that maps the user's scroll position to these image frames. As the user scrolls, progress through frames sequentially. Use Next.js with React. Ensure:
- Frames are preloaded for smooth playback
- Scroll position maps 0-100% to frame 1-N
- Section is sticky (100vh height)
- No lag or jitter during scroll
- Mobile responsive
```

## Technical Specifications

### Optimal Frame Settings
| Setting | Value |
|---------|-------|
| FPS | 25-30 |
| Resolution | 1080p |
| Total Frames | 200-250 |
| Video Duration | 8-10 seconds |

### Frame Naming Convention
```
frame_001.jpg
frame_002.jpg
...
frame_240.jpg
```

## Project Structure
```
project/
├── public/
│   └── sequence/
│       ├── frame_001.jpg
│       ├── frame_002.jpg
│       └── ...
├── src/
│   └── components/
│       └── ScrollAnimation.jsx
└── package.json
```

## Terminal Commands
```bash
# After AI generates code
cd project-name
npm install
npm run dev
```

## Common Issues & Fixes

### Choppy Animation
- Increase frame count (extract at higher FPS)
- Preload all frames before scroll interaction

### Frame Loading Lag
- Use webp format instead of jpg
- Compress frames with quality optimization

### Scroll Jitter
- Implement requestAnimationFrame
- Use will-change CSS property

## Resources
- [Google Whisk](https://labs.google.com/whisk) - Keyframe generation
- [Google Veo Flow](https://labs.google.com/flow) - Frame-to-frame animation
- [EZGif](https://ezgif.com/video-to-jpg) - Video to frames
- [FreePik AI](https://freepik.com) - Alternative video generation
