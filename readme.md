# README — Coping Strategies as Mediators of Depression and Anxiety Among Parents of Children with Autism Spectrum Disorder (Bayesian&nbsp;SEM in R)

**Repository author:** Ghaith Al‑Gburi  

**Study context:** This repository accompanies an analysis exploring how coping strategies mediate the relationship between socio‑demographic factors and mental health outcomes (depression and anxiety) in Iraqi parents caring for children with autism spectrum disorder (ASD). 

---

## Quick view

Click below to view the complete analysis report and plots (rendered HTML):

[Open the full analysis report (HTML)](https://rawcdn.githack.com/GhaithAl-Gburi/ASD-coping/main/results.html)

---

## Purpose

This repository contains `Bayesian_SEM.Rmd` — an R Markdown script that performs data preprocessing, exploratory analyses of background variables, confirmatory factor analysis of Brief‑COPE items, and a Bayesian structural equation modelling (BSEM) pipeline. The aim is to examine whether coping strategies mediate the association between background variables (e.g., age, socioeconomic status, family characteristics) and parental mental health outcomes (PHQ‑9 depression and GAD‑7 anxiety).

> **Data privacy:** All participant‑level data are de‑identified.

---

## Files in this repo

- **`Bayesian_SEM.Rmd`** — Main R Markdown analysis script (SEM and sensitivity analysis).  
- **`results.html`** — Rendered report showing diagnostics, path estimates and plots.  
- **`data collection tool/`** — Folder containing the Arabic and English questionnaires and a scored version.
- **`input.csv`** — the CSV file containing the data related to the study referenced above (added following publication).
- **`LICENSE`** — GNU Affero General Public License v3.0.  
- **`readme.md`** — This documentation file.

---

## Required R version & packages

- **R version:** ≥ 4.1 recommended  
- **Required packages:** `lavaan`, `blavaan`, `rstan`, `dplyr`, `tibble`, `ggplot2`, `rmarkdown`

Install packages in R (if not already installed):

```r
install.packages(c(
  "lavaan",
  "blavaan",
  "rstan",
  "dplyr",
  "tibble",
  "ggplot2",
  "rmarkdown"
))
```

---

## Expected data format (column names)

The script expects a CSV file called `input.csv` with the variables listed below. Columns should be coded numerically or as factors where appropriate; continuous variables are automatically standardised. The variable groups correspond to background characteristics, coping strategies and mental‑health outcomes.

| Category                          | Variable names |
|----------------------------------|---------------|
| Continuous background variables   | `age`, `ses`, `no_child`, `no_asd_child`, `c_age`, `time_since`, `delay` |
| Ordinal background variable       | `birth_rank` |
| Nominal background variables      | `father`, `marital_stat`, `residence`, `consanguinity`, `living_sit`, `parent_cond`, `c_gender`, `comorbidity` |
| Coping items (Brief‑COPE)         | `sd`, `ac`, `de`, `es`, `is`, `bd`, `ve`, `pr`, `pl`, `hu`, `acc`, `re`, `sb` |
| Outcomes                          | `phq9`, `gad7` |

---

## How to run

### Option 1 — Knit in RStudio
Open `Bayesian_SEM.Rmd` in RStudio and click **Knit → HTML** to produce `results.html`.

### Option 2 — Render via the R console

```r
rmarkdown::render("Bayesian_SEM.Rmd")
```

### Option 3 — From the command line

```bash
Rscript -e "rmarkdown::render('Bayesian_SEM.Rmd')"
```

Ensure that `input.csv` is present in the working directory before running the script.

---

## Analysis workflow

The `Bayesian_SEM.Rmd` script carries out the following steps:

- **Data preprocessing:** Standardises continuous variables and computes Spearman correlations for numeric/ordinal background variables  
- **Exploratory tests:** Examines relationships between nominal and numeric/ordinal variables using Kruskal–Wallis and chi‑square tests, and computes effect sizes (η² and Cramer’s V).  
- **Confirmatory factor analysis (CFA):** Specifies a three‑factor model for Brief‑COPE (problem‑focused, emotion‑focused, avoidant) and fits the model using maximum likelihood.  
- **Bayesian SEM functions:** Defines helper functions to fit Bayesian SEM models with user‑specified normal priors on the regression paths, compute MCMC diagnostics (divergences, treedepth, BFMI, R‑hat, effective sample size), extract posterior path estimates, filter stable paths based on credible intervals and probability of direction, and collect posterior draws for sensitivity analysis.  
- **Sensitivity analysis:** Fits the SEM under a grid of beta prior standard deviations (e.g., 0.2–1.0), identifies stable paths and coping mediators, and compares parameter draws across models using the Kruskal–Wallis test to detect large differences.  
- **Visualization:** Produces plots of posterior means (with error bars) for paths exhibiting large prior sensitivity.

The rendered HTML report (`results.html`) includes tables of diagnostic statistics, path estimates, retained coping strategies, sensitivity analysis results, and interactive plots.

---

## License & citation

**License:** This repository is released under the **GNU Affero General Public License v3.0**. See the `LICENSE` file for details.

If you use or adapt this code in your own work, please cite it as follows (replace the year with the date accessed):

```
Al‑Gburi, Ghaith. (2025). ASD‑coping: Bayesian SEM analysis of coping strategies in parents of children with autism. GitHub repository. https://github.com/GhaithAl-Gburi/ASD-coping
```

---

## Contact

- **Author:** Ghaith Al‑Gburi  
- **Email:** ghaith.ali.khaleel@gmail.com  
- **GitHub:** [https://github.com/GhaithAl-Gburi](https://github.com/GhaithAl-Gburi)  
- **ORCID:** `0000‑0001‑7427‑8310`
