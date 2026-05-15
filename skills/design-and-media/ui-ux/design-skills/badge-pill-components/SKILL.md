---
name: Badge & Pill Components
description: Create status badges, category pills, and tag components
---

# Badge & Pill Components

Design consistent badge and pill components for status indicators, categories, and tags.

## Status Badge with Pulse

```html
<span class="inline-flex items-center gap-1.5 rounded-full 
             border border-brand-500/30 bg-brand-500/15 
             px-2.5 py-0.5 text-[11px] font-medium text-brand-300">
  <span class="w-1.5 h-1.5 rounded-full bg-brand-400 animate-pulse"></span>
  ACTIVE
</span>
```

## Category Eyebrow Badge

```html
<div class="inline-flex items-center gap-2 px-3 py-1.5 
            bg-brand-500/10 border border-brand-500/20 rounded-full">
  <div class="w-2 h-2 rounded-full bg-brand-400 animate-pulse"></div>
  <span class="text-xs font-semibold text-brand-300 uppercase tracking-wider">
    AI-Powered
  </span>
</div>
```

## Color Variants

### Success (Emerald)
```html
<span class="border border-emerald-500/30 bg-emerald-500/15 text-emerald-400">
  Success
</span>
```

### Warning (Amber)
```html
<span class="border border-amber-500/30 bg-amber-500/15 text-amber-400">
  Warning
</span>
```

### Error (Rose)
```html
<span class="border border-rose-500/30 bg-rose-500/15 text-rose-400">
  Error
</span>
```

### Info (Blue)
```html
<span class="border border-blue-500/30 bg-blue-500/15 text-blue-400">
  Info
</span>
```

## Compact Tags

```html
<div class="flex items-center gap-2">
  <span class="px-2 py-1 rounded-full bg-emerald-50/10 border border-emerald-500/20 
               text-[8px] font-bold text-emerald-400">HIPAA</span>
  <span class="px-2 py-1 rounded-full bg-blue-50/10 border border-blue-500/20 
               text-[8px] font-bold text-blue-400">GDPR</span>
  <span class="px-2 py-1 rounded-full bg-brand-50/10 border border-brand-500/20 
               text-[8px] font-bold text-brand-400">SOC2</span>
</div>
```

## Light Theme Badges

```html
<div class="inline-flex items-center gap-2 px-3 py-1.5 bg-brand-50 rounded-full">
  <div class="w-2 h-2 rounded-full bg-brand-500 animate-pulse"></div>
  <span class="text-[10px] font-semibold text-brand-700 uppercase tracking-wider">
    New Feature
  </span>
</div>
```

## Numeric Badge

```html
<span class="px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-mono">
  10,000+
</span>
```

## Version Badge

```html
<span class="px-2 py-1 rounded-md bg-zinc-800 border border-zinc-700 
             text-xs font-mono text-zinc-400">
  v2.4.1
</span>
```

## Badge Sizes

| Size | Padding | Text | Use Case |
|------|---------|------|----------|
| XS | `px-2 py-0.5` | `text-[8px]` | Compact tags |
| SM | `px-2.5 py-0.5` | `text-[11px]` | Standard inline |
| MD | `px-3 py-1` | `text-xs` | Prominent badges |
| LG | `px-4 py-1.5` | `text-sm` | Header badges |
