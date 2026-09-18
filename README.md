# The Timing of the Threat: Mainstream Parties' Responses to the Populist Radical Right

Replication code and data for the Master's Thesis of **Carlos Morán García-Quijada**, Master in Computational Social Science, Universidad Carlos III de Madrid (2025–2026).

## Repository contents

| File | Description |
|---|---|
| `ches_analysis_final.Rmd` | Comparative analysis (Chapel Hill Expert Survey, 1999–2024) |
| `MARPOR_analysis_final.Rmd` | Spanish case study (Manifesto Project) |
| `1999-2024_CHES_dataset_meansV2.csv` | CHES trend file, unmodified |
| `1999-2024_CHES_codebook.pdf` | CHES codebook |
| `MPDataset_MPDS2025a.csv`, `parties_MPDataset_MPDS2025a.csv`, `parties_long_MPDataset_MPDS2025a.csv` | Manifesto Project dataset and party lists (version 2025a), included for reference |
| `codebook_MPDataset_MPDS2025a.pdf`, `codebook_Partylist_MPDS2025a.pdf`, `manifestoRworkflow.pdf` | Manifesto Project documentation |
| `tfm_carlosmoran.Rproj` | RStudio project file |

## What each script does

**`ches_analysis_final.Rmd`**. Defines treatment as the first CHES wave in which a radical right party holds at least 5% of national parliamentary seats, builds a party-wave panel of mainstream parties (conservative, liberal, Christian-democratic and socialist families) in Western Europe, and estimates average treatment effects with the Callaway and Sant'Anna (2021) estimator, using not-yet-treated units as controls and clustering by country. A TWFE model and a Sun–Abraham event study are reported as benchmarks. Outcomes are GAL–TAN, immigration policy and immigration salience; economic left–right is used as a placebo. Robustness checks cover a never-treated control group, 5% and 10% pre-treatment vote-share samples, an alternative cultural indicator, and dynamic (event-time) effects. It produces Tables 3.1, 3.2, 4.1, A.1, B.1 and B.2 and Figures 4.1, 4.2, B.1 and B.2 of the thesis.

**`MARPOR_analysis_final.Rmd`**. Downloads the coded manifestos of PP and PSOE through the Manifesto Project API, computes mean category shares before and after April 2019, and builds a *Net Nativist Lean* index (share of nativist-congruent quasi-sentences minus the share of cosmopolitan ones). It also runs a TF-IDF analysis, a glossary-based frequency measure of nativist and security terms, and a co-occurrence analysis around immigration vocabulary. It produces Tables 4.2 and A.2 and Figure 4.3.

## Requirements

Install the packages with:

```r
install.packages(c(
  "tidyverse", "fixest", "did", "knitr", "kableExtra", "flextable",
  "stargazer", "patchwork", "officer", "manifestoR", "quanteda",
  "tidytext", "scales", "lubridate"
))
```

## How to reproduce

1. Clone or download this repository and open `tfm_carlosmoran.Rproj`, so that the working directory is the project folder.
2. Run `ches_analysis_final.Rmd` chunk by chunk, in order, or knit it. It needs no further setup: the CHES data file is read from the project folder.
3. For `MARPOR_analysis_final.Rmd`, request a free API key at <https://manifesto-project.wzb.eu> (Profile → API key), save it as a one-line text file named `manifesto_apikey.txt` in the project folder, and then run the script in order. The key is personal and is not included in this repository.

Tables (`.docx`, `.html`) and figures (`.png`, 600 dpi) are written to the project folder. Random seeds are fixed for the main bootstrap estimates and for the sampled quotations.
.
