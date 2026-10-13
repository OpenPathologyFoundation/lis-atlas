# Global LIS Atlas (prototype)

An open, crowdsourced world map of anatomic pathology: which AP LIS each operation runs, where it stands with digital pathology, and which bespoke tools its informatics team has built and would share.

The unit is the **AP operation**: the group that signs out surgical pathology and cytology for one or more sites (a hospital department, an academic department, a contracted pathology group, or an independent or dermatopathology practice). Each one is counted on its own, never as part of the clinical lab that shares its building.

> **Prototype.** Every institution, vendor, tool, response, and number is synthetic. The LIS vendors are invented too, borrowed from Greek mythology and *The Hitchhiker's Guide to the Galaxy* (Sirius Cybernetics, Cassandra Health, Magrathea Labs, and friends).

**Live page:** https://openpathologyfoundation.github.io/lis-atlas/  
**Observable notebook:** https://observablehq.com/@gershkovich/lis-atlas

## What's in it

- **Who runs what:** world map of the most common AP LIS per country, small maps of where each major vendor is strongest, and the installed base, filterable by region and operation type.
- **Where digital pathology stands:** each type of operation by stage (none to primary digital), the share that would be primary digital each year if every stated target holds, the main barriers, how the image system works with the AP LIS, AI in clinical use, and digital sign-out by informatics staffing.
- **Bespoke technology:** software built by an operation's own informatics team to close gaps the core LIS leaves, what it does, whether the team would share it, and a table of tools on offer.
- **Who's switching:** a Sankey from current to new AP LIS, plus the main reasons for switching and who drives the decision.
- **Upcoming go-lives:** one dot per operation by quarter through 2030, and vendor share over time projected from scheduled go-lives.
- **Hospitals covered in the US:** each operation names the hospitals it signs out for, so coverage is measured against the public CMS hospital list (4,523 hospitals in the 50 states and DC; the only real numbers on the page). A state map of the share covered, coverage by hospital type (acute care, critical access, children's), and coverage over time.
- **Six degrees of the survey:** the referral network from the Association board outward; hover an operation to trace its chain.
- **Coverage:** countries with no responses yet, ranked by population, as the call to action for regional ambassadors.
- **Rollout:** responses and countries over time across the pilot, LinkedIn wave, and ambassador phases.
- **Privacy rules:** each operation picks a consent level in the survey (named, unnamed, or totals only), and the public view hides anything based on fewer than 5 operations. Switching plans are listed only once an operation says they're announced or under contract; "evaluating," digital pathology targets, barriers, and informatics staffing only count in totals. Tool names appear only for operations shown by name that offer to share them. A **Show as** switch compares the public view with the raw staff view.
- **Survey (demo):** a short version of the 5-minute survey. Submitting adds your operation to the charts for that browser session; nothing is sent anywhere.

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
2. Replace the synthetic generator cell with a data loader that reads the cleaned responses and hides names for operations that opted out.
3. Keep the build on GitHub Actions so the page refreshes on a schedule or whenever the data changes.
