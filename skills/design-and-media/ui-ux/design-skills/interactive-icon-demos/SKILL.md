---
name: Interactive Icon Demos
description: Create animated icon-based demonstrations that respond to hover states
---

# Interactive Icon Demos

Build animated icon arrangements and micro-visualizations that bring UI cards to life.

## Network/Graph Visualization

```html
<div class="relative w-full h-32">
  <!-- Center Node -->
  <div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 
              w-12 h-12 rounded-xl bg-brand-500 flex items-center justify-center shadow-lg z-10 
              group-hover:scale-110 transition-transform duration-500">
    <svg class="w-5 h-5 text-white"><!-- Icon --></svg>
  </div>
  
  <!-- Peripheral Nodes -->
  <div class="absolute left-2 top-2 w-8 h-8 rounded-lg bg-white shadow-md border border-zinc-100 
              flex items-center justify-center 
              group-hover:-translate-y-1 transition-transform duration-500">
    <div class="w-4 h-4 rounded-full bg-blue-200"></div>
  </div>
  <div class="absolute right-2 top-2 w-8 h-8 rounded-lg bg-white shadow-md border border-zinc-100 
              group-hover:-translate-y-1 transition-transform duration-500 delay-100">
    <div class="w-4 h-4 rounded-full bg-emerald-200"></div>
  </div>
  
  <!-- Connection Lines -->
  <svg class="absolute inset-0 w-full h-full opacity-20 group-hover:opacity-40 transition-opacity duration-500">
    <line x1="30" y1="25" x2="100" y2="65" stroke="#7C3AED" stroke-width="1.5" stroke-dasharray="4" />
  </svg>
</div>
```

## Orbiting Elements

```html
<div class="relative">
  <!-- Central element -->
  <div class="w-16 h-16 rounded-2xl bg-indigo-100 flex items-center justify-center 
              group-hover:scale-110 transition-transform duration-500">
    <svg class="w-7 h-7 text-indigo-500"><!-- Icon --></svg>
  </div>
  
  <!-- Orbiting dots -->
  <div class="absolute -left-6 top-0 w-6 h-6 rounded-full bg-emerald-50 border border-emerald-100 
              group-hover:-translate-x-1 group-hover:-translate-y-1 transition-transform duration-500">
    <div class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></div>
  </div>
  <div class="absolute -right-6 top-0 w-6 h-6 rounded-full bg-blue-50 border border-blue-100 
              group-hover:translate-x-1 group-hover:-translate-y-1 transition-transform duration-500 delay-100">
    <div class="w-2 h-2 rounded-full bg-blue-400 animate-pulse" style="animation-delay: 0.5s;"></div>
  </div>
</div>
```

## Data Type Grid

```html
<div class="grid grid-cols-2 gap-2">
  <div class="bg-blue-50 rounded-xl p-3 border border-blue-100 
              group-hover:scale-105 group-hover:-rotate-1 transition-all duration-300">
    <div class="w-full h-8 rounded-lg bg-gradient-to-br from-blue-200 to-blue-100 mb-2 
                flex items-center justify-center">
      <svg class="w-4 h-4 text-blue-500"><!-- Image icon --></svg>
    </div>
    <p class="text-[9px] font-medium text-blue-700">CT / MRI</p>
  </div>
  <div class="bg-emerald-50 rounded-xl p-3 border border-emerald-100 
              group-hover:scale-105 group-hover:rotate-1 transition-all duration-300 delay-75">
    <div class="w-full h-8 rounded-lg bg-gradient-to-br from-emerald-200 to-emerald-100 mb-2 
                flex items-center justify-center">
      <svg class="w-4 h-4 text-emerald-500"><!-- DNA icon --></svg>
    </div>
    <p class="text-[9px] font-medium text-emerald-700">Genomics</p>
  </div>
</div>
```

## Shield with Orbiting Security

```html
<div class="relative">
  <!-- Central Shield -->
  <div class="w-20 h-24 relative group-hover:scale-110 transition-transform duration-500">
    <svg viewBox="0 0 24 24" class="w-full h-full text-brand-500">
      <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" 
            fill="currentColor" fill-opacity="0.1" />
      <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" 
            stroke="currentColor" stroke-width="1" fill="none" />
    </svg>
    <!-- Lock Icon overlay -->
    <div class="absolute inset-0 flex items-center justify-center">
      <svg class="w-5 h-5 text-brand-600"><!-- Lock --></svg>
    </div>
  </div>
  
  <!-- Orbiting badges -->
  <div class="absolute -left-4 top-2 w-8 h-8 rounded-lg bg-emerald-50 border border-emerald-100 
              group-hover:-translate-x-1 transition-transform duration-500">
    <svg class="w-3 h-3 text-emerald-500"><!-- Check --></svg>
  </div>
</div>
```

## Decision Tree

```html
<div class="relative w-full max-w-[200px]">
  <!-- Root Node -->
  <div class="flex justify-center mb-3">
    <div class="w-12 h-12 rounded-xl bg-brand-500 flex items-center justify-center shadow-md 
                group-hover:scale-110 transition-transform duration-300">
      <svg class="w-5 h-5 text-white"><!-- AI icon --></svg>
    </div>
  </div>
  
  <!-- Branches -->
  <div class="flex justify-center gap-8">
    <div class="flex flex-col items-center group-hover:-translate-x-1 transition-transform duration-300 delay-100">
      <div class="w-px h-4 bg-zinc-300"></div>
      <div class="w-8 h-8 rounded-lg bg-emerald-50 border border-emerald-100">
        <svg class="w-3 h-3 text-emerald-500"><!-- Check --></svg>
      </div>
      <p class="text-[8px] text-zinc-500 mt-1">Low Risk</p>
    </div>
    <div class="flex flex-col items-center group-hover:translate-x-1 transition-transform duration-300 delay-200">
      <div class="w-px h-4 bg-zinc-300"></div>
      <div class="w-8 h-8 rounded-lg bg-amber-50 border border-amber-100">
        <svg class="w-3 h-3 text-amber-500"><!-- Alert --></svg>
      </div>
      <p class="text-[8px] text-zinc-500 mt-1">Review</p>
    </div>
  </div>
</div>
```

## AI Agent Interface

```html
<div class="bg-zinc-50 rounded-2xl p-4 border border-zinc-100">
  <div class="flex items-center gap-3 mb-3">
    <div class="w-8 h-8 rounded-lg bg-brand-500 flex items-center justify-center">
      <svg class="w-4 h-4 text-white"><!-- Sparkle --></svg>
    </div>
    <div class="bg-brand-50 rounded-xl px-3 py-2 flex-1">
      <p class="text-[9px] font-semibold text-brand-700">AI Agent Active</p>
      <p class="text-[8px] text-brand-600 mt-0.5">Processing analysis...</p>
    </div>
  </div>
  <div class="space-y-2">
    <div class="flex items-center gap-2 group-hover:translate-x-1 transition-transform duration-300">
      <div class="w-4 h-4 rounded-full bg-emerald-100 flex items-center justify-center">
        <svg class="w-2 h-2 text-emerald-600"><!-- Check --></svg>
      </div>
      <span class="text-[10px] text-zinc-600">Step complete</span>
    </div>
    <div class="flex items-center gap-2 group-hover:translate-x-1 transition-transform duration-300 delay-75">
      <div class="w-4 h-4 rounded-full border-2 border-brand-300 animate-spin" 
           style="animation-duration: 2s;"></div>
      <span class="text-[10px] text-zinc-600">Processing...</span>
    </div>
  </div>
</div>
```

## Animation Guidelines

1. Use `group-hover` for parent-triggered animations
2. Stagger with `delay-75`, `delay-100`, `delay-200`
3. Keep transforms subtle (scale 1.05-1.1, translate 1-4px)
4. Use `transition-transform` for performance
5. Pair with `animate-pulse` for activity indicators
