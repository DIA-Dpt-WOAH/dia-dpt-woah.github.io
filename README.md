# DIAD technical material sharing website 

Quarto website for the technical material of the WOAH Data Integration & Analytics Department.
Same stack as the [WOAH Datathon site](https://dia-dpt-woah.github.io/WOAH-Datathon/):
Quarto `website` project, `_brand.yml` with the WOAH palette (from `woah-style`), output in `docs/`.
Only the `.qmd`/`.yml` sources are versioned; GitHub Actions renders the HTML.

## Structure

```
_quarto.yml            site config (navbar, footer, announcement bar)
_brand.yml             WOAH colours and fonts
styles.scss            WOAH look (white navbar, orange accents, cards)
_templates/materials.ejs   card template for technical material
index.qmd              home
observatory/  epiq/  econometrics/  dslab/
    index.qmd          area page
    materials.yml      catalogue of the area's material  <- edit this to add items
resources.qmd          all material, filterable
network.qmd            Data Swarm and partners
about.qmd              department, data strategy, contact
assets/                photos, logos, team pictures
```

## Adding a piece of material

Add an entry to the area's `materials.yml`:

```yaml
- title: "My report"
  type: Report            # Report | Code | Dataset | App | API | Training | Tutorial | Event | Project
  area: EPIQ
  status: Available       # Available | In progress | Planned
  categories: [Report, Epidemic intelligence]
  description: "One sentence."
  link: https://dia-dpt-woah.github.io/epiq-my-report/
  repo: https://github.com/DIA-Dpt-WOAH/epiq-my-report
```

## Build locally

```bash
quarto preview      # live preview
quarto render       # builds into docs/ for a local check (docs/ is git-ignored)
```

## Publishing

- Repo `DIA-Dpt-WOAH/dia-dpt-woah.github.io`, served by GitHub Pages at the organisation root URL
  `https://dia-dpt-woah.github.io/`. The repo name must match the organisation name, or Pages serves it under a sub-path.
- Settings > Pages > Source is set to **GitHub Actions**. On every push to `main`,
  `.github/workflows/publish.yml` runs `quarto render` (Quarto 1.10.18) and deploys `docs/`.
  To update the site: edit the `.qmd`/`.yml` files, commit and push. No local render needed.
  Progress and errors show in the repo's Actions tab.
- Material repos named with an area prefix (`obs-`, `epiq-`, `ahe-`, `dsl-`) and tagged with GitHub topics.
  A repo with its own Quarto/pkgdown site is then served at `https://dia-dpt-woah.github.io/<repo>/`.

## Content rules

- No staff names or photos on the public site.
- No photographs: pages use solid WOAH colours (pastel backgrounds per area, dark grey and orange accents).
  If photos are added later, credit them to WOAH.
