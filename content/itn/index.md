+++
title = "Imagining the Neutrino"
description = "Interactive 3-flavor neutrino oscillation visualization"
template = "page.html"
date = 2026-02-03
+++

## [▶ Launch Demo](https://planckeon.github.io/itn/)

Watch a neutrino fly through space as its flavor evolves in real-time.

---

## What You See

**The Sphere** — A color-blending neutrino whose RGB channels represent flavor probabilities:
- Red = electron neutrino (νₑ)
- Green = muon neutrino (νμ)
- Blue = tau neutrino (ντ)

**The Starfield** — Immersive 3D canvas you can rotate by dragging

**The Plots**:
- Probability vs Distance — P(νₑ), P(νμ), P(ντ) over the journey
- Ternary Flavor Triangle — VISOS-style flavor space trajectory
- Energy Spectrum — P vs E at current distance
- PMNS Matrix — The 3×3 mixing matrix with color intensity

---

## What You Control

| Control | What it does |
|---------|--------------|
| **Experiment Presets** | 11 experiments: T2K, NOvA, DUNE, Hyper-K, KamLAND, Daya Bay, JUNO, Double Chooz, Super-K, IceCube, Solar |
| **Initial Flavor** | Start as νₑ, νμ, or ντ |
| **Energy Slider** | Adjust neutrino energy (affects oscillation wavelength) |
| **δCP Slider** | CP violation phase (0-360°) |
| **ν/ν̄ Toggle** | Neutrino vs antineutrino |
| **NO/IO Toggle** | Normal vs Inverted mass ordering |
| **Matter Effect** | Enable MSW effect with adjustable density |

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Play/Pause |
| `A` | Toggle antineutrino |
| `M` | Toggle matter effect |
| `N` | Toggle mass ordering |
| `R` | Reset simulation |
| `1-4` | Apply presets (T2K, NOvA, DUNE, KamLAND) |
| `↑/↓` | Adjust energy |
| `←/→` | Adjust δCP |
| `S` | Copy share URL |
| `?` | Show help |

---

## URL Sharing

Share exact configurations:

```
https://planckeon.github.io/itn/#e=2.5&f=muon&d=180&m=1&o=inverted
```

Parameters: `e` (energy), `f` (flavor), `d` (δCP), `a` (antineutrino), `m` (matter), `o` (ordering), `p` (preset)

---

## The Physics Engine

Under the hood, ITN uses [nufast](/nufast) compiled to WebAssembly—the same algorithm used by T2K and JUNO, running at 20 million calculations per second in your browser.

The WASM binary is **13 KB**. No CDN, no external dependencies, just math.

---

## Technical Details

| Layer | Tech |
|-------|------|
| Framework | React 19 + TypeScript |
| Build | Vite |
| Rendering | Canvas 2D @ 60fps |
| Physics | nufast WASM (Zig → WASM) |
| Math | KaTeX |
| i18n | 7 languages |
| Tests | 166 passing |

---

## Why Build This?

Neutrino oscillations are one of the most beautiful phenomena in physics—quantum superposition playing out over hundreds of kilometers. But most visualizations are static plots or animations without interactivity.

I wanted something where you could *feel* the physics. Change δCP and watch the oscillation pattern shift. Toggle matter effects and see MSW resonance appear. Compare DUNE to T2K and understand why baseline matters.

Plus, it's a good way to dogfood [nufast](/nufast).

---

## Links

- **Demo**: [planckeon.github.io/itn](https://planckeon.github.io/itn/)
- **GitHub**: [planckeon/itn](https://github.com/planckeon/itn)
- **Physics Engine**: [nufast](/nufast)
