# Exploratory Analysis

A growing collection of exploratory data analyses on public datasets, written in R Markdown. Each project lives in its own folder under `docs/`, with the source (`.Rmd`) and a rendered report (`index.html`) that you can view in the browser.

## Analyses

### 16S microbiome analysis across habitats
- **Question:** How do microbial communities differ across soil, water, sediment and human-associated habitats, and do conclusions change when 16S data are treated as compositional?
- **Data:** GlobalPatterns 16S dataset (26 samples, 9 habitats including mock communities; Caporaso *et al.*, *PNAS* 2011)
- **Methods:** mock-community QC and prevalence filtering; relative abundance; alpha diversity with a rarefaction check; Bray–Curtis vs CLR/Aitchison ordination; PERMANOVA with dispersion checks; genus-level differential abundance with FDR correction
- **Report:** [View HTML report](https://github.com/AdhithiRaviRaghavan/exploratory-analysis/blob/main/docs/GlobalPattens_16S_index.html)
- **Code:** [`docs/microbiome-16S/GlobalPatterns16S.Rmd`](docs/microbiome-16S/GlobalPatterns16S.Rmd)

### Maize microarray: unsupervised analysis
- **Question:** Which gene expression patterns mark nitrogen-use efficiency in maize?
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/)
- **Code:** [`docs/MaizeData.Rmd`](docs/MaizeData.Rmd)

More analyses to be added.

## Reproducing an analysis

Open the `.Rmd` in RStudio and click **Knit**, or run:

```r
rmarkdown::render("docs/microbiome-16S/GlobalPatterns16S.Rmd", output_file = "index.html")
```

Package requirements for the microbiome analysis:

```r
install.packages(c("vegan", "ggplot2", "dplyr", "tidyr", "rmarkdown"))
BiocManager::install("phyloseq")
```

