---
name: Team & About Sections
description: Design team showcases, global presence displays, and company about sections
---

# Team & About Sections

Create compelling team and company sections that showcase expertise, global presence, and organizational values.

## Team Bento Grid

```html
<div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4">
  <!-- Large Map Card (2x2) -->
  <div class="md:col-span-2 md:row-span-2 rounded-3xl border border-white/10 bg-neutral-900/50 
              relative overflow-hidden min-h-[360px]">
    <div class="absolute inset-0 opacity-40 group-hover:opacity-60 transition-all duration-[2000ms]">
      <img src="world-map.png" class="w-full h-full object-cover" alt="Global Operations">
    </div>
    <div class="relative p-8 h-full flex flex-col justify-end">
      <h3 class="text-2xl md:text-3xl font-semibold text-white mb-3">Global Operations</h3>
      <p class="text-neutral-400 text-sm max-w-md">
        Hubs across 3 continents driving 24/7 innovation.
      </p>
    </div>
  </div>

  <!-- Stat Cards -->
  <div class="rounded-2xl border border-white/10 bg-neutral-900/50 p-6 
              hover:-translate-y-1 transition-all duration-500">
    <div class="flex items-center justify-between mb-4">
      <div class="w-11 h-11 rounded-xl bg-violet-500/15 flex items-center justify-center">
        <svg class="w-5 h-5 text-violet-400"><!-- Icon --></svg>
      </div>
      <span class="text-[10px] font-medium text-neutral-500 uppercase tracking-wider">Core</span>
    </div>
    <p class="text-4xl font-semibold text-white mb-1">35%</p>
    <p class="text-neutral-500 text-sm">AI & Machine Learning</p>
  </div>

  <!-- CTA Card (wide) -->
  <div class="md:col-span-3 rounded-2xl border border-white/10 bg-neutral-900/50 p-8">
    <div class="flex flex-col md:flex-row items-start md:items-center justify-between gap-6">
      <div>
        <h3 class="text-xl font-semibold text-white mb-2">Join the Mission</h3>
        <p class="text-neutral-400 text-sm max-w-md">We're looking for extraordinary talent.</p>
      </div>
      <a href="#" class="px-6 py-3 rounded-full bg-brand-500 text-white font-medium">
        View Openings
      </a>
    </div>
  </div>
</div>
```

## Expertise List

```html
<div class="space-y-5">
  <div class="flex items-start gap-4">
    <div class="w-2 h-2 rounded-full bg-violet-400 mt-2 flex-shrink-0"></div>
    <p class="text-neutral-400 text-sm leading-relaxed">
      AI/ML engineers, data scientists, and econometricians
    </p>
  </div>
  <div class="flex items-start gap-4">
    <div class="w-2 h-2 rounded-full bg-pink-400 mt-2 flex-shrink-0"></div>
    <p class="text-neutral-400 text-sm leading-relaxed">
      Oncologists, radiologists, surgeons
    </p>
  </div>
  <div class="flex items-start gap-4">
    <div class="w-2 h-2 rounded-full bg-emerald-400 mt-2 flex-shrink-0"></div>
    <p class="text-neutral-400 text-sm leading-relaxed">
      Bioinformaticians and omics experts
    </p>
  </div>
</div>
```

## Country/Location Badges

```html
<div class="flex flex-wrap gap-2.5">
  <span class="inline-flex items-center gap-2 rounded-full bg-white/[0.04] 
               border border-white/[0.08] px-4 py-2 text-sm text-neutral-300 
               hover:bg-white/[0.08] transition-colors">
    🇺🇸 United States
  </span>
  <span class="inline-flex items-center gap-2 rounded-full bg-white/[0.04] 
               border border-white/[0.08] px-4 py-2 text-sm text-neutral-300 
               hover:bg-white/[0.08] transition-colors">
    🇩🇪 Germany
  </span>
  <span class="inline-flex items-center gap-2 rounded-full bg-white/[0.04] 
               border border-white/[0.08] px-4 py-2 text-sm text-neutral-300 
               hover:bg-white/[0.08] transition-colors">
    🇯🇵 Japan
  </span>
</div>
```

## Hiring Badge

```html
<span class="inline-flex items-center gap-2 rounded-full 
             border border-emerald-500/30 bg-emerald-500/10 
             px-4 py-1.5 text-xs font-medium text-emerald-400">
  <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse"></span>
  Hiring in London & Tokyo
</span>
```

## Quote Block

```html
<blockquote class="relative pl-5 border-l-2 border-emerald-500/40">
  <p class="text-neutral-500 text-sm italic leading-relaxed">
    "Science knows no borders—and neither does our mission."
  </p>
</blockquote>
```

## Two-Column Layout

```html
<div class="mt-16 pt-16 border-t border-white/[0.06]">
  <div class="grid grid-cols-1 md:grid-cols-2 gap-12 lg:gap-16">
    <!-- Left: Team breakdown -->
    <div>
      <h3 class="text-xl font-medium text-white mb-8">Our Expertise</h3>
      <!-- Expertise list -->
    </div>
    
    <!-- Right: Global presence -->
    <div>
      <h3 class="text-xl font-medium text-white mb-8">Global Presence</h3>
      <!-- Country badges -->
    </div>
  </div>
</div>
```

## Icon Variants for Departments

```html
<!-- AI/ML: Violet -->
<div class="w-11 h-11 rounded-xl bg-violet-500/15"><svg class="text-violet-400">

<!-- Biology: Pink -->
<div class="w-11 h-11 rounded-xl bg-pink-500/15"><svg class="text-pink-400">

<!-- Clinical: Emerald -->
<div class="w-11 h-11 rounded-xl bg-emerald-500/15"><svg class="text-emerald-400">

<!-- Research: Purple -->
<div class="w-11 h-11 rounded-xl bg-purple-500/15"><svg class="text-purple-400">
```
