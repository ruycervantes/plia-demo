# PLIA Teams — Demo Materials

Demo site and source documents for the PLIA Teams investor demo.

## Structure

```
docs/               Source markdown (team can edit/contribute)
site/               Published HTML (what Netlify deploys)
netlify.toml        Netlify config (publish = "site")
```

## Pages

| Page | Source | Description |
|------|--------|-------------|
| [Hub](site/index.html) | — | Landing page with links to everything |
| [Demo Flow](site/demo-flow.html) | `docs/investor-demo-flow.md` | 6-beat investor pitch walkthrough |
| [Demo Scenario](site/demo-scenario.html) | `docs/demo-scenario-alfonso-el-sabio.md` | Alfonso el Sabio production scenario |
| [Dashboard Spec](site/dashboard-spec.html) | `docs/dashboard-design-spec.md` | Dashboard visual/interaction spec |
| [Strategic Brief](site/strategic-brief.html) | `docs/strategic-brief.md` | IZEN market case + problem framing |
| [Data Infrastructure](site/data-infra.html) | `docs/data-infrastructure-context.md` | What data PLIA captures/leverages |

## Repo-only docs (not published as HTML)

- `docs/prototype-build-plan.md` — Internal engineering plan

## How to publish

1. Edit markdown in `docs/` or HTML in `site/`
2. Commit and push to `main`
3. Netlify auto-deploys from the `site/` folder

## Related

- [Product Thesis](https://stoic-2026.netlify.app/) — PLIA Teams product thesis on stoic-2026
