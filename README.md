# Multilevel modelling and simulation-based power analysis in R

A worked example of linear mixed-effects modelling for longitudinal data. It starts with the `sleepstudy` dataset as a warm-up, then simulates a 2 × 3 intervention study (digital-skills training in older adults) to check whether the model recovers known effects and to estimate statistical power.

**All data in this repository are simulated. No real participant data are used.**

**Rendered report:** https://UmutVrl.github.io/digital-skills-multilevel-analysis/multilevel-longitudinal-analysis.html

## Headline results

- With N = 120 and a true time × group effect of 0.5 points/month, estimated power is about 91%.
- With the designed effect of 1.0 point/month, power is close to 100%, even with N = 60.
- A small effect (0.25 points/month) stays below 80% power up to N = 200.
- With only three measurements per person, the data cannot detect individual differences in rate of change (random slopes), even though they were simulated. A random-intercept model was retained.

## What the project covers

- Mixed-effects models with `lme4` and `lmerTest` (random intercepts and slopes)
- Intraclass correlation (ICC) and the null model
- Choosing a random-effects structure with likelihood-ratio tests and AIC/BIC
- Model diagnostics with `performance`
- A reusable `simulate_one()` function for a longitudinal design
- Simulation-based power analysis over a grid of sample sizes and effect sizes, with a power curve

## Repository structure

- `multilevel-longitudinal-analysis.Rmd` – analysis and power simulation (R Markdown)
- `multilevel-longitudinal-analysis.html` – rendered report
- `data/simulated_digital_skills_longitudinal.csv` – simulated dataset
- `digital-skills-multilevel-analysis.Rproj` – RStudio project file (needed for `here()` paths)
- `results/power_grid.rds` - power simulation results
- `LICENSE` – MIT License

## Requirements

- R 4.x or newer
- Packages: `tidyverse`, `lme4`, `lmerTest`, `performance`, `see`, `here`, `knitr`, `rmarkdown`

## How to run

1. Clone the repository and open the `.Rproj` file in RStudio.
2. Install the packages:

```r
   install.packages(c("tidyverse", "lme4", "lmerTest", "performance",
                      "see", "here", "knitr", "rmarkdown"))
```

3. Knit `multilevel-longitudinal-analysis.Rmd`. The power simulation fits several thousand models, so the first knit can take several minutes.

## Adapting the template

Change the parameters, the `lmer()` formula and the sample-size grid in `simulate_one()` and the power chunks to fit another repeated-measures design with a continuous outcome.

## Limitations

The data are simulated with parameters chosen by the author, so power estimates depend on those assumptions. The design is balanced, has no dropout or missing data, and assumes normal errors.

## Author and license

Umut Can Vural, 2026. Released under the MIT License.