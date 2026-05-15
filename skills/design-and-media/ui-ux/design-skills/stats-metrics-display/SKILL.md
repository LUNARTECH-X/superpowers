---
name: Stats & Metrics Display
description: Display key statistics and metrics with visual impact
---

# Stats & Metrics Display

Present numbers and metrics in visually impactful ways that communicate value and credibility.

## Overview

Effective stats displays:
- Draw attention with **large typography**
- Provide context with **labels**
- Use **icons** for visual recognition
- Apply **color accents** for hierarchy

## Basic Stat Card

```html
<div class="rounded-2xl border border-white/10 bg-neutral-900/50 p-6">
  <div class="flex items-center justify-between mb-4">
    <div class="w-11 h-11 rounded-xl bg-violet-500/15 flex items-center justify-center">
      <svg class="w-5 h-5 text-violet-400"><!-- Icon --></svg>
    </div>
    <span class="text-[10px] font-medium text-neutral-500 uppercase tracking-wider">
      Category
    </span>
  </div>
  <p class="text-4xl font-semibold text-white mb-1">35%</p>
  <p class="text-neutral-500 text-sm">Metric description</p>
</div>
```

## Large Hero Stat

```html
<div class="p-6 flex flex-col h-full">
  <span class="text-5xl md:text-6xl font-semibold 
               bg-gradient-to-r from-emerald-400 via-teal-400 to-cyan-400 
               bg-clip-text text-transparent">
    15+
  </span>
  <p class="text-neutral-500 text-xs uppercase tracking-[0.15em] font-medium mt-auto">
    Nationalities
  </p>
</div>
```

## Inline Stats Row

```html
<div class="flex items-center gap-6">
  <div class="flex items-center gap-2 group-hover:translate-x-1 transition-transform duration-300">
    <div class="w-10 h-10 rounded-xl bg-emerald-50 flex items-center justify-center 
                group-hover:scale-110 transition-transform duration-300">
      <svg class="text-emerald-600"><!-- Icon --></svg>
    </div>
    <div>
      <p class="text-lg font-bold text-zinc-900">20%+</p>
      <p class="text-[10px] text-zinc-500">Detection Improvement</p>
    </div>
  </div>
</div>
```

## Stats Grid Footer

```html
<div class="grid grid-cols-3 gap-4 pt-6 border-t border-white/10">
  <div class="text-center">
    <p class="text-2xl font-bold text-white">99.2%</p>
    <p class="text-white/40 text-xs">Fidelity Score</p>
  </div>
  <div class="text-center">
    <p class="text-2xl font-bold text-white">0.01%</p>
    <p class="text-white/40 text-xs">Privacy Risk</p>
  </div>
  <div class="text-center">
    <p class="text-2xl font-bold text-white">&lt;2min</p>
    <p class="text-white/40 text-xs">Generation Time</p>
  </div>
</div>
```

## Icon Color Variants

```html
<!-- Violet -->
<div class="w-11 h-11 rounded-xl bg-violet-500/15">
  <svg class="text-violet-400">
    
<!-- Pink -->
<div class="w-11 h-11 rounded-xl bg-pink-500/15">
  <svg class="text-pink-400">

<!-- Emerald -->
<div class="w-11 h-11 rounded-xl bg-emerald-500/15">
  <svg class="text-emerald-400">

<!-- Purple -->
<div class="w-11 h-11 rounded-xl bg-purple-500/15">
  <svg class="text-purple-400">
```

## Compact Badge Stats

```html
<span class="px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-mono">
  10,000+
</span>
```

## Typography Scale

| Stat Size | Class | Use Case |
|-----------|-------|----------|
| Hero | `text-5xl md:text-6xl` | Single highlight |
| Large | `text-4xl` | Card stat |
| Medium | `text-2xl` | Grid stat |
| Small | `text-lg` | Inline stat |

## Hover Effects

```html
<div class="hover:-translate-y-1 hover:shadow-2xl hover:shadow-violet-500/10 
            transition-all duration-500">
  <!-- Stat card -->
</div>
```
