---
name: svg-icon-system
description: Create, optimize, and standardize SVG icons for web and cross-platform use. Use this when building icon libraries, design systems, or replacing icon packs like Font Awesome, Heroicons, or Material Icons.
license: MIT
metadata:
  author: your-org
  version: "1.0.0"
  category: design-system
  tags: svg, icons, ui, frontend, design-system, accessibility
compatibility: Web (HTML, CSS, JS), React, Vue, Svelte, Angular, React Native (via react-native-svg), Flutter (via conversion tools), Figma workflows
---

# SVG Icon System Skill

## Purpose

This skill provides a structured system for creating a scalable, consistent, and production-ready SVG icon library. It is designed to compete with established libraries by enforcing strict visual, technical, and accessibility standards.

Use this skill when:
- Building an icon library from scratch
- Replacing or improving existing icon systems
- Standardizing inconsistent icon assets
- Creating icons for cross-platform design systems

---

## Core Principles

### 1. Consistency First
- All icons must visually belong to the same family
- Maintain identical proportions, stroke styles, and spacing rules
- Avoid stylistic drift between contributors

### 2. Grid Discipline
- Default viewport: `24x24`
- Safe padding: `2px` on all sides
- Align strokes and anchor points to pixel grid
- Avoid subpixel rendering issues

### 3. Simplicity
- Use the minimum number of paths
- Avoid unnecessary detail
- Ensure clarity at small sizes (16px minimum)

### 4. Scalability
- Icons must work at multiple sizes (16, 20, 24, 32, 48)
- No loss of readability when scaled

---

## Visual Specifications

### Viewport
- Default: `0 0 24 24`
- Maintain proportional scaling for other sizes

### Stroke System
- Stroke width: `1.5` or `2` (choose one globally)
- `stroke-linecap`: `round`
- `stroke-linejoin`: `round`

### Fill Rules
- Outline icons: `fill="none"`
- Filled icons: `fill="currentColor"`
- Duotone: use opacity or secondary paths

### Corner Radius
- Maintain consistent rounding across all icons
- Avoid mixing sharp and rounded styles unless intentional

---

## Supported Icon Styles

Each icon should support consistent variants:

### 1. Outline
- Stroke-based
- Default style

### 2. Filled
- Solid shapes
- Same silhouette as outline

### 3. Duotone (Optional)
- Two-tone color using opacity or layered paths

### 4. Rounded (Optional Variant)
- Softer geometry
- Same base structure

---

## SVG Authoring Rules

### Base Template

```xml
<svg
  xmlns="http://www.w3.org/2000/svg"
  viewBox="0 0 24 24"
  fill="none"
  stroke="currentColor"
>
````

### Rules

* Use `currentColor` for all strokes/fills unless explicitly required
* Do NOT include:

  * inline styles
  * embedded CSS
  * hardcoded colors
* Do NOT define `width` and `height` inside SVG
* Use `stroke` for outline icons instead of filled paths where possible
* Combine paths when it reduces complexity without harming clarity
* Limit decimal precision to 2–3 places

---

## Naming Conventions

### Format

* Use `kebab-case`
* Examples:

  * `arrow-left`
  * `user-circle`
  * `file-download`

### Guidelines

* Prefer semantic naming over visual description

  * ✅ `download`
  * ❌ `arrow-down-line`
* Avoid synonyms across the library
* Use consistent prefixes when needed:

  * `nav-` (navigation)
  * `media-` (media controls)
  * `file-` (documents)

---

## File Organization

```
icons/
├── outline/
├── filled/
├── duotone/
├── rounded/
```

Each icon:

```
icons/outline/arrow-left.svg
icons/filled/arrow-left.svg
```

---

## Optimization Workflow

### Step-by-step

1. Remove metadata (e.g., editor info)
2. Collapse groups where unnecessary
3. Merge paths when possible
4. Reduce decimal precision (2–3 max)
5. Normalize transforms
6. Run SVGO (or equivalent)
7. Validate visually after optimization

### Target

* File size: ideally < 2KB per icon
* Clean, human-readable SVG

---

## Accessibility

### Decorative Icons

```html
<svg aria-hidden="true">
```

### Informative Icons

```html
<svg role="img">
  <title>Download</title>
</svg>
```

### Rules

* Always provide meaning if icon conveys information
* Ensure sufficient contrast in UI usage
* Avoid relying solely on icons without labels

---

## Platform Integration

### Web (Recommended)

* Inline SVG usage
* Styled via CSS
* Supports theming via `color`

### React Example

```jsx
export const IconArrowLeft = (props) => (
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" {...props}>
    <path d="M15 18l-6-6 6-6" />
  </svg>
);
```

### Vue Example

```vue
<template>
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
    <path d="M15 18l-6-6 6-6" />
  </svg>
</template>
```

### React Native

* Use `react-native-svg`
* Convert paths directly

### Flutter

* Convert SVG paths using tools like `flutter_svg`

---

## Icon Creation Workflow

1. Define icon meaning (semantic intent)
2. Sketch on 24x24 grid
3. Align key shapes to grid
4. Draw SVG paths
5. Apply stroke/fill rules
6. Compare with existing icons for consistency
7. Optimize SVG
8. Export variants (outline, filled, etc.)
9. Validate at multiple sizes

---

## Quality Checklist

Before finalizing any icon:

* [ ] Fits 24x24 grid correctly
* [ ] Maintains 2px safe padding
* [ ] Stroke width is consistent
* [ ] Pixel-aligned paths
* [ ] Matches existing icon style
* [ ] Minimal path complexity
* [ ] Optimized SVG output
* [ ] Accessible where required
* [ ] Correct naming convention
* [ ] Works at 16px size

---

## Versioning Strategy

Use Semantic Versioning:

* PATCH: minor fixes (alignment, optimization)
* MINOR: new icons added
* MAJOR: breaking visual changes to existing icons

---

## Performance Guidelines

* Prefer inline SVG over icon fonts
* Avoid loading entire libraries when not needed
* Enable tree-shaking in frameworks
* Bundle icons individually or per category

---

## Anti-Patterns

Avoid the following:

* Mixing multiple stroke widths in one icon
* Using colors other than `currentColor`
* Overly complex paths
* Inconsistent padding or alignment
* Icons that rely on context to be understood
* Raster-based exports (PNG as source)

---

## When NOT to Use This Skill

* Detailed illustrations
* Multi-color artwork systems
* Photographic or raster assets
* 3D icon systems

---

## Optional Enhancements

### Automation

* SVGO pipeline integration
* CLI for generating components
* Batch export scripts

### Design Tool Integration

* Figma templates with grid and guides
* Export presets for SVG

### Theming Support

* Light/dark mode compatibility
* Token-based sizing and stroke systems

---

## References

* SVG best practices
* Accessibility (ARIA for SVG)
* Design system principles
* Existing libraries (Heroicons, Material Icons, Feather Icons)

---

```
