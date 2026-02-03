+++
title = "Planckeon Labs"
description = "R&D in high-performance computational physics"
paginate_by = 5
sort_by = "date"
+++

High-performance software tools for computational physics. When physics meets systems programming.

## Flagship Projects

### nufast — Neutrino Oscillations at 25 ns

Fast three-flavor neutrino oscillation probabilities in **Rust**, **Zig**, and **WebAssembly**.

Port of the [NuFast algorithm](https://arxiv.org/abs/2405.02400) by P.B. Denton. The Zig SIMD implementation runs at **21 ns per calculation**—4.7× faster than the original.

[GitHub](https://github.com/planckeon/nufast) • [crates.io](https://crates.io/crates/nufast) • [Paper](https://github.com/planckeon/nufast/blob/main/paper/nufast-benchmark.pdf)

### Imagining the Neutrino — Interactive Visualization

Watch a neutrino fly through space as its flavor changes. Real-time probability calculations powered by nufast WASM.

[**▶ Launch Demo**](https://planckeon.github.io/itn/) • [GitHub](https://github.com/planckeon/itn)

---

## More Projects

| Project | Description |
|---------|-------------|
| [attn-as-bilinear-form](https://planckeon.github.io/attn-as-bilinear-form/) | Transformer attention via tensor calculus and differential geometry |
| [pauliz](https://github.com/planckeon/pauliz) | Zero-dependency quantum computing simulation in Zig |
| [autograv](https://github.com/planckeon/autograv) | Numerical relativity with automatic differentiation (JAX) |
| [pytrino](https://github.com/planckeon/pytrino) | Neutrino oscillations at the speed of C (Python/Cython) |

---

## Philosophy

Speed matters. If your simulation takes hours, you'll run it once. If it takes milliseconds, you'll explore the parameter space.

All projects are MIT licensed and open source.
