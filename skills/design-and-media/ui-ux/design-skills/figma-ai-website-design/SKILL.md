---
name: figma-ai-website-design
description: Creates websites using Figma Make with Gemini 3 Pro. Use when the user wants to build AI-generated websites, landing pages, or needs to quickly prototype web designs using Figma's AI capabilities.
---

# Figma AI Website Design

Build production-quality websites using Figma Make without manual coding.

## When to use this skill
- User wants to create a website using AI
- User needs to prototype a landing page quickly
- User wants to leverage design inspiration from Figma Community
- User mentions Figma Make or Gemini 3 Pro

## Prerequisites

1. **Enable Gemini 3 Pro** in Figma:
   - Settings → General → Experimental Model → Select "Gemini 3 Pro"

## Workflow

### Phase 1: Gather Inspiration
- [ ] Go to Figma Community and search for design styles (e.g., "Apple", "Linear", "Nike")
- [ ] Duplicate a design that matches desired aesthetic
- [ ] Remove unnecessary elements (logos, graphics) to speed up transfer
- [ ] Copy the cleaned design

### Phase 2: Build with Figma Make
- [ ] Open Figma Make (Recent → Make)
- [ ] Paste the inspiration design
- [ ] Prompt: `build out this UI exactly`
- [ ] Review output for animations and mobile responsiveness

### Phase 3: Add Animated Elements
- [ ] Add video backgrounds from Design Rocket or Cloudflare hosting
- [ ] Use 21st.dev for pre-built animated components (navbars, logos)
- [ ] Prompt: `add a video under text and make sure it is stretching from side to side`

### Phase 4: Add Component Libraries
Use 21st.dev for animated components:

```
Navigation Menu:
- Search "navigation menu" on 21st.dev
- Copy the prompt for desired style
- Paste in Figma: "add this navbar"

Logo Section:
- Search "logos" on 21st.dev
- Copy prompt for animated logo marquee
- Paste in Figma: "add this logo section below video"
```

## Key Prompts

### Hero Section with Background
```
add a video under text and make sure it is stretching from side to side
```

### Animated Components
```
add this navbar [paste 21st.dev prompt]
below add this logo section [paste 21st.dev prompt]
add this to the background of hero [paste video URL]
```

### Get AI-Generated Prompt
```
give me a prompt to build out this site with all of the details to have exact design like we have
```

## Video Background Sources
- **Design Rocket**: Pre-hosted video backgrounds ready to use
- **Cloudflare**: Host custom videos for Figma Make
- **Minimax/Hailuo AI**: Generate custom animated backgrounds

## Animated Background Prompt (for AI video generators)
```
animate this make it spin make the spinning noticeable do not change the position make it looped
```

## Resources
- [Figma Community](https://figma.com/community)
- [21st.dev](https://21st.dev) - Animated components
- [Design Rocket](https://designrocket.io) - Video backgrounds
