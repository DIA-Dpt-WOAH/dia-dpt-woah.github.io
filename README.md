# DIAD technical material website (mock-up)

Quarto website for the technical material of the WOAH Data Integration & Analytics Department.
Same stack as the [WOAH Datathon site](https://data-integration-department-woah.github.io/WOAH-Datathon/):
Quarto `website` project, `_brand.yml` with the WOAH palette (from `woah-style`), output in `docs/`.

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
  link: https://data-integration-department-woah.github.io/epiq-my-report/
  repo: https://github.com/Data-Integration-Department-WOAH/epiq-my-report
```

## Build locally

```bash
quarto preview      # live preview
quarto render       # builds into docs/ (keep docs/.nojekyll)
```

## Publishing set-up (agreed, not done yet)

- Repo `Data-Integration-Department-WOAH/data-integration-department-woah.github.io`,
  so the site is served at the organisation root URL
  `https://data-integration-department-woah.github.io/`.
- GitHub Pages from `main` / `docs/` (as for the Datathon), or a GitHub Action running `quarto publish gh-pages`.
- Material repos named with an area prefix (`obs-`, `epiq-`, `ahe-`, `dsl-`) and tagged with GitHub topics.
  A repo with its own Quarto/pkgdown site is then served at `https://data-integration-department-woah.github.io/<repo>/`.

## Content rules

- No staff names or photos on the public site.
- No photographs: pages use solid WOAH colours (pastel backgrounds per area, dark grey and orange accents).
  If photos are added later, credit them to WOAH.
