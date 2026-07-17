# Unveiling U.S. Bird Biodiversity: A Geospatial and Machine Learning Analysis

How does bird observation data vary across an urbanizing country — and
what does that tell us about which species adapt to human-altered
environments?

See the [project poster](./us-bird-biodiversity-poster.png) for a
one-page visual summary, or the [full report](./us-bird-biodiversity-report.pdf)
for the complete write-up with all charts and findings.

## Overview

Bird populations are widely used as indicators of overall ecosystem
health, making them a useful lens for studying how urbanization affects
biodiversity. This project pulls real-time observation data from the
**eBird API** — one of the largest citizen-science biodiversity projects
globally, run by the Cornell Lab of Ornithology — across ten U.S. states,
then explores geographic, seasonal, and species-level patterns to see how
bird activity varies with region and human development.

## Approach

- **Data collection**: pulled recent (30-day) bird observations from the
  eBird API across ten states (NY, CA, TX, FL, PA, IL, OH, GA, NC, MI),
  then cleaned and deduplicated the resulting dataset.
- **Geographic visualization**: built an interactive Folium map with
  clustered markers to see where observations concentrate, plus a
  latitude/longitude scatter plot colored by species.
- **Temporal analysis**: examined both seasonal (monthly) and diurnal
  (hourly) observation patterns to separate bird-behavior signal from
  observer-behavior noise.
- **Habitat classification**: grouped observations into four broad
  regional categories (Northern / Southern / Western / Eastern) based on
  latitude/longitude, then identified the top species within each.
- **NLP on species names**: used spaCy to break down bird common names
  into their component parts (adjectives and nouns) to surface naming
  patterns and generate lightweight descriptions for the most-observed
  species.
- **K-means clustering**: clustered observations geographically to
  identify activity hotspots and examine species composition within each
  cluster.

## Key findings

- Geographic and temporal patterns in the data reflect a mix of natural
  habitat, urbanization level, and observer behavior — all three show up
  entangled in citizen-science data like this, which is itself a useful
  finding for anyone using eBird-style datasets.
- The most frequently observed species are plausible candidates for
  species that are **particularly adaptable to human-altered
  environments** — a signal worth following up with more rigorous
  habitat-classification data.
- Regional habitat groupings showed real differences in which species
  dominate, suggesting urbanization's effects on bird diversity vary by
  region rather than applying uniformly.
- K-means clustering surfaced geographic hotspots of bird activity and
  gave a first look at how species composition shifts across them.
- **Bigger picture**: this project is framed explicitly as a starting
  point — a foundation for more rigorous longitudinal and
  urbanization-metric-driven research on how city expansion affects local
  ecosystems, rather than a final causal claim.

## Repository structure

```
├── us-bird-biodiversity.ipynb          # full analysis: data collection, cleaning, visualization, NLP, clustering
├── us-bird-biodiversity-report.pdf    # full write-up with all charts and findings
├── us-bird-biodiversity-poster.png     # one-page visual summary
└── README.md
```

## How to run

This notebook was originally built and run in Google Colab.

1. Get a free eBird API key at [ebird.org/api/keygen](https://ebird.org/api/keygen).
2. **Do not hardcode the key.** Set it as an environment variable before
   running, or use `getpass()` to enter it interactively in Colab:
   ```python
   import os
   api_key = os.environ.get('EBIRD_API_KEY')
   ```
3. Install dependencies: `requests`, `pandas`, `folium`, `matplotlib`,
   `seaborn`, `scikit-learn`, `spacy` (plus `en_core_web_sm` via
   `python -m spacy download en_core_web_sm`), `transformers`.
4. Run all cells top to bottom — later cells depend on the cleaned
   DataFrame built early in the notebook.

## Tools

Python · eBird API · Folium (interactive mapping) · pandas · scikit-learn
(K-means) · spaCy (NLP) · matplotlib/seaborn

## Data source

[eBird](https://ebird.org) — Cornell Lab of Ornithology's global bird
observation database, accessed via the [eBird API](https://documenter.getpostman.com/view/664302/S1ENwy59).

## Author

Anna Gutierrez — [Portfolio](https://annagtz1.github.io) · [LinkedIn](https://www.linkedin.com/in/anna-gutierrez-m-s/)
