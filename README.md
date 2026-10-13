# Exploratory Analysis

A growing collection of exploratory data analyses on public datasets, written in R Markdown. Each analysis lives in the `docs/` folder, with the source (`.Rmd`) and a rendered HTML report you can view in the browser.

## Analyses

### 16S microbiome analysis across habitats
- **Question:** How do microbial communities differ across soil, water, sediment and human-associated habitats, and do conclusions change when 16S data are treated as compositional?
- **Data:** GlobalPatterns 16S dataset (26 samples, 9 habitats including mock communities; Caporaso *et al.*, *PNAS* 2011)
- **Methods:** mock-community QC and prevalence filtering; alpha diversity with a rarefaction check; Bray–Curtis vs CLR/Aitchison ordination; PERMANOVA with dispersion checks; differential abundance with FDR correction, compared across relative abundance, CLR and robust CLR, with pseudocount sensitivity; random-forest habitat prediction with leave-one-out cross-validation, a shuffled-label baseline, failure analysis and feature-importance stability
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/GlobalPatterns16S.html)
- **Code:** [`docs/GlobalPatterns16S.Rmd`](docs/GlobalPatterns16S.Rmd)

### Maize microarray: unsupervised analysis
- **Question:** Which gene expression patterns mark nitrogen-use efficiency in maize?
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/)
- **Code:** [`docs/MaizeData.Rmd`](docs/MaizeData.Rmd)

More analyses to be added.

## Reproducing an analysis

Open the `.Rmd` in RStudio and click **Knit**, or run:

```r
rmarkdown::render("docs/GlobalPatterns16S.Rmd", output_file = "GlobalPatterns16S.html")
```

Package requirements for the microbiome analysis:

```r
install.packages(c("vegan", "ggplot2", "dplyr", "tidyr", "randomForest", "rmarkdown"))
BiocManager::install("phyloseq")
```

