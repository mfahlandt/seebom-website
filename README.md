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

Weitere Projektdokumentation: `https://docs.bomhort.dev`.
Projekt-Repository: `https://github.com/seebom-labs/BOMHort`.

