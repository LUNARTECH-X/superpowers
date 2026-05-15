---
name: Feature Grid Sections
description: Create two-column feature sections with content and visual demos
---

# Feature Grid Sections

Build impactful two-column sections that pair text content with interactive visual demonstrations.

## Overview

Feature grid sections combine:
- **Content column** — Title, description, feature list
- **Visual column** — Interactive demo, illustration, or card

## Basic Structure

```html
<section class="py-24 md:py-32 px-6 bg-zinc-950">
  <div class="max-w-7xl mx-auto">
    <div class="grid lg:grid-cols-2 gap-16 items-center">
      <!-- Content Column -->
      <div>
        <!-- Badge -->
        <div class="inline-flex items-center gap-2 px-3 py-1.5 
                    bg-brand-500/10 border border-brand-500/20 rounded-full mb-6">
          <div class="w-2 h-2 rounded-full bg-brand-400 animate-pulse"></div>
          <span class="text-xs font-semibold text-brand-300 uppercase tracking-wider">
            Category
          </span>
        </div>
        
        <!-- Title -->
        <h2 class="text-4xl md:text-5xl lg:text-6xl font-medium tracking-tight text-white mb-6 leading-[1.1]">
          Feature Title<br>
          <span class="bg-gradient-to-r from-brand-400 to-purple-400 bg-clip-text text-transparent">
            Highlighted
          </span>
        </h2>
        
        <!-- Description -->
        <p class="text-lg text-white/60 mb-10 max-w-lg leading-relaxed">
          Description text explaining the feature and its benefits.
        </p>
        
        <!-- Feature Grid -->
        <div class="grid grid-cols-2 gap-4">
          <div class="group p-4 rounded-2xl bg-white/5 border border-white/10 
                      hover:bg-white/10 hover:border-brand-500/30 transition-all duration-300">
            <div class="w-10 h-10 rounded-xl bg-emerald-500/20 flex items-center justify-center mb-3 
                        group-hover:scale-110 transition-transform duration-300">
              <svg class="text-emerald-400"><!-- Icon --></svg>
            </div>
            <h4 class="text-white font-medium mb-1">Feature One</h4>
            <p class="text-white/50 text-sm">Brief description</p>
          </div>
          <!-- More feature cards -->
        </div>
      </div>
      
      <!-- Visual Column -->
      <div class="relative">
        <!-- Glow effect -->
        <div class="absolute -inset-4 bg-gradient-to-r from-brand-500/20 via-purple-500/20 to-brand-500/20 
                    rounded-[2rem] blur-2xl opacity-50"></div>
        
        <!-- Demo card -->
        <div class="relative rounded-[1.5rem] overflow-hidden border border-white/10 
                    bg-gradient-to-br from-zinc-900 via-zinc-900 to-zinc-950 p-6">
          <!-- Interactive demo content -->
        </div>
      </div>
    </div>
  </div>
</div>
```

## Feature Item Patterns

### Icon Card

```html
<div class="group p-4 rounded-2xl bg-white/5 border border-white/10 
            hover:bg-white/10 hover:border-brand-500/30 transition-all duration-300">
  <div class="w-10 h-10 rounded-xl bg-emerald-500/20 flex items-center justify-center mb-3 
              group-hover:scale-110 transition-transform duration-300">
    <svg class="w-5 h-5 text-emerald-400"><!-- Icon --></svg>
  </div>
  <h4 class="text-white font-medium mb-1">Feature Name</h4>
  <p class="text-white/50 text-sm">Brief description text</p>
</div>
```

### Bullet List

```html
<div class="space-y-5">
  <div class="flex items-start gap-4">
    <div class="w-2 h-2 rounded-full bg-violet-400 mt-2 flex-shrink-0"></div>
    <p class="text-neutral-400 text-sm leading-relaxed">Feature description</p>
  </div>
</div>
```

## Visual Demo Patterns

### Terminal/Code Card

```html
<div class="rounded-xl bg-zinc-900 border border-white/10">
  <!-- Header -->
  <div class="flex items-center gap-2 px-4 py-3 border-b border-white/10">
    <div class="flex gap-1.5">
      <div class="w-3 h-3 rounded-full bg-red-500/50"></div>
      <div class="w-3 h-3 rounded-full bg-yellow-500/50"></div>
      <div class="w-3 h-3 rounded-full bg-green-500/50"></div>
    </div>
    <span class="text-white/40 text-xs font-mono">pipeline.py</span>
  </div>
  <!-- Content -->
  <div class="p-4"><!-- Code/demo --></div>
</div>
```

### Data Flow Visual

```html
<div class="space-y-4">
  <!-- Input row -->
  <div class="flex items-center gap-4">
    <span class="w-20 text-right text-white/30 text-xs font-mono">INPUT</span>
    <div class="flex-1 flex gap-2">
      <div class="flex-1 h-10 rounded-lg bg-blue-500/20 border border-blue-500/30 
                  flex items-center justify-center">
        <span class="text-blue-400 text-xs font-medium">Data Type</span>
      </div>
    </div>
  </div>
  
  <!-- Arrow -->
  <div class="flex justify-center">
    <svg class="text-brand-400 animate-bounce"><!-- Down arrow --></svg>
  </div>
  
  <!-- Output row -->
  <div class="flex items-center gap-4">
    <span class="w-20 text-right text-white/30 text-xs font-mono">OUTPUT</span>
    <div class="flex-1 h-14 rounded-xl bg-emerald-500/10 border border-emerald-500/30">
      <span class="text-emerald-300">Result</span>
    </div>
  </div>
</div>
```

## Stats Footer

```html
<div class="mt-6 pt-6 border-t border-white/10 grid grid-cols-3 gap-4">
  <div class="text-center">
    <p class="text-2xl font-bold text-white">99.2%</p>
    <p class="text-white/40 text-xs">Accuracy</p>
  </div>
  <div class="text-center">
    <p class="text-2xl font-bold text-white">0.01%</p>
    <p class="text-white/40 text-xs">Error Rate</p>
  </div>
  <div class="text-center">
    <p class="text-2xl font-bold text-white">&lt;2min</p>
    <p class="text-white/40 text-xs">Process Time</p>
  </div>
</div>
```

## Responsive Layout

```html
<div class="grid lg:grid-cols-2 gap-16 items-center">
  <!-- On mobile: stacks vertically -->
  <!-- On lg+: side-by-side -->
</div>
```

## Animation Classes for Reveals

```html
<div class="reveal">
  <!-- Add JS to trigger visibility -->
</div>

<style>
.reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.6s ease-out;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
</style>
```
