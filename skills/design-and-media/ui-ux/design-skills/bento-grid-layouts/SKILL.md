---
name: Bento Grid Layouts
description: Create premium asymmetric card-based grid layouts inspired by Apple and modern SaaS design
---

# Bento Grid Layouts

Build visually striking asymmetric grid layouts that combine cards of varying sizes to create dynamic, premium interfaces commonly seen on Apple product pages and modern SaaS websites.

## Overview

Bento grids break away from uniform column layouts by mixing:
- **Hero cards** (spanning 2 columns or rows)
- **Standard cards** (single cell)
- **Accent cards** (small, focused content)
- **CTA cards** (spanning full width)

## Core Structure

### Basic Grid Setup

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  <!-- Hero Card: 2 columns, 2 rows -->
  <div class="md:col-span-2 md:row-span-2">
    <!-- Large featured content -->
  </div>
  
  <!-- Standard Cards -->
  <div><!-- Card 2 --></div>
  <div><!-- Card 3 --></div>
  <div><!-- Card 4 --></div>
  
  <!-- Wide Card: Full row -->
  <div class="lg:col-span-3">
    <!-- CTA or summary content -->
  </div>
</div>
```

### Grid Configuration Patterns

| Pattern | Grid | Hero Span | Use Case |
|---------|------|-----------|----------|
| **3-Column** | `grid-cols-3` | `col-span-2 row-span-2` | Technology showcases |
| **4-Column** | `grid-cols-4` | `col-span-2` | Team/feature grids |
| **2-Column** | `grid-cols-2` | `col-span-2` | Platform overviews |

## Card Variants

### 1. Hero Card (2x2)

The focal point with image, title, and description:

```html
<div class="group relative overflow-hidden rounded-2xl border border-white/10 bg-white/5 md:col-span-2 md:row-span-2">
  <!-- Image Section -->
  <div class="relative overflow-hidden rounded-t-2xl">
    <img src="image.png" alt="Feature" 
         class="aspect-video w-full object-cover transition-transform duration-700 group-hover:scale-105">
    <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/30 to-transparent"></div>
  </div>
  
  <!-- Content Section -->
  <div class="p-6 sm:p-8">
    <span class="inline-flex items-center gap-1.5 rounded-full border border-brand-500/30 bg-brand-500/15 px-2.5 py-0.5 text-[11px] font-medium text-brand-300">
      <span class="w-1.5 h-1.5 rounded-full bg-brand-400 animate-pulse"></span>
      PRIMARY
    </span>
    <h3 class="text-2xl sm:text-3xl font-medium tracking-tight text-white mb-3 mt-3">
      Hero Feature Title
    </h3>
    <p class="text-sm sm:text-base text-white/70 max-w-xl">
      Comprehensive description of the primary feature or product.
    </p>
  </div>
</div>
```

### 2. Standard Card (1x1)

Compact feature cards:

```html
<div class="group relative overflow-hidden rounded-2xl border border-white/10 bg-white/5">
  <div class="p-5 sm:p-6">
    <h3 class="text-xl font-medium tracking-tight text-white mb-3">Feature Name</h3>
    <p class="text-sm text-white/60 mb-4">Brief description of the feature.</p>
    <div class="rounded-xl overflow-hidden border border-white/10">
      <img src="feature.png" alt="Feature" 
           class="aspect-video w-full object-cover transition-transform duration-500 group-hover:scale-105">
    </div>
  </div>
</div>
```

### 3. Stats Card

For metrics and numbers:

```html
<div class="group relative overflow-hidden rounded-2xl border border-white/10 bg-neutral-900/50 hover:-translate-y-1 transition-all duration-500">
  <div class="p-6">
    <div class="flex items-center justify-between mb-4">
      <div class="w-11 h-11 rounded-xl bg-violet-500/15 flex items-center justify-center">
        <!-- Icon -->
      </div>
      <span class="text-[10px] font-medium text-neutral-500 uppercase tracking-wider">Label</span>
    </div>
    <p class="text-4xl font-semibold text-white mb-1">35%</p>
    <p class="text-neutral-500 text-sm">Metric Description</p>
  </div>
</div>
```

### 4. Interactive Demo Card

Cards with embedded visualizations:

```html
<div class="group bg-white hover:bg-zinc-50 transition-all duration-500 min-h-[280px] p-8 flex flex-col">
  <!-- Demo/Visualization Area -->
  <div class="mb-6 flex-1">
    <!-- Interactive content, charts, or icons -->
    <div class="grid grid-cols-2 gap-2">
      <div class="bg-blue-50 rounded-xl p-3 border border-blue-100 
                  group-hover:scale-105 group-hover:-rotate-1 transition-all duration-300">
        <!-- Content -->
      </div>
      <!-- More grid items -->
    </div>
  </div>
  
  <!-- Title & Description -->
  <h4 class="text-lg font-semibold text-zinc-900 tracking-tight mb-1 
             group-hover:text-brand-600 transition-colors duration-300">
    Feature Title
  </h4>
  <p class="text-sm text-zinc-500 leading-relaxed">Description text</p>
</div>
```

### 5. CTA Card (Full Width)

Call-to-action spanning multiple columns:

```html
<div class="group rounded-2xl border border-white/10 bg-neutral-900/50 md:col-span-3">
  <div class="p-6 md:p-8 flex flex-col md:flex-row items-start md:items-center justify-between gap-6">
    <div>
      <h3 class="text-xl font-semibold text-white mb-2">Join the Mission</h3>
      <p class="text-neutral-400 text-sm max-w-md">
        Compelling call-to-action description.
      </p>
    </div>
    <a href="#" class="inline-flex items-center gap-2 px-5 py-2.5 rounded-full bg-brand-500 text-white">
      Get Started
    </a>
  </div>
</div>
```

## Light vs Dark Themes

### Dark Theme (Tech/SaaS)

```css
/* Card base */
.card-dark {
  @apply border-white/10 bg-white/5;
  /* or */
  @apply border-white/10 bg-neutral-900/50 backdrop-blur-md;
}

/* Text */
.text-dark {
  @apply text-white;
}
.text-muted-dark {
  @apply text-white/60;
}

/* Hover */
.card-dark:hover {
  @apply bg-white/10 border-white/20;
}
```

### Light Theme (Clean/Medical)

```css
/* Card base */
.card-light {
  @apply bg-white border-zinc-200;
}

/* Text */
.text-light {
  @apply text-zinc-900;
}
.text-muted-light {
  @apply text-zinc-500;
}

/* Hover */
.card-light:hover {
  @apply bg-zinc-50;
}
```

## Grid Layout Patterns

### Technology Grid (3-col with Hero)

```
┌─────────────┬──────┐
│             │  B   │
│     A       ├──────┤
│   (2x2)     │  C   │
├──────┬──────┼──────┤
│  D   │  E   │  F   │
├──────┴──────┴──────┤
│        CTA         │
└────────────────────┘
```

### Team/Stats Grid (4-col)

```
┌─────────────┬──────┬──────┐
│             │  B   │  C   │
│     A       ├──────┼──────┤
│   (2x2)     │  D   │  E   │
├──────┬──────┴──────┴──────┤
│  F   │        CTA         │
└──────┴────────────────────┘
```

### Platform Overview (Gap-less)

```html
<!-- Seamless grid with gap-px for hairline borders -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-px bg-zinc-200 rounded-[2rem] overflow-hidden">
  <!-- Cards have bg-white to show the gap-px as borders -->
</div>
```

## Hover Effects

```css
/* Card hover */
.bento-card {
  @apply transition-all duration-500;
}
.bento-card:hover {
  @apply -translate-y-1;
  @apply shadow-2xl shadow-brand-500/10;
  @apply bg-neutral-800/50 border-white/20;
}

/* Image scale on card hover */
.bento-card:hover img {
  @apply scale-105;
}

/* Title color change on hover */
.bento-card:hover h3 {
  @apply text-brand-600;
}
```

## Responsive Considerations

```html
<div class="grid 
            grid-cols-1       /* Mobile: single column */
            md:grid-cols-2    /* Tablet: 2 columns */
            lg:grid-cols-3    /* Desktop: 3 columns */
            gap-4">
  
  <!-- Hero spans 2 cols on md+, 2 rows on md+ -->
  <div class="md:col-span-2 md:row-span-2">
    <!-- Hero content -->
  </div>
  
  <!-- CTA spans all columns at each breakpoint -->
  <div class="md:col-span-2 lg:col-span-3">
    <!-- CTA content -->
  </div>
</div>
```

## Best Practices

1. **Visual Hierarchy**: Hero card should contain your most important content
2. **Consistent Padding**: Use `p-6` or `p-8` consistently across cards
3. **Image Ratios**: Use `aspect-video` or `aspect-square` for consistency
4. **Border Radius**: Match radius across all cards (`rounded-2xl`)
5. **Animation Duration**: Use consistent timing (300-500ms for hovers)
6. **Color Accents**: Use brand colors sparingly for badges and highlights

## Resources

- [Apple Design Inspiration](https://apple.com)
- [Tailwind CSS Grid](https://tailwindcss.com/docs/grid-template-columns)
- [Framer Motion for Animations](https://www.framer.com/motion/)
