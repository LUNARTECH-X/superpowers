---
name: Glassmorphism Design
description: Create frosted glass UI effects with blur, transparency, and subtle borders
---

# Glassmorphism Design

Implement the popular glassmorphism aesthetic with frosted glass effects, backdrop blur, transparent backgrounds, and subtle borders for premium, modern interfaces.

## Overview

Glassmorphism creates a sense of depth through:
- **Backdrop blur** — frosted glass effect
- **Transparency** — semi-transparent backgrounds
- **Subtle borders** — light borders for definition
- **Layered depth** — cards appear to float

## Core Implementation

### Basic Glass Card

```html
<div class="relative rounded-2xl border border-white/10 bg-white/5 backdrop-blur-md">
  <div class="p-6">
    <h3 class="text-white font-medium">Glass Card</h3>
    <p class="text-white/70">Content with frosted effect</p>
  </div>
</div>
```

### CSS Properties Breakdown

```css
.glass-card {
  /* Frosted glass blur */
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  
  /* Semi-transparent background */
  background: rgba(255, 255, 255, 0.05);
  
  /* Subtle border for definition */
  border: 1px solid rgba(255, 255, 255, 0.1);
  
  /* Smooth corners */
  border-radius: 1rem;
}
```

## Tailwind Utility Classes

| Effect | Class | Value |
|--------|-------|-------|
| Light blur | `backdrop-blur-sm` | 4px |
| Medium blur | `backdrop-blur-md` | 12px |
| Heavy blur | `backdrop-blur-xl` | 24px |
| Transparent bg (dark) | `bg-white/5` | 5% white |
| Transparent bg (light) | `bg-black/5` | 5% black |
| Subtle border | `border-white/10` | 10% white |

## Dark Theme Glass

### Standard Dark Glass

```html
<div class="rounded-2xl border border-white/10 bg-neutral-900/50 backdrop-blur-md">
  <!-- Content -->
</div>
```

### Premium Dark Glass with Glow

```html
<div class="group relative">
  <!-- Outer glow -->
  <div class="absolute -inset-4 bg-gradient-to-r from-brand-500/20 via-purple-500/20 to-brand-500/20 
              rounded-[2rem] blur-2xl opacity-50"></div>
  
  <!-- Glass card -->
  <div class="relative rounded-[1.5rem] overflow-hidden border border-white/10 
              bg-gradient-to-br from-zinc-900 via-zinc-900 to-zinc-950 p-6">
    <!-- Content -->
  </div>
</div>
```

### Elevated Dark Glass

```html
<div class="rounded-2xl border border-white/10 bg-neutral-900/50 backdrop-blur-md
            hover:bg-neutral-800/50 hover:border-white/20 
            hover:shadow-2xl hover:shadow-violet-500/10
            transition-all duration-500">
  <!-- Content -->
</div>
```

## Light Theme Glass

### Clean Light Glass

```html
<div class="rounded-2xl border border-zinc-200/50 bg-white/70 backdrop-blur-md shadow-sm">
  <!-- Content -->
</div>
```

### Elevated Light Glass

```html
<div class="rounded-2xl border border-zinc-100 bg-white/80 backdrop-blur-lg
            shadow-[0_8px_32px_rgba(0,0,0,0.08)]
            hover:bg-white/90 hover:shadow-lg
            transition-all duration-300">
  <!-- Content -->
</div>
```

## Glass Navigation

### Floating Glass Navbar

```html
<nav class="fixed top-4 left-1/2 -translate-x-1/2 z-50 
            rounded-full border border-white/10 bg-black/20 backdrop-blur-xl 
            px-6 py-3">
  <div class="flex items-center gap-6">
    <a href="#" class="text-white/80 hover:text-white transition-colors">Home</a>
    <a href="#" class="text-white/80 hover:text-white transition-colors">About</a>
    <a href="#" class="text-white/80 hover:text-white transition-colors">Contact</a>
  </div>
</nav>
```

### Glass Sidebar

```html
<aside class="fixed left-0 top-0 h-full w-64 
              border-r border-white/10 bg-neutral-950/80 backdrop-blur-xl">
  <!-- Sidebar content -->
</aside>
```

## Glass Badges & Pills

### Status Badge

```html
<span class="inline-flex items-center gap-1.5 rounded-full 
             border border-brand-500/30 bg-brand-500/15 
             px-2.5 py-0.5 text-[11px] font-medium text-brand-300">
  <span class="w-1.5 h-1.5 rounded-full bg-brand-400 animate-pulse"></span>
  ACTIVE
</span>
```

### Tag Pills

```html
<div class="flex gap-2">
  <span class="px-2 py-1 rounded-full bg-emerald-50/10 border border-emerald-500/20 
               text-[8px] font-bold text-emerald-400">HIPAA</span>
  <span class="px-2 py-1 rounded-full bg-blue-50/10 border border-blue-500/20 
               text-[8px] font-bold text-blue-400">GDPR</span>
</div>
```

## Glass Modals & Dialogs

```html
<!-- Backdrop -->
<div class="fixed inset-0 bg-black/50 backdrop-blur-sm z-40"></div>

<!-- Modal -->
<div class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 z-50
            w-full max-w-md rounded-2xl border border-white/10 
            bg-neutral-900/90 backdrop-blur-xl p-6
            shadow-2xl shadow-black/50">
  <h2 class="text-white text-xl font-medium mb-4">Modal Title</h2>
  <p class="text-white/70">Modal content here.</p>
</div>
```

## Background Effects for Glass

### Animated Gradient Blobs

```html
<div class="relative overflow-hidden">
  <!-- Background blobs -->
  <div class="absolute inset-0 pointer-events-none">
    <div class="absolute top-1/4 left-1/4 w-96 h-96 
                bg-brand-500/10 rounded-full blur-[120px] animate-pulse"></div>
    <div class="absolute bottom-1/4 right-1/4 w-96 h-96 
                bg-purple-500/10 rounded-full blur-[120px] animate-pulse"
         style="animation-delay: 2s;"></div>
  </div>
  
  <!-- Glass content -->
  <div class="relative z-10">
    <!-- Your glass cards here -->
  </div>
</div>
```

### Dot Grid Pattern

```html
<div class="absolute inset-0 opacity-[0.03]">
  <div class="absolute inset-0" 
       style="background-image: radial-gradient(circle at 1px 1px, white 1px, transparent 0); 
              background-size: 40px 40px;">
  </div>
</div>
```

## Hover States

### Glow on Hover

```html
<div class="group rounded-2xl border border-white/10 bg-neutral-900/50 backdrop-blur-md
            hover:shadow-2xl hover:shadow-violet-500/10
            transition-all duration-500">
  <!-- Content -->
</div>
```

### Border Brightness on Hover

```html
<div class="rounded-2xl border border-white/10 bg-white/5 backdrop-blur-md
            hover:border-white/20 hover:bg-white/10
            transition-all duration-300">
  <!-- Content -->
</div>
```

## Accessibility Considerations

1. **Contrast**: Ensure text has sufficient contrast against transparent backgrounds
2. **Readability**: Increase blur for better text legibility
3. **Focus States**: Add visible focus rings for keyboard navigation
4. **Reduced Motion**: Respect `prefers-reduced-motion` for animations

```css
@media (prefers-reduced-motion: reduce) {
  .glass-card {
    animation: none;
    transition: none;
  }
}
```

## Browser Support

```css
/* Fallback for browsers without backdrop-blur support */
@supports not (backdrop-filter: blur(12px)) {
  .glass-card {
    background: rgba(0, 0, 0, 0.8); /* Solid fallback */
  }
}
```

## Common Mistakes to Avoid

1. ❌ Too much transparency — content becomes unreadable
2. ❌ Missing borders — cards lack definition
3. ❌ Excessive blur — performance issues
4. ❌ No fallback — broken on older browsers
5. ❌ Pure white/black backgrounds — breaks glass illusion

## Best Practices

1. ✅ Use blur between 8-24px for best effect
2. ✅ Keep background opacity between 5-30%
3. ✅ Add subtle borders (10-20% opacity)
4. ✅ Layer glass over interesting backgrounds
5. ✅ Test on various backgrounds for readability

## Resources

- [Glassmorphism CSS Generator](https://hype4.academy/tools/glassmorphism-generator)
- [MDN: backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter)
