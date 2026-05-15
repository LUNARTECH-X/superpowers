---
name: whisk-product-visuals
description: Generates premium product visuals and animations using Google Whisk. Use when the user needs 3D product renders, exploded view animations, product shots for landing pages, or Apple-style product photography.
---

# Whisk Product Visuals

Create premium product renders and animations using Google Whisk's Subject-Scene-Style framework.

## When to use this skill
- User needs product photography for a website
- User wants 3D product renders
- User needs exploded view animations
- User mentions Google Whisk or product visuals

## Prerequisites

Access Google Whisk at [labs.google.com/whisk](https://labs.google.com/whisk)

## Core Concepts

### Subject-Scene-Style Framework
1. **Subject**: The main product/object (upload or generate)
2. **Scene**: Environment/backdrop context
3. **Style**: Aesthetic treatment/visual vibe

## Workflow

### Phase 1: Create Subject
- [ ] Upload product photo OR generate with text prompt
- [ ] Use Nano Banana model for image generation

### Phase 2: Define Scene
- [ ] Create or upload backdrop environment
- [ ] Prompt for gradient/studio backgrounds

### Phase 3: Apply Style
- [ ] Select aesthetic treatment
- [ ] Combine all three for final composition

### Phase 4: Generate & Animate
- [ ] Generate final product shot
- [ ] Click "Animate" for motion
- [ ] Download as video or static image

## Key Prompts

### Premium Product Shot (Horizontal - Hero Section)
```
[product name] in horizontal orientation. It should look premium and high-end product shot. Ultra-realistic 3D rendering, professional studio lighting with soft shadows, isolated on a clean gradient background, cinematic product photography
```

### Premium Product Shot (Centered)
```
The bottle or the product needs to be in the center of the image. Ultra-realistic 3D rendering, professional studio lighting with soft shadows, isolated on a clean gradient background
```

### Exploded View
```
Show the internal components of [product] floating in the air. Professional tech showcase, Apple-style product breakdown, each component clearly visible and separated, 3D explosion effect
```

### Blank Background (for animation start frame)
```
remove all the elements from the image only keep the background
```

### Animation Prompt
```
create me a smooth 360-degree rotating animation
```

## Use Cases

### Hero Section Product Shot
1. Upload product image as subject
2. Use "horizontal orientation" prompt
3. Generate premium render
4. Animate if needed for video background

### Exploded View Animation
1. Generate assembled product shot (Frame 1)
2. Generate exploded view (Frame 2)
3. Use Google Flow to animate between frames
4. Convert to frames for scroll animation

### Multi-Flavor Products
Generate variations by changing prompts:
```
Dutch Chocolate flavor product shot...
Ruby Pomegranate flavor product shot...
```

## Output Formats
- **Static Image**: Download for hero sections
- **Animated Video**: Use for backgrounds or convert to frames
- **Frame Sequence**: Export via EZGif for scroll animations

## Resources
- [Google Whisk](https://labs.google.com/whisk)
- [Google Veo Flow](https://labs.google.com/flow) - For transitions
