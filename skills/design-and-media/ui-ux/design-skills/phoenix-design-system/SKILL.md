---
name: phoenix-design-system
description: Creates premium AI SaaS landing pages following the Phoenix design system. Use when the user wants to build dark-themed tech websites, AI product pages, glassmorphism designs, or modern SaaS landing pages with gradient aesthetics.
---

# Phoenix Design System

Build premium AI SaaS landing pages with the Phoenix design aesthetic - a dark, futuristic look with vibrant gradients and glassmorphism.

## When to use this skill
- User wants a dark-themed AI/tech landing page
- User needs a premium SaaS website design
- User mentions Phoenix-style, glassmorphism, or gradient aesthetics
- User wants to create an AI product showcase

## Design DNA

### Core Aesthetic
- **Dark Mode**: Pure black (#000000) or near-black backgrounds
- **Accent Colors**: Vibrant purple/blue/pink gradients (glowing effect)
- **Typography**: Clean sans-serif (Inter family recommended)
- **Visual Motif**: Flowing ribbon/aurora gradients as connecting element

### Color Palette
```css
:root {
  /* Backgrounds */
  --bg-primary: #000000;
  --bg-secondary: #0a0a0a;
  --bg-card: rgba(15, 15, 15, 0.8);
  
  /* Text */
  --text-primary: #ffffff;
  --text-secondary: #a1a1aa;
  --text-muted: #71717a;
  
  /* Accents */
  --accent-purple: #a855f7;
  --accent-pink: #ec4899;
  --accent-blue: #3b82f6;
  --accent-cyan: #06b6d4;
  
  /* Gradients */
  --gradient-aurora: linear-gradient(135deg, #a855f7, #ec4899, #3b82f6);
  --gradient-glow: radial-gradient(circle, rgba(168,85,247,0.3), transparent);
}
```

## Page Structure

### 1. Navigation (Sticky)
```
[Logo] [Home] [About] [Features] [Pricing] [Use Cases] [Blog] [Contact]  [Login] [Get Started]
```
- Transparent background, becomes solid on scroll
- CTA button with white fill, black text
- Login as text link

### 2. Hero Section
- **Headline**: Large, bold, benefit-driven
- **Subheadline**: Supporting value proposition (1-2 lines)
- **Dual CTAs**: Primary (filled) + Secondary (outline)
- **Visual**: 3D product mockup or animated gradient
- **Product Preview**: Dashboard/app screenshot with subtle glow

Example:
```
Supercharge Your Productivity with AI

Over 200+ Next-Gen AI Assistants and Coaches to boost
your creativity and productivity – work smarter, not harder.

[Get started] [View pricing]
```

### 3. Trust Badges / Logos
- Major brand logos (NVIDIA, Microsoft, Google, OpenAI)
- Media mentions (Forbes, Bloomberg, Entrepreneur)
- White/gray logos on dark background
- Animated marquee effect (optional)

### 4. How It Works Section
```
Learn how [Product] works
Ready to reclaim your time? Here's the rundown.
```
- Step cards with icons
- Video embed or animated demo
- Clear numbered steps

### 5. Benefits/Features Section
- **Aspirational Headlines**: "Skyrocket Your Career", "Lead Your Market"
- **Icon-rich cards**: Tool name + brief description
- **Categorized grids**: Group by use case (Career, Business, Content)
- **Persona-based messaging**: Speak to specific user needs

### 6. Product Cards / Chat UI
- Glassmorphism effect: `backdrop-filter: blur(10px)`
- Chat interface mockups showing AI in action
- Highlighted keywords with accent colors
- Sentiment/reaction tags at bottom

### 7. Testimonials
- Quote from authority sources (Forbes, Entrepreneur)
- Company logos as attribution
- High-contrast white text on dark

### 8. Pricing Section
```
Choose your plan
```
- 3-tier layout (Free, Monthly, Annual)
- Highlight recommended plan
- Feature comparison list
- Clear CTAs per tier

### 9. Footer
- Multi-column layout
- Newsletter signup
- Social icons (LinkedIn, Twitter, YouTube)
- Legal links

## Visual Effects

### Glassmorphism Cards
```css
.glass-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
}
```

### Glowing Accent
```css
.glow {
  box-shadow: 0 0 40px rgba(168, 85, 247, 0.3);
}
```

### Aurora/Ribbon Background
- 3D-rendered flowing ribbon in purple/pink/blue
- Use as hero visual or section separator
- Can be static image or animated video

### Button Styles
```css
.btn-primary {
  background: #ffffff;
  color: #000000;
  border-radius: 9999px;
  padding: 12px 24px;
  font-weight: 500;
}

.btn-secondary {
  background: transparent;
  color: #ffffff;
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 9999px;
}
```

## Typography Scale

| Element | Size | Weight |
|---------|------|--------|
| H1 (Hero) | 48-64px | 600-700 |
| H2 (Section) | 36-42px | 600 |
| H3 (Card) | 20-24px | 600 |
| Body | 16-18px | 400 |
| Small | 14px | 400 |

## Responsive Breakpoints
```css
/* Mobile first */
@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
```

## Copy Principles

### Headlines
- **Aspirational**: "Skyrocket Your Career"
- **Benefit-focused**: "Boost Your Productivity"
- **Challenge status quo**: "The old ways don't work anymore"

### Body Copy
- Empathize with pain points first
- Position product as the solution
- Use "you" and "your" frequently
- Keep paragraphs short (2-3 sentences)

## Implementation Checklist

- [ ] Dark background (#000 or near-black)
- [ ] Gradient aurora visual element
- [ ] Glassmorphism cards
- [ ] Trust badges below hero
- [ ] Benefit-driven headlines
- [ ] Dual CTA buttons (filled + outline)
- [ ] Icon-based feature grids
- [ ] Chat UI mockups showing product
- [ ] 3-tier pricing layout
- [ ] Social proof (logos + quotes)

## Resources
- [Inter Font Family](https://fonts.google.com/specimen/Inter)
- [Figma Community](https://figma.com/community) - Dark UI templates
- [Google Whisk](https://labs.google.com/whisk) - Generate aurora visuals
