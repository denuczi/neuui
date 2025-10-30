# neuui — UI Surface Effects

A lightweight collection of CSS utilities for modern UI surface aesthetics.  
This repository provides two styling layers:

- `neuui.css` — Neumorphism utilities (global stylesheet, fully namespaced).
- `glassmorphism.module.css` — Glassmorphism utilities (CSS Module, locally scoped).

Both stylesheets are **layout-safe**: they do not modify padding, margin, layout flow, font properties, or text color.  
Their purpose is strictly visual—backgrounds, radii, borders, shadows, and reflective overlays.


## Overview

- Non-intrusive: No resets or global overrides.
- Safe for any project: No effect on spacing, layout, or content styling.
- Portable: Works with static HTML, PHP, React, Vite, Next.js, etc.
- Customizable: All key visual parameters use CSS variables.
- Collision-free:
  - `neuui.css` uses the `.neuui` namespace.
  - `glassmorphism.module.css` is module-scoped.



## Files

- `neuui.css` — Global stylesheet for Neumorphism surface effects.
- `glassmorphism.module.css` — CSS Module implementing Glassmorphism with reflection overlays.

Repository: **https://github.com/denuczi/neuui/**



## Installation

### Direct use
Download or clone the repository, then include:

html
<link rel="stylesheet" href="neuui.css">


For the glassmorphism module (CSS Module):

ts
import styles from "./glassmorphism.module.css";


### Using a bundler

Place the files anywhere in your project and import:

.ts
For global Neumorphism
import "./neuui.css";


.ts
// For component-level Glassmorphism
import styles from "./glassmorphism.module.css";


---

## Quick Start

### Neumorphism (global CSS)

html
<div class="neuui neuui--alto" style="width:240px;height:140px;">
  …
</div>


### Glassmorphism (CSS Module)

tsx
<div className={`${styles.glass} ${styles.solaris}`} style={{ width: 300, height: 160 }}>
  …
</div>


---

# Neumorphism (`neuui.css`)

A pure-CSS neumorphic system built around a single base class and several ready-to-use variants.

### Base class

html
<div class="neuui"></div>


Variants extend the base:

<div class="neuui neuui--sutil"></div>


---

## Variants

| Class           | Description                                    |
| ----------------| ---------------------------------------------- |
| neuui--alto     | Large radius, soft deep shadows, light surface |
| neuui--sutil    | Compact shadows, subtle appearance             |
| neuui--nocturno | Dark mode neumorphism with high contrast       |
| neuui--claro    | Light surface with crossed shadows             |
| neuui--pastilla | Pill-style rounded shape                       |
| neuui--grafito  | Dark graphite surface with strong contrast     |
| neuui--cielo    | Cool cyan-tinted soft surface                  |
| neuui--pizarra  | Slate-style compact dark surface               |

---

## Examples

<div class="neuui neuui--grafito" style="width:200px;height:120px;"></div>
<div class="neuui neuui--pastilla" style="width:260px;height:80px;"></div>
<div class="neuui neuui--claro" style="width:220px;height:160px;"></div>

---

## Customization

Override variables on the element:

<div
  class="neuui neuui--sutil"
  style="
    --neuui-radius: 24px;
    --neuui-bg: #ececec;
    --neuui-shadow-1: 6px 6px 14px rgba(0,0,0,.08);
    --neuui-shadow-2: -6px -6px 14px rgba(255,255,255,.45);
  "
></div>

---

# Glassmorphism (`glassmorphism.module.css`)

A modular, reflection-enhanced glassmorphism system.
Uses backdrop blur, saturation, translucent backgrounds, and two overlay gradients (`::before`, `::after`) for realism.

### Usage

tsx
import styles from "./glassmorphism.module.css";

<div className={`${styles.glass} ${styles.cosmic}`}>
  …
</div>

---

## Variants

| Class    | Description                                         |
| ---------| --------------------------------------------------- |
| amethyst | Heavy blur, low saturation, thick border, deep glow |
| solaris  | Medium blur, warm/neutral tone, balanced shadowing  |
| cosmic   | Light blur, warm tint, subtle inner glow            |

---

## Examples

tsx
<div className={`${styles.glass} ${styles.amethyst}`} style={{ height: 200 }} />
<div className={`${styles.glass} ${styles.solaris}`} style={{ width: 260, height: 140 }} />
<div className={`${styles.glass} ${styles.cosmic}`} style={{ borderRadius: 20 }} />

---

## Customization

CSS variables may be overridden inline:

tsx
<div
  className={`${styles.glass} ${styles.solaris}`}
  style={{
    ["--glass-radius"]: "30px",
    ["--glass-blur"]: "blur(20px)",
    ["--glass-saturate"]: "saturate(160%)",
    ["--glass-bg"]: "rgba(255,255,255,0.12)",
  }}
>
  …
</div>

---


## Performance

* Neumorphism shadows are lightweight but can add up on large lists.
* Glassmorphism uses `backdrop-filter`, which is GPU-intensive on large surfaces.

  * Keep surfaces moderate in size.
  * Avoid animating blur or saturation.
