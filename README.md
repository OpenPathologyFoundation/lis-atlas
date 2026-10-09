# Global LIS Atlas (prototype)

An open, crowdsourced world map of which laboratory information system (LIS) every lab runs, who's switching, to what, and when.

> **Prototype.** Every institution, vendor, response, and number is synthetic. The LIS vendors are invented too, borrowed from Greek mythology and *The Hitchhiker's Guide to the Galaxy* (Sirius Cybernetics, Cassandra Health, Magrathea Labs, and friends).

**Live page:** https://openpathologyfoundation.github.io/lis-atlas/  
**Observable notebook:** https://observablehq.com/@gershkovich/lis-atlas

## What's in it

- **Who runs what:** world map of the most common LIS per country, small maps of where each major vendor is strongest, and the installed base, filterable by discipline (AP, CP, microbiology, blood bank), region, and institution type.
- **Who's switching:** a Sankey from current LIS to new LIS, plus the main reasons for switching.
- **Upcoming go-lives:** one dot per lab by quarter through 2030, and vendor share over time projected from scheduled go-lives.
- **Six degrees of the survey:** the referral network from the Association board outward; hover a lab to trace its chain.
- **Coverage:** countries with no responses yet, ranked by population, as the call to action for regional ambassadors.
- **Rollout:** responses and countries over time across the pilot, LinkedIn wave, and ambassador phases.
- **Privacy rules:** each lab picks a consent level in the survey (named, unnamed, or totals only), and the public view hides anything based on fewer than 5 labs. Switching plans are listed only once a lab says they're announced or under contract; "evaluating" only counts in totals. A **Show as** switch compares the public view with the raw staff view.
- **Survey (demo):** the 2–3 minute survey. Submitting adds your lab to every chart in the page for that browser session; nothing is sent anywhere.

## The notebook

The whole atlas is one file, [`docs/index.html`](docs/index.html), in Observable's open [Notebooks 2.0 format](https://observablehq.com/notebook-kit/). You can edit it in a text editor, in [Observable Desktop](https://observablehq.com/notebook-kit/desktop), or on observablehq.com. The [Observable copy](https://observablehq.com/@gershkovich/lis-atlas) is edited separately; copy changes back into `docs/index.html` to publish them here. The synthetic data generator and chart code are in the appendix cells at the bottom.

## Run locally

```bash
npm install
npm run preview
```

`npm run build` writes a static site to `docs/.observable/dist`. Every push to `main` builds the notebook and publishes it to GitHub Pages (see [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml)).

## From prototype to live

1. Point the survey (REDCap, Qualtrics, Google Forms, or similar) at a response store, with the referral code carried as a `?ref=CODE` URL parameter.
2. Replace the synthetic generator cell with a data loader that reads the cleaned responses and hides names for labs that opted out.
3. Keep the build on GitHub Actions so the page refreshes on a schedule or whenever the data changes.
