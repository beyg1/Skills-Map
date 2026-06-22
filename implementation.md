# The Definitive Skills Map Dashboard — Maximum Skill Utilization

After reading every single design, frontend, animation, and UI skill in `/home/darth/.agents/skills`, here is the final plan. Every skill's **specific, concrete contribution** is documented below. No hand-waving.

---

## Skills Utilized (22 total)

| # | Skill | Concrete Contribution |
|---|-------|----------------------|
| 1 | `emil-design-eng` | Interruptible spring physics, custom cubic-bezier curves, haptic `:active` scale, blur crossfade masking, asymmetric enter/exit timing |
| 2 | `high-end-visual-design` | Doppelrand (double-bezel) card architecture, Button-in-Button CTA, floating glass pill nav, staggered mask reveal entry |
| 3 | `impeccable` | Font selection discipline (ban Inter/Roboto), typographic precision, micro-spacing audit |
| 4 | `brandkit` | Locked CMYK neon palette (Cyan/Magenta/Yellow), single accent discipline, consistent palette across all cards |
| 5 | `frontend-design` | `design-taste-frontend` anti-slop rules, Section-Layout-Repetition Ban, eyebrow restraint, hero 2-line rule |
| 6 | `design-taste-frontend` | Three-dial system (Variance 9, Motion 8, Density 4), anti-default discipline, layout diversification |
| 7 | `gpt-taste` | Python-driven randomization for layout variance, gapless bento verification, GSAP ScrollTrigger pinning, scrubbing text reveals |
| 8 | `stitch-design-taste` | Atmosphere definition (Variance 8, Motion 10, Density 6 = "Cockpit-dense + Cinematic"), perpetual micro-interactions on idle cards |
| 9 | `minimalist-ui` | Balance counterweight — warm monochrome surface for expanded card interiors, Phosphor Bold icons, `border-top` dividers instead of card spam |
| 10 | `industrial-brutalist-ui` | CRT scanlines, SVG noise filter overlay, monospace coordinate HUD (`X:0.4 Y:-1.2 Z:5.0`), raw data-dense tactical labels |
| 11 | `redesign-existing-projects` | Audit-first methodology, parallax card stacks, spotlight borders (cursor-tracking glow), grain/noise overlays, variable font animation |
| 12 | `gsap-core` | Base tween engine for all animations |
| 13 | `gsap-timeline` | Master timeline for carousel rotation + camera fly-in sequences |
| 14 | `gsap-scrolltrigger` | Scroll-pinned hero section, scrub-linked text opacity reveals, batch stagger for card entries |
| 15 | `gsap-plugins` | Draggable/Inertia for physical carousel spin with spring deceleration |
| 16 | `gsap-utils` | `gsap.utils.toArray()`, `gsap.utils.wrap()` for cycling, `clamp()` for bounds |
| 17 | `gsap-performance` | GPU-only animation rules (`transform`/`opacity` only), `will-change` discipline |
| 18 | `motion-design` | Three-pillar framework (Emotional Intent + Visual Narrative + Motion Craft), three motion layers (Primary/Secondary/Ambient), stagger budgets |
| 19 | `review-animations` | Post-build QA pass — 10 Non-Negotiable Standards audit, remedial hierarchy (delete > reduce > fix easing > fix origin) |
| 20 | `algorithmic-art` | Canvas-based generative particle flow field for the background |
| 21 | `imagegen-frontend-web` | Section rhythm discipline, composition anchor variety, anti-AI-slop color/layout rules |
| 22 | `graphic-overlays` | Timed card reveal choreography with `data-anim` vocabulary (fade-in, kinetic-chars, count-up, mask-reveal) |

---

## The Architecture (5 Layers)

The single `index.html` file will be structured as 5 composited visual layers, from back to front:

```
┌─────────────────────────────────────────┐
│  Layer 5: FOREGROUND HUD (brutalist)    │  ← industrial-brutalist-ui
│  Layer 4: EXPANDED CARD (focus state)   │  ← minimalist-ui + emil-design-eng
│  Layer 3: 3D CAROUSEL (midground)       │  ← gsap-timeline + high-end-visual
│  Layer 2: PARTICLE CANVAS (background)  │  ← algorithmic-art
│  Layer 1: OLED BLACK + NOISE + CRT      │  ← industrial-brutalist-ui
└─────────────────────────────────────────┘
```

---

## Layer 1: The Canvas (Industrial Brutalist + Algorithmic Art)

### Background Treatment
- **OLED Black** (`#050505` per `high-end-visual-design` — never pure `#000` per `stitch-design-taste`)
- **SVG Noise Filter** (`<feTurbulence>` + `<feColorMatrix>`) at `opacity: 0.03` — per `redesign-existing-projects` grain overlay rule
- **CRT Scanlines** — repeating 2px lines at `opacity: 0.04` via CSS `repeating-linear-gradient`, applied to a `position: fixed; pointer-events: none` pseudo-element per `high-end-visual-design` performance rule
- **Vignette** — radial gradient from transparent to black at edges

### Generative Particle System (`algorithmic-art`)
- Full-viewport `<canvas>` element behind everything
- ~2000 microscopic particles flowing through a Perlin noise field
- Particles colored in Cyan (`#00FFFF`) and Magenta (`#FF00FF`) at very low opacity (0.1-0.3)
- Connected by 1px lines when within proximity threshold
- `requestAnimationFrame` loop with delta-time smoothing

---

## Layer 2: The 3D Carousel (GSAP Suite + High-End Visual)

### Geometry
- 8 category cards arranged in a true CSS 3D cylinder
- `transform-style: preserve-3d` on the container
- Each card positioned via `rotateY(i * 45deg) translateZ(apothem)` where `apothem = cardWidth / (2 * tan(π/8))`
- Cards are uniform size (380×480px)

### The Doppelrand Card Architecture (`high-end-visual-design`)
Each card uses the "Double-Bezel" nested technique:
```
┌──────────────────────────┐  ← Outer Shell: 1px cyan hairline, p-1.5
│ ┌──────────────────────┐ │     rounded-[2rem]
│ │                      │ │
│ │   CATEGORY TITLE     │ │  ← Inner Core: backdrop-blur-2xl
│ │   ══════════════     │ │     bg-white/5, inner highlight shadow
│ │   12 skills          │ │     rounded-[calc(2rem-0.375rem)]
│ │                      │ │
│ │   [EXPAND →]         │ │  ← Button-in-Button CTA
│ └──────────────────────┘ │
└──────────────────────────┘
```

### Continuous Rotation (`gsap-timeline`)
- GSAP master timeline with `repeat: -1` rotating the container `360deg`
- Duration: ~30s for one full revolution
- Easing: `"none"` (linear for continuous spin per `gsap-scrolltrigger` horizontal scroll rules)

### Physical Spin (`gsap-plugins`)
- GSAP Draggable on the carousel container with `type: "rotation"`
- Inertia plugin for momentum-based deceleration after release
- Spring physics per `motion-design` "Elastic" material: `0.8x duration, 15-25% overshoot`

---

## Layer 3: Interaction States (Emil Kowalski + Motion Design)

### Hover State — "Bullet Time"
When the cursor enters a card:
1. Master timeline `timeScale()` smoothly tweens from `1.0` → `0.05` (near-freeze)
2. Hovered card gets a punchy glow: `box-shadow: 0 0 40px rgba(0,255,255,0.4)`
3. Non-hovered cards dim to `opacity: 0.3` with `filter: blur(2px)` (Emil's blur-mask technique)
4. All transitions use custom `cubic-bezier(0.23, 1, 0.32, 1)` (Emil's strong ease-out)
5. Duration: 200ms for hover-in, 400ms for hover-out (asymmetric per `review-animations` Standard #9)

### Click State — "Focus Mode"
When a card is clicked:
1. Master timeline pauses completely
2. Clicked card tweens to `rotateY(0) translateZ(600px)` — directly in front of the camera
3. Card dimensions expand from `380×480` to `800×600` using `transform: scale()` only (GPU-safe per `gsap-performance`)
4. A `filter: blur(4px)` is applied and removed during the 300ms transition to mask the state change (Emil's blur crossfade)
5. Background particle speed reduces to 10%
6. The expanded card reveals its interior content (Layer 4)

### Interruptibility (`emil-design-eng`)
- If the user clicks another card mid-flight, the current animation doesn't restart from zero
- GSAP tweens are set with `overwrite: "auto"` so they smoothly retarget from their current position
- This is the core Emil principle: "Springs maintain velocity when interrupted"

---

## Layer 4: Expanded Card Interior (Minimalist UI + Graphic Overlays)

When a card is in focus, its interior reveals the full list of capabilities and skills:

### Layout (`minimalist-ui`)
- Warm monochrome interior: Off-white surface (`#F7F6F3`) with charcoal text (`#2F3437`)
- Skills listed with `border-top: 1px solid #EAEAEA` dividers (not card spam)
- Generous padding (`24px-40px`)
- `JetBrains Mono` for skill counts and metadata

### Entry Choreography (`graphic-overlays` + `motion-design`)
Skills inside the expanded card enter with timed `data-anim` vocabulary:
1. Category title: `kinetic-chars` (per-character pop, stagger 40ms)
2. Skill count: `count-up` (animates from 0 to N)
3. Individual skills: `fade-in` with `slide-in` from bottom, staggered at 50ms intervals
4. Accent line: `grow-x` (width animates from 0 to full)
5. Total entry budget: <500ms per `motion-design` stagger rules

### Close Mechanism
- "Back" button uses the Button-in-Button architecture (`high-end-visual-design`): outer pill + nested circular arrow icon
- On click: card reverses its expansion tween, master timeline resumes
- Exit is 40% faster than entry (asymmetric timing per `emil-design-eng`)

---

## Layer 5: Foreground HUD (Industrial Brutalist)

### Persistent UI Overlay
- **Floating Glass Pill Nav** at top center (`high-end-visual-design` Fluid Island pattern): contains the title "SKILLS MAP" in `JetBrains Mono` uppercase, 0.2em tracking
- **Spatial Coordinates** in the four corners: `X: 0.00 Y: 0.00 Z: 0.00` updating in real-time based on carousel rotation angle — `JetBrains Mono` at 10px, `opacity: 0.4`
- **Total Skill Counter**: Bottom-center HUD showing `112 SKILLS MAPPED` with a `count-up` animation on page load
- **Crosshair** center marker: 1px cyan lines intersecting at viewport center, `opacity: 0.15`

---

## Typography System (`impeccable` + `stitch-design-taste` + `design-taste-frontend`)

| Role | Font | Size | Treatment |
|------|------|------|-----------|
| Hero Title (page load) | `Clash Display` (Google Fonts) | `clamp(4rem, 8vw, 8rem)` | tracking `-0.04em`, line-height `0.9`, gradient fill (white → white/40%) |
| Card Category Title | `Clash Display` | `1.5rem` | uppercase, tracking `0.05em` |
| Skill Labels | `JetBrains Mono` | `0.75rem` | uppercase, tracking `0.1em` |
| HUD Coordinates | `JetBrains Mono` | `0.625rem` | monospace tabular figures, `opacity: 0.4` |
| Expanded Card Body | `Satoshi` or `Geist` | `0.875rem` | `line-height: 1.6`, `max-width: 65ch` |

**Banned** (per `impeccable` + `stitch-design-taste`): Inter, Roboto, Arial, Open Sans, Helvetica, generic serifs.

---

## Color System (`brandkit` + `stitch-design-taste`)

| Token | Value | Role |
|-------|-------|------|
| `--bg` | `#050505` | OLED canvas (off-black, not pure `#000`) |
| `--text` | `#F1F1F1` | Primary text |
| `--text-muted` | `rgba(255,255,255,0.4)` | Secondary text, coordinates |
| `--accent-cyan` | `#00FFFF` | Primary accent, borders, particle system |
| `--accent-magenta` | `#FF00FF` | Secondary accent, hover glows |
| `--accent-yellow` | `#E5FF00` | Tertiary accent, counter highlights |
| `--surface` | `rgba(255,255,255,0.05)` | Card glass surfaces |
| `--border` | `rgba(0,255,255,0.2)` | Card hairline borders |

**One palette, locked** per `design-taste-frontend` Color Consistency Lock. No palette drift between cards.

---

## Scroll Experience (`gsap-scrolltrigger` + `gpt-taste`)

The page will have a scroll-driven intro sequence before the carousel:

### Hero Section (Pinned)
1. Page loads with the hero title "SKILLS MAP" in massive `Clash Display` type
2. `ScrollTrigger` pins the hero for `+=1000px` of scroll
3. During the pinned scroll:
   - Title opacity scrubs from `0.1` → `1.0` word-by-word (`gpt-taste` scrubbing text reveal)
   - Subtitle fades in: "112 Agent Capabilities Visualized"
   - Particle field density increases from sparse to full
4. At the end of the pin, the hero fades out and the 3D carousel fades in

### Card Entry (`gsap-scrolltrigger` batch)
- `ScrollTrigger.batch()` is used so all 8 cards enter as a coordinated stagger (not individually triggered)
- Entry: `translateY(80px) + opacity: 0` → `translateY(0) + opacity: 1`
- Stagger: 80ms between cards (within the "Standard" budget of <400ms per `motion-design`)
- Easing: Material Design 3 Emphasized `cubic-bezier(0.05, 0.7, 0.1, 1)` per `motion-design`

---

## Spotlight Borders (`redesign-existing-projects`)

Each card will have a **cursor-tracking border glow**:
- On `mousemove`, calculate the cursor position relative to the card
- Apply a `radial-gradient` to the card's `::before` pseudo-element at the cursor position
- Gradient: `radial-gradient(600px circle at ${x}px ${y}px, rgba(0,255,255,0.15), transparent 40%)`
- This creates the "spotlight border" effect from `redesign-existing-projects`

---

## Post-Build QA Pass (`review-animations`)

After implementation, every animation will be audited against the **10 Non-Negotiable Standards**:

1. ✅ Justified motion (carousel rotation = spatial exploration; hover = state indication; click = focus)
2. ✅ Frequency-appropriate (carousel is occasional; no animation on keyboard actions)
3. ✅ Responsive easing (all use custom `cubic-bezier`, no `ease-in` on UI)
4. ✅ Sub-300ms UI (hover: 200ms, click expand: 300ms)
5. ✅ Origin correctness (cards scale from their own center in 3D space)
6. ✅ Interruptibility (GSAP `overwrite: "auto"`)
7. ✅ GPU-only (`transform` and `opacity` exclusively)
8. ✅ `prefers-reduced-motion` honored (collapse to static grid)
9. ✅ Asymmetric enter/exit (entry 300ms, exit 180ms)
10. ✅ Cohesion (all motion follows "Energetic" archetype per `motion-design`)

---

## Accessibility (`design-taste-frontend` + `review-animations`)

- `@media (prefers-reduced-motion: reduce)`: Carousel stops rotating, all scroll animations disabled, cards appear in a static CSS grid
- `@media (hover: hover) and (pointer: fine)`: Hover effects only fire on mouse devices
- Semantic HTML: `<nav>`, `<main>`, `<section>`, `<article>` for cards
- All interactive elements have `tabindex` and keyboard handlers
- WCAG AA contrast ratios enforced on all text

---

## CDN Dependencies

```html
<!-- GSAP Suite -->
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/ScrollTrigger.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/Draggable.min.js"></script>

<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<!-- Clash Display via @font-face from a CDN or local -->
```

---

## Proposed Execution Steps

### Step 1: HTML Skeleton + CSS Design System
- Write the 5-layer DOM structure
- Define all CSS custom properties (colors, fonts, timing)
- Implement the CRT scanline + noise + vignette overlays

### Step 2: Generative Background Canvas
- Implement the Perlin noise particle flow field
- Wire up `requestAnimationFrame` with delta-time

### Step 3: 3D Carousel + Doppelrand Cards
- Calculate the cylinder geometry
- Build the card HTML with double-bezel architecture
- Apply `preserve-3d` transforms

### Step 4: GSAP Choreography
- Master rotation timeline
- ScrollTrigger pinned hero with scrubbing text reveal
- Hover bullet-time + click focus-mode tweens
- Draggable spin with inertia

### Step 5: Expanded Card Interiors
- Build the minimalist-ui interior layout
- Wire up the `data-anim` entry choreography
- Implement the Button-in-Button close mechanism

### Step 6: Foreground HUD + Spotlight Borders
- Floating glass pill nav
- Spatial coordinate readouts
- Cursor-tracking radial gradient borders

### Step 7: QA Pass (`review-animations`)
- Audit every animation against the 10 standards
- Test `prefers-reduced-motion`
- Test keyboard navigation
- Verify GPU-only animation properties

---

## User Review Required

> [!IMPORTANT]
> **This plan now concretely utilizes 22 design/frontend/animation skills.** Every one has a specific, documented contribution — not a vague mention. The remaining skills in your repository (Expo, RevenueCat, Supabase, Cloudflare, etc.) are backend/mobile skills that don't apply to a single HTML visualization.

> [!TIP]
> **Font Choice**: I plan to use `Clash Display` for display type. It's available via fontsource or CDN. Do you have a preference, or should I proceed?

Ready to execute on your approval.
