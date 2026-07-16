# bomhort-website

Hugo-basierte Website fuer **BOMHort** (ehemals SeeBOM), das Kubernetes-native SBOM Visualisierungs- und Governance-Projekt.

## Struktur

- `hugo.toml`: Site-Konfiguration und Hauptnavigation
- `layouts/`: Templates fuer Home, Listen- und Content-Seiten
- `content/`: Inhaltsseiten (`Documentation`, `Community`, `Blog`)
- `static/css/main.css`: Dark-Mode Design-Tokens und Layout-Styling
- `static/images/logo.svg`: Markenlogo
- `layouts/partials/icon.html`: Flowbite-Icons (MIT), lokal eingebunden aus `static/images/flowbite/`

## Lokal starten

```bash
hugo server -D
```

## Produktion bauen

```bash
hugo
```

Das Build-Ergebnis liegt in `public/`.

## Deployment (GitHub Pages)

Die Seite wird via GitHub Actions automatisch auf GitHub Pages deployed
(`.github/workflows/hugo.yml`). Jeder Push auf `main` baut die Seite mit Hugo
(`--gc --minify`) und veröffentlicht sie.

Einmalige Einrichtung im Repo: **Settings → Pages → Build and deployment →
Source: GitHub Actions**. Die Custom Domain `bomhort.dev` wird über
`static/CNAME` gesetzt (DNS muss auf GitHub Pages zeigen).

Weitere Projektdokumentation: `https://docs.bomhort.dev`.
Projekt-Repository: `https://github.com/seebom-labs/BOMHort`.

