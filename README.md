# Analysis of Plastic Pellets Quality Decline

Chemometric investigation of a quality drop in plastic pellet production, using exploratory data analysis and Principal Component Analysis (PCA) in R.

## Objective
24 batches of plastic pellets (7 classified as "Poor", 17 as "Adequate") were analyzed across six material and thermal measurements — three particle size fractions (Size5, Size10, Size15) and three thermal properties (TGA, DSC, TMA) — to identify what distinguishes failing batches and to suggest a root cause.

## Method
- Exploratory analysis: outcome distribution, boxplots by variable, correlation matrix
- **PCA** (`prcomp`, scaled) to reduce the six correlated variables to a small number of composite quality indices
- Score, scree, and loadings plots (`factoextra`) to interpret the principal components

## Key Findings
- PC1 ("Particle Size Index") and PC2 ("Thermal Stability Index") together explain **78.5%** of total variance
- Poor and Adequate batches separate cleanly in PCA space, with almost no overlap between 95% confidence ellipses
- Poor batches show a **dual-mode failure**: oversized particles *and* reduced thermal stability, occurring together — this pattern favors a raw-material/supplier issue over a slow process drift
- DSC carries no discriminating information and can be dropped from routine testing

## Tools
R, tidyverse, ggplot2, corrplot, factoextra, ggrepel

## Files
- `pellets_quality_analysis.Rmd` — full analysis, knit with `output: github_document`
- `pellets.csv` — dataset (add your own copy here; not included if restricted)

## Recommendations
Track five variables (Size5/10/15, TGA, TMA) going forward, set control limits (e.g. Size10 < 8.5, TGA > 650), and trace the seven Poor-batch lot numbers back to supplier and production records to confirm root cause.
