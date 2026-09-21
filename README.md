# Angling Trust Data: GitHub Pages index

Commit `index.html` to the root of `FISHINGIT/anglingtrust` and it publishes at https://fishingit.github.io/anglingtrust/, linking out to the five dashboard sites you host (`/gff/`, `/re/`, `/rlw/`, `/bur/`, `/fma/`). Everything the page says about a dashboard (link, figures, date, wording) is in one `DASHBOARDS` block at the bottom of `index.html`, so a refresh is a two-minute edit.

## Where things live

```
FISHINGIT/anglingtrust     -> https://fishingit.github.io/anglingtrust/   (this index)
FISHINGIT/gff              -> https://fishingit.github.io/gff/            Get Fishing Fund
FISHINGIT/re               -> https://fishingit.github.io/re/             Reel Education
FISHINGIT/rlw              -> https://fishingit.github.io/rlw/            Rod Licence Waivers
FISHINGIT/bur              -> https://fishingit.github.io/bur/            Coach Bursaries
FISHINGIT/fma              -> https://fishingit.github.io/fma/            Fishery Management Advisors
```

The index uses full URLs for the five dashboards, so it works from the `anglingtrust` repo and would also work unchanged if you ever moved it to `FISHINGIT/fishingit.github.io` to sit at the site root.

## Publishing steps

1. In the `anglingtrust` repo, add `index.html` at the root (move any existing `index.html` aside first if you want to keep it).
2. Commit and push to the branch Pages serves from (Settings, Pages, "Build and deployment" shows which).
3. If Pages is not yet on for this repo: Settings, Pages, Source "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
4. After a minute or two open https://fishingit.github.io/anglingtrust/ and click through the five cards.

## Adding or removing a dashboard

Add a new entry to the `DASHBOARDS` block (copy an existing one), add a jump link in the hero `nav`, and add a step to the "How they fit together" row if it belongs in the story. The page handles an odd number of cards by widening the last one to fill the row.

## Refreshing the index after a dashboard update

Open `index.html`, find `const DASHBOARDS` near the bottom and edit that dashboard's entry:

- `kpis`: three `["value","label"]` pairs shown as tiles on the card
- `asAt`: the date under the button ("Figures as at ...")
- `href`: only if a dashboard's address changes
- `what`, `use`, `views`: wording, if the dashboard's scope changes

The Get Fishing Fund entry is filled with `TBC` placeholders because that dashboard was not read in this session; replace them with its headline figures.

## What the index does not do

It is a static page and does not pull figures out of the dashboards automatically (each dashboard computes its own figures live from embedded rows, and GitHub Pages has no server to query them). The card figures are a snapshot you update by hand. If that becomes a chore, the next step is for each dashboard's build script to also write a small `summary.json` beside it, which the index could fetch on load, since all six sites share the `fishingit.github.io` origin.

## Public visibility

GitHub Pages sites are public to anyone with the link, whether or not the repo is private. The dashboards show organisers, clubs, schools, partners and projects as professional roles, officers as initials, and no participant, applicant or contact details, consistent with the house rules agreed for the suite.
