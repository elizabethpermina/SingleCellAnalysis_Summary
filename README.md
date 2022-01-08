# SC analysis summary
this SC analysis had the objective of finding what genes are overexpressed in the absence of the cancer driver gene.

It is a simple summary. The file is not runnable as I cannot attach the data I used, but it is easily adaptable for other datasets. I skipped some steps that are often discussed in SC tutorials.

## Steps covered

### dimentionality reduction

Selecting the gene set with a higher variance to base the dimensionality reduction procedures allows us to save time, computer power and sanity: usually, even bulk RNA-seq data is too big to run PCA or MDR plots on the whole data set. To make sure we have the best representation we select a group of genes with the variance above a certain cut-off. Often these cut-offs are set arbitrarily, like selecting the 500 most variable genes in the set.

#### PCA 
PCA is done using scater package function plotPCA()

#### tSNE

t-SNE is done with comparing different perplexity settings

the code for the t-SNE plot shows the selection of custom gene expression levels for plot colours.

### Differential expression

The problem with single-cell data when compared to bulk RNA-seq is zero inflation: while in a cell population most genes will have some reading, in each individual cell a lot of genes will have close to 0 reads. A standard DE workflow often shows these genes as if they have a significant expression change, when in fact these changes are negligible. estimateDisp() is used here as an acceptable way of dealing with zero-inflated data.

### Gene categories enrichment analysis

The code here shows how to use REACTOME database for gene set enrichment and goseq package (this code chunk credits to @mikblacklab)
