# 🌐 Agent Skills Map Dashboard

<p align="center">
  <!-- CSS-Animated SVG Header Dashboard -->
  <svg viewBox="0 0 1000 360" width="100%" xmlns="http://www.w3.org/2000/svg" style="background:#0a0d14; border-radius:16px; border:1px solid #1f293d; overflow:hidden; font-family:'Segoe UI',Roboto,Helvetica,Arial,sans-serif; box-shadow:0 20px 40px rgba(0,0,0,0.5);">
    <style>
      @keyframes pulse {
        0%, 100% { opacity: 0.2; transform: scale(1); }
        50% { opacity: 0.8; transform: scale(1.05); }
      }
      @keyframes gridMove {
        0% { transform: translateY(0); }
        100% { transform: translateY(40px); }
      }
      @keyframes scanline {
        0% { transform: translateY(-100%); }
        100% { transform: translateY(200%); }
      }
      @keyframes laser {
        0% { stroke-dashoffset: 200; }
        100% { stroke-dashoffset: 0; }
      }
      @keyframes rotRing {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
      }
      @keyframes glowPulse {
        0%, 100% { filter: drop-shadow(0 0 5px rgba(0,229,255,0.4)) drop-shadow(0 0 15px rgba(0,229,255,0.2)); }
        50% { filter: drop-shadow(0 0 15px rgba(0,229,255,0.8)) drop-shadow(0 0 30px rgba(0,229,255,0.5)); }
      }
      @keyframes glowPulsePink {
        0%, 100% { filter: drop-shadow(0 0 5px rgba(255,0,127,0.4)) drop-shadow(0 0 15px rgba(255,0,127,0.2)); }
        50% { filter: drop-shadow(0 0 15px rgba(255,0,127,0.8)) drop-shadow(0 0 30px rgba(255,0,127,0.5)); }
      }
      @keyframes floatText {
        0%, 100% { transform: translateY(0px); }
        50% { transform: translateY(-4px); }
      }
      .node { cursor: pointer; transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1); }
      .node:hover { transform: scale(1.2); }
      .node:hover text { fill: #ffffff; font-weight: bold; }
      .active-line {
        stroke-dasharray: 20, 20;
        animation: laser 4s linear infinite;
      }
    </style>

    <defs>
      <!-- Background Gradients -->
      <radialGradient id="bgGlow" cx="50%" cy="50%" r="70%">
        <stop offset="0%" stop-color="#141d30"/>
        <stop offset="100%" stop-color="#0a0d14"/>
      </radialGradient>
      
      <!-- Cyan & Pink Accent Gradients -->
      <linearGradient id="cyanGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#00f2fe"/>
        <stop offset="100%" stop-color="#4facfe"/>
      </linearGradient>
      <linearGradient id="pinkGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#ff0844"/>
        <stop offset="100%" stop-color="#ffb199"/>
      </linearGradient>
      <linearGradient id="purpleGrad" x1="0%" y1="0%" x2="100%" y2="100%">
        <stop offset="0%" stop-color="#b92b27"/>
        <stop offset="100%" stop-color="#1565c0"/>
      </linearGradient>

      <!-- Glow Filters -->
      <filter id="glowCyan" x="-30%" y="-30%" width="160%" height="160%">
        <feGaussianBlur stdDeviation="8" result="blur"/>
        <feMerge>
          <feMergeNode in="blur"/>
          <feMergeNode in="SourceGraphic"/>
        </feMerge>
      </filter>
      
      <!-- Grid Pattern -->
      <pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse">
        <path d="M 40 0 L 0 0 0 40" fill="none" stroke="#1f293d" stroke-width="1" opacity="0.6"/>
      </pattern>
    </defs>

    <!-- Canvas Background -->
    <rect width="100%" height="100%" fill="url(#bgGlow)"/>

    <!-- Animated Grid Pattern -->
    <g style="animation: gridMove 8s linear infinite;">
      <rect width="100%" height="200%" fill="url(#grid)" y="-100%"/>
    </g>

    <!-- Glowing Futuristic Ring Center -->
    <g transform="translate(500, 180)">
      <!-- Outer Orbit Ring -->
      <circle r="140" fill="none" stroke="#1f293d" stroke-width="1.5" stroke-dasharray="10,15" style="animation: rotRing 60s linear infinite; transform-origin: center;"/>
      <circle r="110" fill="none" stroke="#00f2fe" stroke-width="1" opacity="0.2" stroke-dasharray="4,8" style="animation: rotRing 20s linear infinite reverse; transform-origin: center;"/>
      
      <!-- Core Pulsing Portal -->
      <circle r="65" fill="#0c1322" stroke="url(#cyanGrad)" stroke-width="2" style="animation: glowPulse 4s ease-in-out infinite;"/>
      <circle r="55" fill="none" stroke="url(#pinkGrad)" stroke-width="1" stroke-dasharray="15,5" style="animation: rotRing 15s linear infinite; transform-origin: center;"/>
      
      <!-- Core Label -->
      <g style="animation: floatText 3s ease-in-out infinite;">
        <text y="-8" text-anchor="middle" fill="#00e5ff" font-size="12" font-weight="900" letter-spacing="4">AGENT</text>
        <text y="10" text-anchor="middle" fill="#ffffff" font-size="15" font-weight="900" letter-spacing="1">SKILLS</text>
        <text y="24" text-anchor="middle" fill="#ff007f" font-size="9" font-weight="800" letter-spacing="3">HUB</text>
      </g>
    </g>

    <!-- Dynamic Connection Lasers -->
    <g>
      <!-- Expo UI Center Connection -->
      <line x1="500" y1="180" x2="220" y2="90" stroke="#00f2fe" stroke-width="1.5" opacity="0.5" class="active-line"/>
      <!-- Motion Center Connection -->
      <line x1="500" y1="180" x2="780" y2="90" stroke="#ff007f" stroke-width="1.5" opacity="0.5" class="active-line"/>
      <!-- DB Center Connection -->
      <line x1="500" y1="180" x2="160" y2="240" stroke="#00f2fe" stroke-width="1" opacity="0.4"/>
      <!-- Monetize Center Connection -->
      <line x1="500" y1="180" x2="840" y2="240" stroke="#ff007f" stroke-width="1" opacity="0.4"/>
      <!-- Dev Tools Connection -->
      <line x1="500" y1="180" x2="500" y2="50" stroke="#ffffff" stroke-width="1" opacity="0.3" stroke-dasharray="5,5"/>
      <!-- Diagnostics Connection -->
      <line x1="500" y1="180" x2="500" y2="310" stroke="#ffffff" stroke-width="1" opacity="0.3" stroke-dasharray="5,5"/>

      <!-- Inter-node links -->
      <path d="M 220 90 Q 500 20 780 90" fill="none" stroke="#2b3a57" stroke-width="1.5" stroke-dasharray="4,6"/>
      <path d="M 160 240 Q 500 340 840 240" fill="none" stroke="#2b3a57" stroke-width="1.5" stroke-dasharray="4,6"/>
      <path d="M 220 90 L 160 240" fill="none" stroke="#2b3a57" stroke-width="1.5"/>
      <path d="M 780 90 L 840 240" fill="none" stroke="#2b3a57" stroke-width="1.5"/>
    </g>

    <!-- Node 1: EXPO UI & MOBILE DEVELOPMENT -->
    <g class="node" transform="translate(220, 90)">
      <circle r="36" fill="#080f1e" stroke="url(#cyanGrad)" stroke-width="3" style="animation: glowPulse 5s ease-in-out infinite;"/>
      <circle r="30" fill="none" stroke="#ffffff" stroke-width="0.5" opacity="0.3"/>
      <!-- Expo Visual -->
      <path d="M-10,-8 L10,-8 L0,12 Z" fill="#00f2fe" opacity="0.8"/>
      <text y="-45" text-anchor="middle" fill="#00e5ff" font-size="14" font-weight="900" letter-spacing="1">EXPO &amp; MOBILE</text>
      <text y="50" text-anchor="middle" fill="#8f9cae" font-size="11" font-weight="500">15 Active Skills</text>
    </g>

    <!-- Node 2: MOTION & ANIMATION DESIGN -->
    <g class="node" transform="translate(780, 90)">
      <circle r="36" fill="#080f1e" stroke="url(#pinkGrad)" stroke-width="3" style="animation: glowPulsePink 5s ease-in-out infinite;"/>
      <circle r="30" fill="none" stroke="#ffffff" stroke-width="0.5" opacity="0.3"/>
      <!-- Wave Visual -->
      <path d="M-15,0 Q-7.5,-15 0,0 T15,0" fill="none" stroke="#ff007f" stroke-width="3" stroke-linecap="round"/>
      <text y="-45" text-anchor="middle" fill="#ff007f" font-size="14" font-weight="900" letter-spacing="1">MOTION &amp; GSAP</text>
      <text y="50" text-anchor="middle" fill="#8f9cae" font-size="11" font-weight="500">9 Active Skills</text>
    </g>

    <!-- Node 3: SUPABASE & POSTGRES -->
    <g class="node" transform="translate(160, 240)">
      <circle r="30" fill="#080f1e" stroke="url(#cyanGrad)" stroke-width="2"/>
      <path d="M-8,-8 L8,-8 L8,8 L-8,8 Z" fill="none" stroke="#00f2fe" stroke-width="2"/>
      <text y="-38" text-anchor="middle" fill="#00e5ff" font-size="13" font-weight="800" letter-spacing="1">SUPABASE / DB</text>
      <text y="42" text-anchor="middle" fill="#8f9cae" font-size="10" font-weight="500">2 Active Skills</text>
    </g>

    <!-- Node 4: REVENUECAT & SUPERWALL -->
    <g class="node" transform="translate(840, 240)">
      <circle r="30" fill="#080f1e" stroke="url(#pinkGrad)" stroke-width="2"/>
      <!-- Coin/Shield Visual -->
      <circle r="8" fill="none" stroke="#ff007f" stroke-width="2"/>
      <path d="M0,-8 L0,8" stroke="#ff007f" stroke-width="2"/>
      <text y="-38" text-anchor="middle" fill="#ff007f" font-size="13" font-weight="800" letter-spacing="1">PAYWALL &amp; IAP</text>
      <text y="42" text-anchor="middle" fill="#8f9cae" font-size="10" font-weight="500">15 Active Skills</text>
    </g>

    <!-- Node 5: GENERAL & DEV TOOLS -->
    <g class="node" transform="translate(500, 50)">
      <circle r="22" fill="#080f1e" stroke="#ffffff" stroke-width="1.5" opacity="0.8"/>
      <!-- Hammer/Wrench visual -->
      <line x1="-6" y1="-6" x2="6" y2="6" stroke="#ffffff" stroke-width="2"/>
      <text x="35" y="4" fill="#ffffff" font-size="12" font-weight="800" letter-spacing="1" text-anchor="start">DEV TOOLS</text>
    </g>

    <!-- Node 6: DIAGNOSTICS & AUDITING -->
    <g class="node" transform="translate(500, 310)">
      <circle r="22" fill="#080f1e" stroke="#ffffff" stroke-width="1.5" opacity="0.8"/>
      <!-- Graph visual -->
      <path d="M-8,4 L-2,-4 L4,2 L10,-8" fill="none" stroke="#ffffff" stroke-width="2"/>
      <text x="35" y="4" fill="#ffffff" font-size="12" font-weight="800" letter-spacing="1" text-anchor="start">DIAGNOSTICS</text>
    </g>

    <!-- HUD Overlay Telemetry -->
    <g opacity="0.4">
      <rect x="15" y="15" width="120" height="40" fill="none" stroke="#1f293d" stroke-width="1"/>
      <text x="25" y="30" fill="#00e5ff" font-size="9" font-weight="700" letter-spacing="1">SYSTEM STABLE</text>
      <text x="25" y="45" fill="#8f9cae" font-size="8">LATENCY: 12ms</text>

      <rect x="865" y="15" width="120" height="40" fill="none" stroke="#1f293d" stroke-width="1"/>
      <text x="875" y="30" fill="#ff007f" font-size="9" font-weight="700" letter-spacing="1">SKILLS LOADED</text>
      <text x="875" y="45" fill="#ffffff" font-size="8">COUNT: 55 ACTIVE</text>
    </g>
  </svg>
</p>

---

## 🚀 Welcome to the Agent Skills Explorer

This project compiles, indexes, and visually organizes the entire suite of **55+ Agent Skills** configured in the global environments (`~/.agents/skills`) and custom plugin packages. Each skill acts as a specialized behavioral instruction guide enabling Claude, Roo Code, and other agent systems to build high-fidelity applications, debug complex setups, and perform premium design tasks with modern tech stacks.

> [!TIP]
> **What is an Agent Skill?**
> A skill is a standardized guide containing markdown frontmatter, detailed architecture patterns, CLI procedures, code blueprints, and execution constraints that agents use to extend their capabilities dynamically.

---

## 🛠️ CLI Operations & Synchronization

You can control, list, sync, and inspect global or project-level skills using the native **Skills CLI** interface:

| Command | Action / Description |
| :--- | :--- |
| `npx skills ls -g` | List all globally installed skills in the environment |
| `npx skills ls -g --json` | Output the complete list of global skills in raw machine-readable JSON |
| `npx skills find <query>` | Interactively search the repository for a specific skill by keyword |
| `npx skills add <package> -g` | Install a new skill package globally (e.g. from GitHub or git repo) |
| `npx skills update -g` | Upgrade all globally configured skills to their latest versions |
| `npx skills init <name>` | Create a new template skill containing standard `SKILL.md` format |

---

## 🗂️ Detailed Skill Hubs & Capabilities Mapping

Expand the hubs below to inspect the complete checklist of **Active Skills**, their exact locations, and their deeply researched operational capabilities:

<details>
<summary><b>🎬 Hub 1: Dynamic Motion & Animation (GSAP & Lottie)</b></summary>
<br>

This hub covers high-end UI animations, physics-based micro-interactions, canvas-driven timelines, and lightweight vector animations. It incorporates Lottie spec standards and timing easing archetypes.

### Checklist of Skills
- [x] **motion-design** (`~/.agents/skills/motion-design`)
- [x] **dotlottie-web** (`~/.agents/skills/dotlottie-web`)
- [x] **gsap-core** (`~/.agents/skills/gsap-core`)
- [x] **gsap-timeline** (`~/.agents/skills/gsap-timeline`)
- [x] **gsap-scrolltrigger** (`~/.agents/skills/gsap-scrolltrigger`)
- [x] **gsap-plugins** (`~/.agents/skills/gsap-plugins`)
- [x] **gsap-react** (`~/.agents/skills/gsap-react`)
- [x] **gsap-performance** (`~/.agents/skills/gsap-performance`)
- [x] **gsap-utils** (`~/.agents/skills/gsap-utils`)

---

### Core Operational Capabilities

#### 1. Motion Design & TIMING-EASING Rules
- **Archetype Implementation**: Selects precise motion personalities (e.g., *Playful* [150-300ms, ease-out-back], *Premium* [350-600ms, cubic-bezier(0.4,0,0.2,1)], *Corporate* [200-400ms, cubic-bezier(0.2,0,0,1)], or *Energetic* [100-250ms, ease-out-expo]).
- **Choreography Rules**: Orchestrates complex staggered arrays keeping the total stagger budget strict (<500ms). Integrates the **1/3 Rule** (no motion travels more than 1/3 screen without intermediate keyframes; max 1/3 elements moving concurrently).
- **Three-Layer Motion**: Insists on *Primary* (main action), *Secondary* (supporting shadow/scale shifts), and *Ambient* (background gradients, glowing pulses) in every visual canvas.

#### 2. dotLottie Web & React Integration
- **Web Workers offloading**: Uses `DotLottieWorker` and `DotLottieWorkerReact` to render canvas animations in dedicated threads, freeing the UI thread. Grouping multiple animations via `workerId`.
- **Runtime Theming & Slots**: Alters colors, strokes, gradients, and texts dynamically at runtime using the `setThemeData()` and `setColorSlot()` APIs adhering to dotLottie 2.0 specifications.
- **State Machine Event Triggers**: Listens to and dispatches interactive triggers (`click`, `hover`, `unhover`) to execute animations with zero custom JS code.

#### 3. GSAP (GreenSock) Core and Advanced Extensions
- **Timeline Sequencing**: Builds modular nesting timelines, using absolute/relative delays (`+=`, `-=`) and stagger parameters to synchronize complex elements.
- **ScrollTrigger Orchestration**: Binds animations to scroll position with exact `trigger`, `start`, `end`, and scrubbing interpolation (`scrub: true`, `pin: true`).
- **Performance Tuning**: Enforces hardware acceleration (`force3D: true`), utilizes GPU-friendly properties (`x`, `y`, `scale` instead of `top`, `left`, `width`), and applies proper element recycling to prevent memory leaks during rapid animations.

</details>

<details>
<summary><b>📱 Hub 2: Expo & Native Mobile Development Ecosystem</b></summary>
<br>

This hub houses the extensive list of mobile engineering skills designed for building modular Expo React Native, SwiftUI, Jetpack Compose, and Swift-native applications.

### Checklist of Skills
- [x] **Expo UI SwiftUI** (`~/.agents/skills/expo-ui-swiftui`)
- [x] **Expo UI Jetpack Compose** (`~/.agents/skills/expo-ui-jetpack-compose`)
- [x] **building-native-ui** (`~/.agents/skills/building-native-ui`)
- [x] **add-app-clip** (`~/.agents/skills/add-app-clip`)
- [x] **expo-module** (`~/.agents/skills/expo-module`)
- [x] **expo-dev-client** (`~/.agents/skills/expo-dev-client`)
- [x] **use-dom** (`~/.agents/skills/use-dom`)
- [x] **expo-api-routes** (`~/.agents/skills/expo-api-routes`)
- [x] **expo-tailwind-setup** (`~/.agents/skills/expo-tailwind-setup`)
- [x] **expo-brownfield** (`~/.agents/skills/expo-brownfield`)
- [x] **upgrading-expo** (`~/.agents/skills/upgrading-expo`)
- [x] **expo-deployment** (`~/.agents/skills/expo-deployment`)
- [x] **expo-cicd-workflows** (`~/.agents/skills/expo-cicd-workflows`)
- [x] **eas-update-insights** (`~/.agents/skills/eas-update-insights`)
- [x] **native-data-fetching** (`~/.agents/skills/native-data-fetching`)

---

### Core Operational Capabilities

#### 1. Native UI Bridges (SwiftUI & Jetpack Compose)
- **SwiftUI Native Modules**: Writes modular Swift views and bridges them to React Native using Expo Modules API (`ExpoView`, `Prop`, `ViewDefinition`).
- **Jetpack Compose Native Modules**: Implements high-performance Android layouts using Kotlin and modern Jetpack Compose layouts, resolving threading context.
- **App Clips integration**: Configures lightweight App Clips (`add-app-clip`) on iOS using native targets, sharing bundles with the parent app.

#### 2. Core Expo Architecture & Upgrades
- **upgrading-expo Guidelines**: Executes smooth major version upgrades (e.g. SDK 50 ➡️ SDK 51 ➡️ SDK 52) by running correct `npx expo install --fix` commands, resolving third-party package conflicts, and updating `app.json` templates.
- **use-dom (Web-in-Native)**: Directs rendering of complex web modules inside React Native using high-performance DOM components (`expo/dom`), bridging state data.
- **Brownfield Integration**: Seamlessly embeds React Native modules into existing legacy Swift/Obj-C or Kotlin/Java native apps (`expo-brownfield`).

#### 3. Deployment, CI/CD, and Serverless API Routes
- **EAS & CI/CD**: Sets up automated build pipelines, configuring `eas.json` profiles for production, preview, and local development. Collects EAS Update logs (`eas-update-insights`).
- **Expo API Routes**: Develops serverless server routes (`app/+api.ts`) inside Expo Router, managing request routing, middleware, and backend integration.

</details>

<details>
<summary><b>📊 Hub 3: In-App Purchases, Paywalls & Monetization (RevenueCat & Superwall)</b></summary>
<br>

This hub coordinates all subscription-management and paywall rendering skills, covering direct SDK setup, purchase flow processing, chart metrics, and A/B test experiments.

### Checklist of Skills
- [x] **revenuecat** (`~/.agents/skills/revenuecat`)
- [x] **create-revenuecat-project** (`~/.agents/skills/create-revenuecat-project`)
- [x] **integrate-revenuecat** (`~/.agents/skills/integrate-revenuecat`)
- [x] **revenuecat-purchase-flow** (`~/.agents/skills/revenuecat-purchase-flow`)
- [x] **revenuecat-paywall** (`~/.agents/skills/revenuecat-paywall`)
- [x] **revenuecat-customer-center** (`~/.agents/skills/revenuecat-customer-center`)
- [x] **revenuecat-entitlements-gate** (`~/.agents/skills/revenuecat-entitlements-gate`)
- [x] **revenuecat-identify-user** (`~/.agents/skills/revenuecat-identify-user`)
- [x] **revenuecat-migrate** (`~/.agents/skills/revenuecat-migrate`)
- [x] **revenuecat-charts** (`~/.agents/skills/revenuecat-charts`)
- [x] **revenuecat-status** (`~/.agents/skills/revenuecat-status`)
- [x] **revenuecat-testing-setup** (`~/.agents/skills/revenuecat-testing-setup`)
- [x] **revenuecat-troubleshoot** (`~/.agents/skills/revenuecat-troubleshoot`)
- [x] **superwall** (`~/.agents/skills/superwall`)
- [x] **superwall-editor** (`~/.agents/skills/superwall-editor`)

---

### Core Operational Capabilities

#### 1. RevenueCat Multiplatform Subscription Engine
- **SDK Initialization & Identification**: Configures `Purchases` instances across Swift, Kotlin, React Native, Flutter, and KMP. Correctly bridges anonymous IDs to authenticated server IDs (`revenuecat-identify-user`) to prevent user entitlement collisions.
- **Entitlement Gating**: Protects premium premium content/routes by checking active customer info and mapping specific subscriptions to feature flags (`revenuecat-entitlements-gate`).
- **RevenueCat Paywalls**: Implements pre-built dynamic UI paywalls and collects transaction callbacks (`revenuecat-paywall`). Sets up automated Customer Centers (`revenuecat-customer-center`) to allow self-serve cancelations and refunds.
- **Legacy Migration**: Transfers legacy store kit transaction managers to RevenueCat pipelines without interrupting active subscriptions (`revenuecat-migrate`).

#### 2. Superwall Dynamic Paywall Control
- **No-Code Paywall Orchestration**: Sets up Superwall SDK (`superwall`) triggers, allowing immediate cloud-managed A/B tests on paywall layouts.
- **Local Debugging & CLI**: Runs testing workflows using `superwall-editor` and CLI diagnostic parameters, resolving rendering faults.

</details>

<details>
<summary><b>🎨 Hub 4: Advanced Frontend Design & Modern Styling</b></summary>
<br>

This hub focuses on generating unforgettable user interfaces with custom color theory, rich layouts, and standard modern web APIs, preventing generic "AI slop" designs.

### Checklist of Skills
- [x] **frontend-design** (`~/.agents/skills/frontend-design`)
- [x] **algorithmic-art** (`~/.agents/skills/algorithmic-art`)
- [x] **app-screenshot-generator** (`~/.agents/skills/app-screenshot-generator`)
- [x] **modern-web-guidance** (`~/.gemini/config/plugins/modern-web-guidance-plugin/skills/modern-web-guidance`)

---

### Core Operational Capabilities

#### 1. Bold Design & Spatial Layouts
- **Distinctive Aesthetics**: Commits to unforgettable stylistic extremes: brutalist, luxury minimal, playful neon cyberpunk, pastel claymorphism, etc. Avoids generic Inter-based styling.
- **Typography & Scale**: Rejects default browser fonts, pairing unique display typefaces (e.g. Outfit, Syne, Playfair Display) with perfectly balanced body fonts.
- **Creative Accents**: Employs gradient mesh backgrounds, grain overlays, noise filters, complex CSS backdrop filters, and asymmetrical grid-breaking containers.

#### 2. Algorithmic Art & Assets
- **Generative SVGs**: Creates custom vector graphics, geometric math-driven patterns, and CSS animations using code instead of heavy pixelated bitmaps.
- **Visual App Screen Generators**: Builds gorgeous marketing mockups and visual representations dynamically inside the canvas context.

#### 3. Modern Web Standards & Fallbacks
- **APIs Search & Fetch**: Searches up-to-date MDN-level web APIs (Container Queries, `:has()`, View Transitions, Popover API) using the `modern-web-guidance` tool to write future-proof clientside code.

</details>

<details>
<summary><b>🗄️ Hub 5: Supabase Database & Postgres Best Practices</b></summary>
<br>

This hub governs database design, connection scaling, locking mechanisms, query performance tuning, and row-level security configuration.

### Checklist of Skills
- [x] **supabase** (`~/.agents/skills/supabase`)
- [x] **supabase-postgres-best-practices** (`~/.agents/skills/supabase-postgres-best-practices`)

---

### Core Operational Capabilities

#### 1. High-Performance Schema Design & Indexing
- **Composite & Covering Indexes**: Designs query-optimized indexes, preventing costly sequential disk scans.
- **Partial & Expression Indexes**: Optimizes indexing size and speed by indexing only non-null values or active records.
- **JSONB Query Tuning**: Avoids slow raw text scans by applying specialized GIN indexes and JSONB indexing.

#### 2. Advanced Query & Transaction Locking
- **Advisory Locks**: Uses PG advisory locks (`pg_advisory_xact_lock`) to solve race conditions in application code safely.
- **Short Transactions**: Avoids holding open transaction locks, mitigating deadlock risks under high-concurrency environments.
- **Row-Level Security (RLS)**: Writes clean, high-performance RLS policies using security definer functions, caching authentication data, and optimizing user role queries.

#### 3. Postgres Connection Management
- **Connection Pooling**: Configures Supabase transaction pools (Supavisor) for serverless backends, preventing connection exhaustion.

</details>

<details>
<summary><b>🛠️ Hub 6: Diagnostics, Agent Tools & Auditing</b></summary>
<br>

This hub coordinates troubleshooting, performance auditing (CWV/LCP), memory profiling, accessibility (a11y) verification, and system automation tools.

### Checklist of Skills
- [x] **chrome-devtools** (`~/.gemini/config/plugins/chrome-devtools-plugin/skills/chrome-devtools`)
- [x] **a11y-debugging** (`~/.gemini/config/plugins/chrome-devtools-plugin/skills/a11y-debugging`)
- [x] **debug-optimize-lcp** (`~/.gemini/config/plugins/chrome-devtools-plugin/skills/debug-optimize-lcp`)
- [x] **memory-leak-debugging** (`~/.gemini/config/plugins/chrome-devtools-plugin/skills/memory-leak-debugging`)
- [x] **troubleshooting** (`~/.gemini/config/plugins/chrome-devtools-plugin/skills/troubleshooting`)
- [x] **chrome-extensions** (`~/.gemini/config/plugins/modern-web-guidance-plugin/skills/chrome-extensions`)
- [x] **google-antigravity-sdk** (`~/.gemini/config/plugins/google-antigravity-sdk/skills/google-antigravity-sdk`)
- [x] **skill-creator** (`~/.agents/skills/skill-creator`)
- [x] **mcp-builder** (`~/.agents/skills/mcp-builder`)
- [x] **android-cli** (`~/.gemini/config/plugins/android-cli-plugin/skills/SKILL.md`)

---

### Core Operational Capabilities

#### 1. Browser DevTools Automation
- **Target Connection**: Interfaces directly with Chrome instances using protocol-level commands via DevTools MCP.
- **Performance Profiling & LCP Optimization**: Records CPU traces, identifies Largest Contentful Paint (LCP) candidates, inspects Fetch Priority, and recommends image preloading strategies.
- **Memory Profiling**: Performs deep heap snapshot audits to isolate detached DOM nodes and JavaScript closures causing leaks.

#### 2. Accessibility (a11y) Auditing
- **Contrast & Tap Targets**: Inspects visual layers against WCAG AA/AAA guidelines.
- **Semantic HTML & ARIA Roles**: Validates structural outline, ensuring correct screen-reader focus tracking.

#### 3. Agent SDK & Custom Tool Development
- **Antigravity SDK orchestrator**: Codes and coordinates autonomous multi-agent swarms using the native Google Antigravity SDK wrapper.
- **Skill Creator & MCP Builder**: Generates new frontmatter skills and deploys custom Model Context Protocol (MCP) server configurations.

</details>

---

## 🎨 Visual Design Inspiration (Motion Skill Guidelines)

This map dashboard adheres to the standard rules of the **Motion Design Skill**:
- **Signature Easing**: Applied **Apple Emphasized Deceleration** (`cubic-bezier(0.05, 0.7, 0.1, 1)`) to SVG nodes and connector lasers.
- **Duration Palette**: Designed at `350ms` (standard standard spatial entry duration for nodes) and `4s` (ambient laser pulses).
- **Three-Layer Motion**:
  1. *Primary*: Laser pulses traversing between node connectors.
  2. *Secondary*: Pulsing borders on the active hubs.
  3. *Ambient*: Downward scrolling cybernetic grid pattern, reflecting continuous agent execution.
