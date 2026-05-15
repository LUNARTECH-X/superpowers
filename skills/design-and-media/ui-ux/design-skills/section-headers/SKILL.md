---
name: Section Headers
description: Design impactful section headers with eyebrows, titles, descriptions, and badges
---

# Section Headers

Create consistent, visually striking section headers with eyebrow text, main titles, descriptions, and optional badges or CTAs.

## Overview

A well-designed section header establishes:
- **Hierarchy** — clear visual importance
- **Context** — category or topic indicator
- **Information** — what the section contains
- **Action** — optional CTAs or links

## Anatomy of a Section Header

```
┌─────────────────────────────────────────────────────────┐
│ [BADGE] Eyebrow Text                                    │
│                                                         │
│ Main Title Text                                         │
│                                                         │
│ Supporting description text that provides               │
│ additional context about the section.                   │
│                                                         │
│                                        [Optional CTA]   │
└─────────────────────────────────────────────────────────┘
```

## Dark Theme Headers

### Standard Dark Header

```html
<div class="flex flex-col sm:flex-row sm:items-end sm:justify-between gap-4 mb-12">
  <div>
    <p class="text-sm font-medium text-white/50 tracking-wider uppercase mb-2">
      Section Category
    </p>
    <h2 class="text-3xl sm:text-4xl md:text-5xl font-medium tracking-tight text-white">
      Section Title Here
    </h2>
    <p class="mt-3 text-base text-white/70 max-w-2xl">
      A brief description providing context about what this section contains
      and why it matters to the reader.
    </p>
  </div>
</div>
```

### Dark Header with Badge

```html
<div class="text-center mb-16">
  <span class="inline-flex items-center gap-2 rounded-full 
               border border-emerald-500/30 bg-emerald-500/10 
               px-4 py-1.5 text-xs font-medium text-emerald-400 mb-6">
    <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse"></span>
    Live Status Badge
  </span>
  
  <h2 class="text-3xl md:text-4xl lg:text-5xl font-medium text-white tracking-tight mb-4">
    Main Section Title<br class="hidden sm:block">
    Multi-line Supported
  </h2>
  
  <p class="text-neutral-400 text-base md:text-lg max-w-2xl mx-auto leading-relaxed">
    Description text that explains the section purpose with appropriate
    line length for readability.
  </p>
</div>
```

### Gradient Title

```html
<h2 class="text-4xl md:text-5xl lg:text-6xl font-medium tracking-tight text-white mb-6">
  Synthetic Data<br>
  Generation <span class="bg-gradient-to-r from-brand-400 to-purple-400 bg-clip-text text-transparent">Engine</span>
</h2>
```

## Light Theme Headers

### Standard Light Header

```html
<div class="flex sm:mb-8 mb-6 items-end justify-between">
  <div>
    <p class="text-[11px] sm:text-xs tracking-widest text-neutral-500 uppercase">
      Platform Overview
    </p>
    <h3 class="mt-2 text-2xl sm:text-3xl tracking-tight font-medium">
      What is <span class="text-brand-600">BrandName</span>?
    </h3>
  </div>
</div>
```

### Light Header with Description

```html
<div class="mb-12">
  <p class="text-xs font-medium text-zinc-500 tracking-wider uppercase mb-2">
    Features
  </p>
  <h2 class="text-3xl sm:text-4xl font-semibold text-zinc-900 tracking-tight mb-4">
    Everything you need
  </h2>
  <p class="text-zinc-600 text-lg max-w-2xl">
    Comprehensive description of the section's contents and value proposition.
  </p>
</div>
```

## Eyebrow Styles

### Simple Uppercase

```html
<p class="text-[11px] sm:text-xs tracking-widest text-neutral-500 uppercase">
  Category Name
</p>
```

### With Dot Indicator

```html
<div class="flex items-center gap-2 mb-2">
  <span class="w-2 h-2 rounded-full bg-brand-500"></span>
  <span class="text-xs font-medium text-brand-600 uppercase tracking-wider">
    Category
  </span>
</div>
```

### Badge Style

```html
<span class="inline-flex items-center gap-2 px-3 py-1.5 bg-brand-50 rounded-full mb-4">
  <div class="w-2 h-2 rounded-full bg-brand-500 animate-pulse"></div>
  <span class="text-[10px] font-semibold text-brand-700 uppercase tracking-wider">
    AI-Powered Platform
  </span>
</span>
```

### Pill with Border

```html
<span class="inline-flex items-center gap-2 rounded-full 
             border border-brand-500/30 bg-brand-500/10 
             px-4 py-1.5 text-xs font-medium text-brand-400">
  <span class="w-1.5 h-1.5 rounded-full bg-brand-400"></span>
  What We Built
</span>
```

## Title Sizing Scale

| Breakpoint | Classes | Use Case |
|------------|---------|----------|
| Mobile | `text-2xl` or `text-3xl` | Compact |
| Tablet | `sm:text-3xl` or `sm:text-4xl` | Medium |
| Desktop | `md:text-4xl` or `md:text-5xl` | Standard |
| Large | `lg:text-5xl` or `lg:text-6xl` | Hero |

### Responsive Example

```html
<h2 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl 
           font-medium tracking-tight">
  Responsive Title
</h2>
```

## Layout Patterns

### Left-Aligned (Default)

```html
<div class="mb-12">
  <p class="eyebrow">Category</p>
  <h2 class="title">Section Title</h2>
  <p class="description max-w-2xl">Description text...</p>
</div>
```

### Centered

```html
<div class="text-center mb-16">
  <p class="eyebrow">Category</p>
  <h2 class="title">Section Title</h2>
  <p class="description max-w-2xl mx-auto">Description text...</p>
</div>
```

### With Right-Aligned CTA

```html
<div class="flex flex-col sm:flex-row sm:items-end sm:justify-between gap-4 mb-12">
  <div>
    <p class="eyebrow">Category</p>
    <h2 class="title">Section Title</h2>
  </div>
  <a href="#" class="inline-flex items-center gap-2 text-brand-500 hover:text-brand-600">
    View all
    <svg><!-- Arrow icon --></svg>
  </a>
</div>
```

## Typography Guidelines

### Font Weights

| Element | Weight | Tailwind |
|---------|--------|----------|
| Eyebrow | Medium/Semibold | `font-medium` |
| Title | Medium/Semibold | `font-medium` or `font-semibold` |
| Description | Regular | `font-normal` (default) |

### Letter Spacing

| Element | Spacing | Tailwind |
|---------|---------|----------|
| Eyebrow | Wide | `tracking-wider` or `tracking-widest` |
| Title | Tight | `tracking-tight` |
| Description | Normal | Default |

### Line Height

```html
<!-- Tight for titles -->
<h2 class="leading-tight">Multi-line Title</h2>
<!-- or -->
<h2 class="leading-[1.1]">Precise Control</h2>

<!-- Relaxed for descriptions -->
<p class="leading-relaxed">Description paragraph...</p>
```

## Color Patterns

### Dark Theme

```html
<p class="text-white/50">Eyebrow (muted)</p>
<h2 class="text-white">Title (primary)</h2>
<p class="text-white/70">Description (secondary)</p>
```

### Light Theme

```html
<p class="text-neutral-500">Eyebrow (muted)</p>
<h2 class="text-zinc-900">Title (primary)</h2>
<p class="text-zinc-600">Description (secondary)</p>
```

### Brand Accent

```html
<span class="text-brand-600">Highlighted</span>
<!-- or gradient -->
<span class="bg-gradient-to-r from-brand-400 to-purple-400 bg-clip-text text-transparent">
  Gradient Text
</span>
```

## Complete Examples

### Hero Section Header

```html
<div class="text-center max-w-4xl mx-auto mb-20">
  <div class="inline-flex items-center gap-2 px-3 py-1.5 
              bg-brand-500/10 border border-brand-500/20 
              rounded-full mb-6">
    <div class="w-2 h-2 rounded-full bg-brand-400 animate-pulse"></div>
    <span class="text-xs font-semibold text-brand-300 uppercase tracking-wider">
      Now Available
    </span>
  </div>
  
  <h1 class="text-4xl md:text-5xl lg:text-6xl font-medium tracking-tight text-white mb-6 leading-[1.1]">
    Revolutionary AI<br>
    <span class="bg-gradient-to-r from-brand-400 to-purple-400 bg-clip-text text-transparent">
      For Healthcare
    </span>
  </h1>
  
  <p class="text-lg text-white/60 max-w-2xl mx-auto leading-relaxed">
    Comprehensive AI platform enabling early detection and precise diagnosis
    through advanced multimodal analysis.
  </p>
</div>
```

### Feature Section Header

```html
<div class="flex flex-col sm:flex-row sm:items-end sm:justify-between gap-4 mb-12">
  <div>
    <p class="text-sm font-medium text-white/50 tracking-wider uppercase mb-2">
      Core Technologies
    </p>
    <h2 class="text-3xl sm:text-4xl md:text-5xl font-medium tracking-tight text-white">
      Our Technology Stack
    </h2>
    <p class="mt-3 text-base text-white/70 max-w-2xl">
      Advanced capabilities powering the next generation of early cancer detection.
    </p>
  </div>
</div>
```

## Spacing Guidelines

| Spacing | Value | Use |
|---------|-------|-----|
| Eyebrow → Title | `mb-2` | Minimal |
| Title → Description | `mt-3` or `mb-3` | Standard |
| Header → Content | `mb-12` to `mb-16` | Section gap |

## Resources

- [Typography Scale Tool](https://typescale.com)
- [Tailwind Typography](https://tailwindcss.com/docs/font-size)
