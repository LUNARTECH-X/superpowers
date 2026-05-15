---
name: Micro-Interactions
description: Add subtle animations and hover effects that make interfaces feel alive and responsive
---

# Micro-Interactions

Implement subtle, purposeful animations that provide feedback, guide attention, and create delightful user experiences without overwhelming the interface.

## Overview

Micro-interactions are small, focused animations that:
- Provide **feedback** on user actions
- Guide **attention** to important elements
- Create **delight** through polish
- Communicate **state changes**

## Core Animation Properties

### Tailwind Transition Classes

```html
<!-- Duration -->
<div class="transition duration-300">300ms</div>
<div class="transition duration-500">500ms (recommended)</div>
<div class="transition duration-700">700ms (dramatic)</div>

<!-- Easing -->
<div class="transition ease-out">Decelerate (exiting)</div>
<div class="transition ease-in-out">Smooth both ways</div>

<!-- Properties -->
<div class="transition-all">All properties</div>
<div class="transition-transform">Transform only</div>
<div class="transition-colors">Colors only</div>
<div class="transition-opacity">Opacity only</div>
```

## Hover State Patterns

### Card Lift

```html
<div class="rounded-2xl bg-white shadow-md
            hover:-translate-y-1 hover:shadow-lg
            transition-all duration-300">
  <!-- Card content -->
</div>
```

### Image Scale

```html
<div class="group overflow-hidden rounded-xl">
  <img src="image.jpg" 
       class="w-full transition-transform duration-500 
              group-hover:scale-105" 
       alt="Zoomable image">
</div>
```

### Border Glow

```html
<div class="rounded-2xl border border-white/10 bg-neutral-900
            hover:border-white/20 hover:shadow-2xl hover:shadow-brand-500/10
            transition-all duration-500">
  <!-- Content -->
</div>
```

### Text Color Change

```html
<h3 class="text-zinc-900 group-hover:text-brand-600 
           transition-colors duration-300">
  Hover to change color
</h3>
```

### Background Shift

```html
<div class="bg-white hover:bg-zinc-50 
            transition-colors duration-500">
  <!-- Content -->
</div>
```

## Group Hover Patterns

Use `group` class on parent to trigger child animations:

```html
<div class="group rounded-2xl p-6">
  <!-- Icon scales on card hover -->
  <div class="w-10 h-10 rounded-xl bg-brand-50
              group-hover:scale-110 
              transition-transform duration-300">
    <!-- Icon -->
  </div>
  
  <!-- Title changes color -->
  <h3 class="text-zinc-900 group-hover:text-brand-600 
             transition-colors duration-300">
    Feature Title
  </h3>
  
  <!-- Element slides -->
  <div class="group-hover:translate-x-1 
              transition-transform duration-300">
    Read more →
  </div>
</div>
```

## Staggered Animations

Use `delay` utilities for sequential reveals:

```html
<div class="grid grid-cols-4 gap-4">
  <div class="group-hover:translate-y-[-4px] transition-transform duration-300">
    Step 1
  </div>
  <div class="group-hover:translate-y-[-4px] transition-transform duration-300 delay-100">
    Step 2
  </div>
  <div class="group-hover:translate-y-[-4px] transition-transform duration-300 delay-200">
    Step 3
  </div>
  <div class="group-hover:translate-y-[-4px] transition-transform duration-300 delay-300">
    Step 4
  </div>
</div>
```

## Interactive Demo Elements

### Floating Data Points

```html
<div class="relative">
  <!-- Center element -->
  <div class="w-16 h-16 rounded-2xl bg-brand-500 
              group-hover:scale-110 transition-transform duration-500">
    <!-- Icon -->
  </div>
  
  <!-- Orbiting elements -->
  <div class="absolute -left-4 top-0 w-6 h-6 rounded-full bg-emerald-50
              group-hover:-translate-x-1 group-hover:-translate-y-1 
              transition-transform duration-500">
    <div class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></div>
  </div>
  
  <div class="absolute -right-4 top-0 w-6 h-6 rounded-full bg-blue-50
              group-hover:translate-x-1 group-hover:-translate-y-1 
              transition-transform duration-500 delay-100">
    <div class="w-2 h-2 rounded-full bg-blue-400 animate-pulse" 
         style="animation-delay: 0.5s;"></div>
  </div>
</div>
```

### Rotating/Transforming Cards

```html
<div class="grid grid-cols-2 gap-2">
  <div class="bg-blue-50 rounded-xl p-3 
              group-hover:scale-105 group-hover:-rotate-1 
              transition-all duration-300">
    Item 1
  </div>
  <div class="bg-emerald-50 rounded-xl p-3 
              group-hover:scale-105 group-hover:rotate-1 
              transition-all duration-300 delay-75">
    Item 2
  </div>
</div>
```

## Pulsing & Loading States

### Pulse Indicator

```html
<span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
```

### Custom Pulse Timing

```html
<span class="w-1.5 h-1.5 rounded-full bg-brand-400" 
      style="animation: pulse 3s ease-in-out infinite;"></span>
```

### Spinning Loader

```html
<svg class="animate-spin text-brand-500" style="animation-duration: 3s;">
  <!-- Spinner SVG paths -->
</svg>
```

### Shimmer Effect

```html
<div class="relative overflow-hidden">
  <div class="absolute inset-0 bg-gradient-to-r from-transparent via-white/10 to-transparent"
       style="animation: shimmer 2s infinite;"></div>
</div>

<style>
@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}
</style>
```

## Reveal Animations

### Fade In on Appear

```html
<div class="opacity-0 translate-y-4 
            animate-[fadeIn_0.5s_ease-out_forwards]">
  Content appears with fade
</div>

<style>
@keyframes fadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
```

### Staggered List Reveal

```html
<ul class="space-y-2">
  <li class="animate-[fadeIn_0.3s_ease-out_forwards]" style="animation-delay: 0ms;">Item 1</li>
  <li class="animate-[fadeIn_0.3s_ease-out_forwards]" style="animation-delay: 100ms;">Item 2</li>
  <li class="animate-[fadeIn_0.3s_ease-out_forwards]" style="animation-delay: 200ms;">Item 3</li>
</ul>
```

## Button Interactions

### Scale on Press

```html
<button class="px-4 py-2 bg-brand-500 text-white rounded-lg
               hover:bg-brand-600
               active:scale-95
               transition-all duration-150">
  Click Me
</button>
```

### Arrow Slide on Hover

```html
<a href="#" class="inline-flex items-center gap-2 group">
  Learn More
  <svg class="w-4 h-4 group-hover:translate-x-1 transition-transform duration-300">
    <path d="M5 12h14m-7-7 7 7-7 7" />
  </svg>
</a>
```

## Decorative Background Animations

### Floating Gradient Blobs

```html
<div class="absolute inset-0 pointer-events-none">
  <div class="absolute top-1/4 left-1/4 w-96 h-96 
              bg-brand-500/10 rounded-full blur-[120px] animate-pulse">
  </div>
  <div class="absolute bottom-1/4 right-1/4 w-96 h-96 
              bg-purple-500/10 rounded-full blur-[120px] animate-pulse" 
       style="animation-delay: 2s;">
  </div>
</div>
```

### Bouncing Arrow

```html
<svg class="animate-bounce text-brand-400">
  <path d="M12 5v14m7-7-7 7-7-7" />
</svg>
```

## Timing Guidelines

| Interaction Type | Duration | Use Case |
|------------------|----------|----------|
| **Instant** | 100-150ms | Button press, toggle |
| **Quick** | 200-300ms | Hover states, small reveals |
| **Standard** | 300-500ms | Card animations, transitions |
| **Dramatic** | 500-700ms | Hero reveals, page transitions |
| **Slow** | 700-1000ms | Background effects, ambient |

## Performance Best Practices

```css
/* Only animate transform and opacity for best performance */
.optimized-animation {
  will-change: transform, opacity;
  transform: translateZ(0); /* GPU acceleration */
}

/* Avoid animating */
.avoid {
  /* ❌ Don't animate: width, height, top, left, margin, padding, box-shadow */
}
```

## Accessibility

```html
<!-- Respect reduced motion preferences -->
<div class="motion-safe:hover:-translate-y-1 
            motion-safe:transition-transform 
            motion-safe:duration-300">
  Respects user preferences
</div>
```

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## Common Patterns Cheatsheet

```html
<!-- Card lift -->
class="hover:-translate-y-1 transition-transform duration-300"

<!-- Image zoom -->
class="group-hover:scale-105 transition-transform duration-500"

<!-- Color shift -->
class="hover:text-brand-600 transition-colors duration-300"

<!-- Glow effect -->
class="hover:shadow-2xl hover:shadow-brand-500/10 transition-all duration-500"

<!-- Element reveal -->
class="group-hover:opacity-100 opacity-0 transition-opacity duration-300"

<!-- Icon scale -->
class="group-hover:scale-110 transition-transform duration-300"

<!-- Slide in -->
class="group-hover:translate-x-1 transition-transform duration-300"
```

## Resources

- [Tailwind Transition Utilities](https://tailwindcss.com/docs/transition-property)
- [Cubic Bezier Easing](https://cubic-bezier.com/)
- [UI Animation Guidelines](https://material.io/design/motion)
