# planckeon.github.io

The official website for **Planckeon Labs** — R&D in fast | intelligent software tooling for theoretical physics.

**Live site**: https://planckeon.github.io

---

## Tech Stack

- **Static Site Generator**: [Zola](https://www.getzola.org/) (v0.19.2+)
- **Styling**: Custom SCSS (self-contained deep space theme)
- **Math Rendering**: MathJax 3
- **Deployment**: GitHub Actions → GitHub Pages
- **Hosting**: GitHub Pages

---

## Local Development

### Prerequisites

Install Zola via Homebrew (macOS) or see [Zola installation docs](https://www.getzola.org/documentation/getting-started/installation/):

```bash
brew install zola
```

### Running Locally

```bash
# Clone the repository
git clone https://github.com/planckeon/planckeon.github.io.git
cd planckeon.github.io

# Start development server with live reload
zola serve

# Site will be available at http://127.0.0.1:1111
```

### Building for Production

```bash
zola build

# Output will be in ./public/
```

---

## Project Structure

```
planckeon.github.io/
├── config.toml           # Zola configuration
├── content/              # Markdown content
│   ├── _index.md         # Landing page metadata
│   └── about/
│       └── index.md      # About page
├── sass/
│   └── site.scss         # Main stylesheet (deep space theme)
├── static/
│   └── logo.png          # Organization logo
├── templates/
│   ├── index.html        # Landing page template
│   ├── page.html         # Generic page template
│   └── 404.html          # Error page
└── .github/
    └── workflows/
        └── deploy.yml    # GitHub Actions deployment
```

---

## Theme: Deep Space Mystical

The site uses a custom, self-contained SCSS theme with:

- **Color Palette**: Deep purples (#0a0a12 background), slate blue (#7b68ee), cyan (#00ced1), gold (#c9a227)
- **Starfield Effect**: CSS radial gradients creating a subtle star field
- **Typography**: System fonts with monospace for code
- **Responsive Design**: Mobile-first approach
- **MathJax Support**: LaTeX equations via `$...$` and `$$...$$`

The theme has no external dependencies — it's fully self-contained in `sass/site.scss`.

---

## Adding Content

### New Page

Create a new directory under `content/` with an `index.md` file:

```markdown
+++
title = "Page Title"
description = "Page description for meta tags"
template = "page.html"
date = 2026-01-22
+++

Your markdown content here...
```

### LaTeX Math

Inline math: `$E = mc^2$`

Display math:
```
$$
S_A = \frac{\text{Area}(\gamma_A^{\min})}{4G_{d+1}}
$$
```

---

## Deployment

The site automatically deploys via GitHub Actions when changes are pushed to `main`:

1. Zola builds the site
2. Output is uploaded as a GitHub Pages artifact
3. GitHub Pages serves from the artifact

See `.github/workflows/deploy.yml` for configuration.

---

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make your changes
4. Test locally with `zola serve`
5. Commit and push
6. Open a pull request

---

## Related Repositories

- [planckeon/.github](https://github.com/planckeon/.github) — Organization README and profile
- [planckeon/autograv](https://github.com/planckeon/autograv) — Numerical relativity + autodiff (JAX)
- [planckeon/pauliz](https://github.com/planckeon/pauliz) — Quantum computing simulation (Zig)
- [planckeon/attn-as-bilinear-form](https://github.com/planckeon/attn-as-bilinear-form) — Transformer attention research

---

## License

Content is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Code samples are licensed under MIT.
