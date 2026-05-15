---
name: Timeline & Process Flows
description: Visualize step-by-step processes and progressive workflows
---

# Timeline & Process Flows

Create visual representations of sequential processes, timelines, and progressive workflows.

## Horizontal Step Flow

```html
<div class="flex items-center justify-between gap-4">
  <!-- Step 1 -->
  <div class="flex-1 text-center group-hover:translate-y-[-4px] transition-transform duration-300">
    <div class="w-14 h-14 mx-auto rounded-2xl bg-emerald-50 border border-emerald-100 
                flex items-center justify-center mb-2 
                group-hover:scale-110 transition-transform duration-300">
      <svg class="w-6 h-6 text-emerald-600"><!-- Icon --></svg>
    </div>
    <p class="text-[10px] font-semibold text-zinc-700">Step Name</p>
    <p class="text-[9px] text-zinc-400">Subtitle</p>
  </div>
  
  <!-- Arrow -->
  <div class="flex-shrink-0">
    <svg class="w-5 h-5 text-zinc-300">
      <path d="M5 12h14m-7-7 7 7-7 7" />
    </svg>
  </div>
  
  <!-- Step 2 -->
  <div class="flex-1 text-center group-hover:translate-y-[-4px] transition-transform duration-300 delay-100">
    <!-- Similar structure -->
  </div>
  
  <!-- Arrow -->
  <!-- Step 3, etc. -->
</div>
```

## Staggered Animation

Add delays to each step for sequential reveal:

```html
<div class="transition-transform duration-300">Step 1</div>
<div class="transition-transform duration-300 delay-100">Step 2</div>
<div class="transition-transform duration-300 delay-200">Step 3</div>
<div class="transition-transform duration-300 delay-300">Step 4</div>
```

## Vertical Timeline

```html
<div class="space-y-6">
  <div class="flex items-start gap-4">
    <div class="flex flex-col items-center">
      <div class="w-10 h-10 rounded-full bg-brand-500 flex items-center justify-center">
        <span class="text-white font-medium">1</span>
      </div>
      <div class="w-0.5 h-full bg-white/10 my-2"></div>
    </div>
    <div class="pb-8">
      <h4 class="text-white font-medium">Step Title</h4>
      <p class="text-white/60 text-sm">Description of this step.</p>
    </div>
  </div>
  <!-- More steps -->
</div>
```

## Icon Color by Stage

```html
<!-- Early stage: Emerald -->
<div class="bg-emerald-50 border-emerald-100">
  <svg class="text-emerald-600">

<!-- Mid stage: Blue -->
<div class="bg-blue-50 border-blue-100">
  <svg class="text-blue-600">

<!-- Late stage: Amber -->
<div class="bg-amber-50 border-amber-100">
  <svg class="text-amber-600">

<!-- Final stage: Rose -->
<div class="bg-rose-50 border-rose-100">
  <svg class="text-rose-600">
```

## Data Flow Visualization

```html
<div class="space-y-4">
  <!-- Input -->
  <div class="flex items-center gap-4">
    <span class="w-20 text-right text-white/30 text-xs font-mono">INPUT</span>
    <div class="flex-1 flex gap-2">
      <div class="flex-1 h-10 rounded-lg bg-blue-500/20 border border-blue-500/30 
                  flex items-center justify-center">
        <span class="text-blue-400 text-xs">Data A</span>
      </div>
      <div class="flex-1 h-10 rounded-lg bg-emerald-500/20 border border-emerald-500/30 
                  flex items-center justify-center">
        <span class="text-emerald-400 text-xs">Data B</span>
      </div>
    </div>
  </div>
  
  <!-- Arrow -->
  <div class="flex justify-center">
    <svg class="text-brand-400 animate-bounce">
      <path d="M12 5v14m7-7-7 7-7-7" />
    </svg>
  </div>
  
  <!-- Process -->
  <div class="flex items-center gap-4">
    <span class="w-20 text-right text-white/30 text-xs font-mono">PROCESS</span>
    <div class="flex-1 h-16 rounded-xl bg-gradient-to-r from-brand-500/20 to-purple-500/20 
                border border-brand-500/30 flex items-center justify-center">
      <span class="text-brand-300 font-medium">Processing Step</span>
    </div>
  </div>
  
  <!-- Arrow -->
  <div class="flex justify-center">
    <svg class="text-emerald-400 animate-bounce" style="animation-delay: 0.5s;">
      <path d="M12 5v14m7-7-7 7-7-7" />
    </svg>
  </div>
  
  <!-- Output -->
  <div class="flex items-center gap-4">
    <span class="w-20 text-right text-white/30 text-xs font-mono">OUTPUT</span>
    <div class="flex-1 h-14 rounded-xl bg-emerald-500/10 border border-emerald-500/30 
                flex items-center justify-center gap-3">
      <svg class="text-emerald-400"><!-- Check icon --></svg>
      <span class="text-emerald-300 font-medium">Result</span>
    </div>
  </div>
</div>
```

## Shimmer Loading Effect

```html
<div class="relative overflow-hidden">
  <div class="absolute inset-0 bg-gradient-to-r from-transparent via-white/5 to-transparent"
       style="animation: shimmer 2s infinite;"></div>
</div>

<style>
@keyframes shimmer {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}
</style>
```
