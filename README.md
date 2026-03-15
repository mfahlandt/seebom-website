# seebom-website

Hugo-basierte Website fuer Seebom Labs, visuell an `kcp.io` orientiert und mit Dark-Mode-Farbwerten aus `seebom/ui/src/styles.scss`.

## Struktur

- `hugo.toml`: Site-Konfiguration und Hauptnavigation
- `layouts/`: Templates fuer Home, Listen- und Content-Seiten
- `content/`: Inhaltsseiten (`Documentation`, `Community`, `Blog`)
- `static/css/main.css`: Dark-Mode Design-Tokens und Layout-Styling
- `static/images/logo.svg`: Einfaches Markenlogo
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

Weitere Projektdokumentation: `https://docs.seebom.dev`.

