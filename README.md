# Exploratory Analysis

A growing collection of exploratory data analyses on public and synthetic datasets, written in R Markdown. Each analysis lives in the `docs/` folder, with the source (`.Rmd`) and a rendered HTML report you can view in the browser.

## Analyses

### Gene X knockdown rescue assay: replicates, blocking and partial rescue
- **Question:** Does knocking down Gene X rescue low viability in patient-derived disease cells, and how much of the gap to healthy cells does each guide close?
- **Data:** synthetic cell-viability assay: 3 donors × 4 conditions (healthy, disease control, two Gene X guides) × 2 days × 4 wells
- **Methods:** identifying the true replicate (donor, not well) and plate/day confounding; outlier screen with sensitivity analysis; log-scale linear model on donor × day means with blocking; Dunnett comparisons against the disease control (`emmeans`); fraction of the gap rescued with a delta-method confidence interval
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/GeneXRescue.html)
- **Code:** [`docs/GeneXRescue.Rmd`](docs/GeneXRescue.Rmd)

### Human PBMC single-cell RNA-seq: clustering and cell-type annotation
- **Question:** Which cell types are present in human blood, and how robust are the clusters and labels to subsampling, normalisation and an independent pipeline?
- **Data:** 10x Genomics PBMC 3k: 2,638 peripheral blood mononuclear cells from a healthy donor
- **Methods:** Seurat QC, normalisation, PCA, graph-based clustering and UMAP; resolution sweep and subsampling stability (ARI, Jaccard); marker genes (Wilcoxon); cell-type annotation by marker-panel module scores; comparison with SCTransform and with an independent Scanpy analysis; classical vs non-classical monocyte differential expression
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/PBMCSingleCell.html)
- **Code:** [`docs/PBMCSingleCell.Rmd`](docs/PBMCSingleCell.Rmd)

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
- **Report:** [View HTML report](https://adhithiraviraghavan.github.io/exploratory-analysis/index.html)
- **Code:** [`docs/MaizeData.Rmd`](docs/MaizeData.Rmd)

More analyses to be added.

## Reproducing an analysis

Open an `.Rmd` file in RStudio and click **Knit**, or for example:

```r
rmarkdown::render("docs/MaizeGWAS.Rmd")
```

Package requirements:

```r
install.packages(c("ggplot2", "dplyr", "tidyr", "tidyverse", "emmeans", "patchwork", "ggrepel", "mclust", "vegan",
                   "randomForest", "statgenGWAS", "Seurat", "rmarkdown"))
BiocManager::install("phyloseq")
```
