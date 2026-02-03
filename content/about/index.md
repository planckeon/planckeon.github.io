+++
title = "About Planckeon Labs"
description = "The physics behind our name and work"
template = "page.html"
date = 2026-02-03
+++

## Who We Are

I'm Baalateja Kataru—physics grad turned systems programmer. Planckeon Labs is where I build high-performance computational physics tools.

The work spans neutrino phenomenology, quantum computing simulation, numerical relativity, and AI infrastructure. The common thread: make software go zoom.

---

## The Neutrino Story

My path into neutrino physics started during undergrad at Krea University (2020-2023). My thesis, supervised by Dr. Sushant Raut, explored the **Eigenvalue-Eigenvector Identity (EEI)**—a elegant result from linear algebra that simplifies neutrino oscillation calculations.

The idea: instead of solving cubic eigenvalue equations, use 2×2 submatrix diagonalization. The math is cleaner and the physics more transparent.

That work became [pytrino](https://github.com/planckeon/pytrino), a Python/Cython library published on PyPI.

### The Correspondence with Denton

In October 2024, I emailed Peter Denton (Brookhaven National Lab) about extending EEI to 4-flavor oscillations—the sterile neutrino case that might explain short-baseline anomalies.

His reply: *"Four flavors is analytically much much worse, and also numerically somewhat unstable."*

But he pointed me to [NuFast](https://arxiv.org/abs/2405.02400), his ~100 ns algorithm for 3-flavor oscillations. Used in production by T2K and JUNO.

I thought: can I beat that?

### The Result

The Zig port of NuFast runs at **21 ns per calculation** (SIMD f32). That's 4.7× faster than the original.

Not because I'm smarter—because Zig gives you explicit control over everything LLVM cares about. No hidden allocations, no ownership overhead, comptime everything.

The full [nufast](/nufast) package now includes:
- Rust crate on crates.io
- Zig implementation with SIMD
- WASM for browsers (13 KB)
- PREM Earth model for atmospheric neutrinos
- NSI support for new physics searches
- 3+1 sterile neutrino model

And [Imagining the Neutrino](/itn)—an interactive visualization powered by nufast WASM.

---

## Why "Planckeon"?

**Planckeons** are theoretical entities at the Planck scale (~10⁻³⁵ m) where quantum mechanics and gravity merge.

Recent work by Licata, Tamburini, and Fiscaletti (2024-2025) models planckeons as the "mouths" of quantum wormholes—realizing the **ER=EPR conjecture** proposed by Maldacena and Susskind. The idea: entanglement *is* geometry. Quantum correlations between distant regions are geometrically realized as wormhole connections.

In this framework, spacetime isn't fundamental—it *emerges* from the entanglement structure of planckeons.

Just as planckeons bridge quantum and gravitational physics, we build software that bridges theoretical physics and practical computation.

---

## Philosophy

**Speed matters.** If your simulation takes hours, you'll run it once. If it takes milliseconds, you'll explore the parameter space.

**Systems programming is underrated in physics.** Most physicists default to Python. That's fine for prototypes. But production tools should be fast.

**The best abstractions are zero-cost.** Zig and Rust let you write high-level code that compiles to what you'd write by hand.

**Open source is the way.** All our tools are MIT licensed.

---

## Links

- GitHub: [github.com/planckeon](https://github.com/planckeon)
- crates.io: [nufast](https://crates.io/crates/nufast)
- Personal: [github.com/bkataru](https://github.com/bkataru)

---

## References

1. Licata, I., Tamburini, F., & Fiscaletti, D. (2025). *Planckeons as mouths of quantum wormholes*. [arXiv:2505.02804](https://arxiv.org/abs/2505.02804)
2. P.B. Denton & S.J. Parke. *NuFast*. [arXiv:2405.02400](https://arxiv.org/abs/2405.02400)
3. Maldacena, J. & Susskind, L. (2013). *Cool horizons for entangled black holes*. [arXiv:1306.0533](https://arxiv.org/abs/1306.0533)
