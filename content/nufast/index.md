+++
title = "nufast: Neutrino Oscillations at 25 ns"
description = "Fast three-flavor neutrino oscillation probabilities in Rust, Zig, and WebAssembly"
template = "page.html"
date = 2026-02-03
+++

## The Problem

Computing neutrino oscillation probabilities is fundamental to experimental neutrino physics. Experiments like DUNE, T2K, and JUNO need to evaluate these probabilities millions of times during parameter fitting and systematic studies.

The traditional approach—direct matrix exponentiation—is slow. Even optimized implementations take microseconds per calculation. That adds up.

## The Solution: NuFast

In 2024, Peter Denton and Stephen Parke published the [NuFast algorithm](https://arxiv.org/abs/2405.02400), achieving ~100 ns per calculation. The key insight: use the Eigenvalue-Eigenvector Identity (EEI) to avoid cubic eigenvalue equations entirely.

NuFast is now used in production by **T2K** (via MaCH3) and **JUNO**.

## Our Implementation

We ported NuFast to modern systems languages:

| Implementation | Performance | Notes |
|----------------|-------------|-------|
| **Zig SIMD f32** | **21 ns** | 8 simultaneous calculations |
| **Zig SIMD f64** | **25 ns** | 4 simultaneous calculations |
| **Zig scalar** | 42 ns | No vectorization |
| **Rust** | 61 ns | crates.io package |
| **WASM** | ~80 ns | Runs in browsers |
| *Original C++* | *49 ns* | *Denton's reference* |
| *Original Python* | *14,700 ns* | *Baseline* |

The Zig SIMD implementation is **4.7× faster** than the original.

---

## Features

### Core Physics
- **Vacuum oscillations** — Exact analytic formula
- **Matter effects** — DMP approximation with Newton refinement
- **Anti-neutrino mode** — Sign-flipped δCP and matter potential

### Advanced (Zig only)
- **PREM Earth model** — 6-layer variable density for atmospheric neutrinos
- **NSI support** — Non-Standard Interactions with complex ε matrix
- **Sterile neutrinos** — 3+1 model with exact 4-flavor vacuum
- **Experiment presets** — DUNE, T2K, NOvA, Hyper-K, JUNO

### Developer Experience
- **Batch APIs** — Pre-computed mixing for 45% speedup
- **SIMD vectorization** — 4×f64 or 8×f32 lanes
- **Python bindings** — ctypes wrapper with zero dependencies
- **TypeScript bindings** — Full type definitions for WASM

---

## Quick Start

### Rust

```toml
[dependencies]
nufast = "0.5"
```

```rust
use nufast::{VacuumParameters, probability_vacuum_lbl};

let params = VacuumParameters::nufit52_no(1300.0, 2.5);
let probs = probability_vacuum_lbl(&params);
println!("P(νμ → νe) = {:.4}", probs.Pme);
```

### Zig

```zig
const nufast = @import("nufast");

const dune = nufast.experiments.dune;
const probs = nufast.matterProbability(dune.toMatterParams(), dune.L, dune.E);
// probs[1][0] = P(νμ → νe)
```

### WebAssembly (TypeScript)

```typescript
import { loadNuFast } from '@nufast/wasm';

const nufast = await loadNuFast();
const Pme = nufast.vacuumPmeDefault(1300, 2.5);
console.log(`P(νμ → νe) = ${(Pme * 100).toFixed(2)}%`);
```

---

## Why Zig?

The performance gap isn't magic. It comes from explicit control:

1. **No ownership overhead** — Zig's memory model doesn't add borrow-checker constraints
2. **Comptime everything** — Physics constants and batch sizes resolved at compile time
3. **Direct SIMD** — `@Vector` types map to hardware intrinsics
4. **Zero allocations** — All computation on the stack

Rust's ~61 ns is still excellent. But when you need maximum throughput, Zig delivers.

---

## The Story

This project has roots in my undergrad thesis at Krea University (2022-2023), where I explored the Eigenvalue-Eigenvector Identity for neutrino oscillations. That work became `pytrino`, a Python/Cython library on PyPI.

In October 2024, I emailed Peter Denton about extending EEI to 4-flavor oscillations. His response: "analytically much much worse." But he pointed me to NuFast, quoting ~100 ns per calculation.

Challenge accepted. The Zig port now runs at 21 ns—beating the original by 4.7×.

---

## Links

- **GitHub**: [planckeon/nufast](https://github.com/planckeon/nufast)
- **crates.io**: [nufast](https://crates.io/crates/nufast)
- **Paper**: [PDF](https://github.com/planckeon/nufast/blob/main/paper/nufast-benchmark.pdf)
- **Live Demo**: [Imagining the Neutrino](https://planckeon.github.io/itn/) (powered by nufast WASM)

## References

1. P.B. Denton & S.J. Parke, [arXiv:2405.02400](https://arxiv.org/abs/2405.02400) (2024)
2. [NuFit 5.2](http://www.nu-fit.org) — Neutrino oscillation parameters
3. [NuFast GitHub](https://github.com/PeterDenton/NuFast) — Original implementations
