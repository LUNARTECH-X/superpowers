---
name: brand-identity
description: Provides the single source of truth for brand guidelines, design tokens, technology choices, and voice/tone. Use this skill whenever generating UI components, styling applications, writing copy, or creating user-facing assets to ensure brand consistency.
---

# Brand Identity & Guidelines

> **Instructions:** Copy this template and fill in all `{{PLACEHOLDER}}` values with your brand's specifics. Delete this instruction block when done.

**Brand Name:** {{BRAND_NAME}}
**Tagline:** {{BRAND_TAGLINE}}

This skill defines the core constraints for visual design and technical implementation. Adhere to these guidelines strictly to maintain brand consistency.

---

## Design Tokens

### Colors

| Token | Value | Usage |
|-------|-------|-------|
| **Primary** | `{{PRIMARY_COLOR}}` | Main brand color |
| Primary Hover | `{{PRIMARY_HOVER}}` | Hover state |
| Primary Foreground | `{{PRIMARY_FOREGROUND}}` | Text on primary |
| **Secondary** | `{{SECONDARY_COLOR}}` | Secondary elements |
| Secondary Foreground | `{{SECONDARY_FOREGROUND}}` | Text on secondary |
| **Background** | `{{BACKGROUND_COLOR}}` | Page background |
| **Foreground** | `{{FOREGROUND_COLOR}}` | Default text |
| **Muted** | `{{MUTED_COLOR}}` | Muted backgrounds |
| **Accent** | `{{ACCENT_COLOR}}` | Accent elements |
| **Destructive** | `{{DESTRUCTIVE_COLOR}}` | Error/danger actions |
| **Success** | `{{SUCCESS_COLOR}}` | Success states |

### Typography

| Property | Value |
|----------|-------|
| Headings Font | `{{HEADING_FONT}}`, sans-serif |
| Body Font | `{{BODY_FONT}}`, sans-serif |
| Bold Weight | `{{BOLD_WEIGHT}}` |
| Normal Weight | `{{NORMAL_WEIGHT}}` |

### UI Measurements

| Property | Value |
|----------|-------|
| Border Radius (default) | `{{BORDER_RADIUS}}` |
| Border Radius (small) | `{{BORDER_RADIUS_SM}}` |
| Spacing Base Unit | `{{SPACING_UNIT}}` |

---

## Tech Stack & Implementation Rules

### Core Stack

| Category | Technology |
|----------|------------|
| Framework | {{FRAMEWORK}} |
| Styling | {{STYLING_ENGINE}} |
| Components | {{COMPONENT_LIBRARY}} |
| Icons | {{ICON_LIBRARY}} |

### Implementation Guidelines

#### Styling Usage
{{STYLING_RULES}}

#### Component Patterns
- **Buttons:** {{BUTTON_PATTERN}}
- **Forms:** {{FORM_PATTERN}}
- **Layout:** {{LAYOUT_PATTERN}}

#### Forbidden Patterns
{{FORBIDDEN_PATTERNS}}

---

## Voice & Tone Guidelines

### Brand Personality
{{PERSONALITY_KEYWORDS}}

### Grammar & Mechanics

| Rule | Guideline |
|------|-----------|
| Headings | {{HEADING_STYLE}} |
| Punctuation | {{PUNCTUATION_RULES}} |
| Voice | {{VOICE_PREFERENCE}} |
| Sentences | {{SENTENCE_STYLE}} |

### Terminology Guide

| ❌ Do Not Use | ✅ Use Instead |
|---------------|----------------|
| {{AVOID_TERM_1}} | {{PREFER_TERM_1}} |
| {{AVOID_TERM_2}} | {{PREFER_TERM_2}} |
| {{AVOID_TERM_3}} | {{PREFER_TERM_3}} |

---

## Quick Reference Defaults

> Use these if no specific brand values are provided:

```json
{
  "colors": {
    "primary": "#000000",
    "primary_hover": "#333333",
    "primary_foreground": "#FFFFFF",
    "secondary": "#F4F4F5",
    "secondary_foreground": "#18181B",
    "background": "#FFFFFF",
    "foreground": "#09090B",
    "muted": "#F4F4F5",
    "accent": "#F4F4F5",
    "destructive": "#EF4444",
    "success": "#10B981"
  },
  "typography": {
    "headings": "Inter",
    "body": "Roboto",
    "bold": "700",
    "normal": "400"
  },
  "ui": {
    "border_radius": "0.5rem",
    "border_radius_sm": "0.25rem",
    "spacing_unit": "4px"
  },
  "stack": {
    "framework": "React (TypeScript)",
    "styling": "Tailwind CSS",
    "components": "shadcn/ui",
    "icons": "Lucide React"
  }
}
```
