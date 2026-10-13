# Exploratory Analysis

A growing collection of exploratory data analyses on public datasets, written in R Markdown. Each analysis lives in the `docs/` folder, with the source (`.Rmd`) and a rendered HTML report you can view in the browser.

## Analyses

### Maize flowering time: GWAS and genomic prediction
- **Question:** How does population structure confound GWAS, which correction works best, and is a polygenic trait predictable even without individually significant SNPs?
- **Data:** DROPS maize diversity panel: 246 inbred lines, ~41,700 SNPs, 10 field trials (Millet *et al.*, *Plant Physiology* 2016; data from the [`statgenGWAS`](https://github.com/Biometris/statgenGWAS) package)
- **Methods:** genotype QC; PCA of population structure; GWAS with no correction, PC covariates and a leave-one-chromosome-out linear mixed model; genomic inflation, QQ and Manhattan plots; genomic prediction (GBLUP) with repeated cross-validation
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/MaizeGWAS.html)
- **Code:** [`docs/MaizeGWAS.Rmd`](docs/MaizeGWAS.Rmd)

### 16S microbiome analysis across habitats
- **Question:** How do microbial communities differ across soil, water, sediment and human-associated habitats, and do conclusions change when 16S data are treated as compositional?
- **Data:** GlobalPatterns 16S dataset (26 samples, 9 habitats including mock communities; Caporaso *et al.*, *PNAS* 2011)
- **Methods:** mock-community QC and prevalence filtering; alpha diversity with a rarefaction check; Bray–Curtis vs CLR/Aitchison ordination; PERMANOVA with dispersion checks; differential abundance compared across relative abundance, CLR and robust CLR; random-forest habitat prediction with leave-one-out cross-validation
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/GlobalPatterns16S.html)
- **Code:** [`docs/GlobalPatterns16S.Rmd`](docs/GlobalPatterns16S.Rmd)

### Maize microarray: unsupervised analysis
- **Question:** Which gene expression patterns mark nitrogen-use efficiency in maize?
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/)
- **Code:** [`docs/MaizeData.Rmd`](docs/MaizeData.Rmd)

More analyses to be added.

## Reproducing an analysis

Open an `.Rmd` file in RStudio and click **Knit**, or for example:

```r
rmarkdown::render("docs/MaizeGWAS.Rmd")
```

Package requirements:

```r
install.packages(c("ggplot2", "dplyr", "tidyr", "vegan", "randomForest", "rmarkdown"))
BiocManager::install("phyloseq")
```
