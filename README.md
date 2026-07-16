# bomhort-website

Hugo-based website for **BOMHort** (formerly SeeBOM), the Kubernetes-native SBOM
visualization and governance project.

## Structure

- `hugo.toml`: site configuration and main navigation
- `layouts/`: templates for the home, list, and content pages
- `content/`: content pages (`Documentation`, `Community`, `Blog`, `Styleguide`)
- `static/css/main.css`: dark-mode design tokens and layout styling
- `static/images/`: brand assets, mascot, and logos
- `layouts/partials/icon.html`: Flowbite Icons (MIT), bundled locally from `static/images/flowbite/`

## Run locally

```bash
hugo server -D
```

## Build for production

```bash
hugo
```

The build output is written to `public/`.

## Deployment (GitHub Pages)

The site is deployed to GitHub Pages automatically via GitHub Actions
(`.github/workflows/hugo.yml`). Every push to `main` builds the site with Hugo
(`--gc --minify`) and publishes it.

One-time repository setup: **Settings → Pages → Build and deployment →
Source: GitHub Actions**. The custom domain `bomhort.dev` is set via
`static/CNAME` (DNS must point to GitHub Pages).

More project documentation: `https://docs.bomhort.dev`.
Project repository: `https://github.com/seebom-labs/BOMHort`.

