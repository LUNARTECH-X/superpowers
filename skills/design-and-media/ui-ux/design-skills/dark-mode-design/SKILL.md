---
name: Dark Mode Design
description: Design premium dark interfaces with proper contrast, color palettes, and visual hierarchy
---

# Dark Mode Design

Create sophisticated dark-themed interfaces with proper contrast and premium visual hierarchy.

## Background Hierarchy

```css
/* Tailwind Dark Backgrounds */
bg-zinc-950     /* #09090b - Base/page */
bg-neutral-900  /* #171717 - Cards */
bg-zinc-800     /* #27272a - Elevated */
bg-neutral-900/50  /* Transparent cards */
```

## Text Hierarchy

| Purpose | Class | Use Case |
|---------|-------|----------|
| Primary | `text-white` | Titles, headings |
| Secondary | `text-white/70` | Body text |
| Tertiary | `text-white/50` | Labels, captions |
| Muted | `text-white/40` | Metadata |

## Border Colors

```html
<div class="border border-white/10">Subtle</div>
<div class="border border-white/20">Visible</div>
<div class="hover:border-white/20">Hover enhanced</div>
```

## Card Patterns

```html
<!-- Standard dark card -->
<div class="rounded-2xl border border-white/10 bg-neutral-900/50 p-6">

<!-- Elevated glass card -->
<div class="rounded-2xl border border-white/10 bg-neutral-900/50 backdrop-blur-md
            hover:bg-neutral-800/50 hover:shadow-2xl hover:shadow-brand-500/10">
```

## Status Colors

```html
<!-- Success -->
<span class="bg-emerald-500/15 border border-emerald-500/30 text-emerald-400">

<!-- Warning -->
<span class="bg-amber-500/15 border border-amber-500/30 text-amber-400">

<!-- Error -->
<span class="bg-rose-500/15 border border-rose-500/30 text-rose-400">
```

## Icon Backgrounds

```html
<div class="w-11 h-11 rounded-xl bg-violet-500/15 flex items-center justify-center
            group-hover:bg-violet-500/25">
  <svg class="text-violet-400"><!-- Icon --></svg>
</div>
```

## Decorative Elements

```html
<!-- Gradient blobs -->
<div class="absolute w-96 h-96 bg-brand-500/10 rounded-full blur-[120px] animate-pulse">

<!-- Dot pattern -->
<div style="background-image: radial-gradient(circle at 1px 1px, white 1px, transparent 0); 
            background-size: 40px 40px;" class="opacity-[0.03]">
```

## Best Practices

1. ✅ Use `zinc-950` for base, layer lighter surfaces on top
2. ✅ Use 70% opacity for body text
3. ✅ Add subtle borders (`border-white/10`)
4. ✅ Use colored glows instead of black shadows
5. ❌ Don't use pure black (`#000000`)
6. ❌ Don't use pure white for all text
