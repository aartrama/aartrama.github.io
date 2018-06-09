---
layout: post
title:  "Gene Set Enrichment Analysis"
date:   2018-01-17 01:05:27 -0400
categories: 
---
Gene set enrichment analysis is an improved version of functional enrichment analysis. This analysis considers the ranking of genes, whereas a traditional functional enrichment analysis does not. Following is the background of the analysis using an RNA-seq gene list as an example:

The following explanation is based on the paper [REPA: Applying Pathway Analysis to Genome-wide Transcription Factor Binding Data](https://ieeexplore.ieee.org/document/7152849/){:target="_blank"}

1. Gene set enrichment analysis typically requires a gene list where genes are ranked by the most significantly upregulated, to the most significantly downregulated. This is done by multiplying the sign of fold change with the negative log(p value).

**RNA-seq gene list:**

gene1 |   rank1   | <- most significantly upregulated
gene2 |   rank2	|
gene3 |   rank3|
gene4 |   rank4|
gene5 |   rank5  |  <- most significantly downregulated

2. HPO (Human Phenotype Ontology) is an example of a gene set collection. HPO has a total of approximately 7,000 gene sets; each gene set containing a large number of genes. These gene sets are converted to GMT format text files to facilitate extraction of gene names in each gene set.

3.  Genes in each gene set are compared with our list of RNA-seq genes.

4. The ranks of common genes are compared to equal number of random genes which have been assigned random ranks. Therefore, we have the following: 


**List of genes common b/w RNA-seq gene list and HPO gene set:**

gene1 |   rank1
gene3 |   rank3
gene5 |   rank5
..    |    ..

**Random genes**

randomgene1  |  rank2
randomgene2  |  rank3
randomgene3  |  rank5
..           |    ..

The ranks of the genes are compared using 'Mann-Whitney U Test' (Fisher's exact test?). Upon comparison, a p-value is obtained.

5. After we obtain p-values upon comparison of the RNA-seq gene list with each gene set, corrected p-values are calculated as follows:

Corrected P-value =  max (1-#sign.test/#total.tests, 1/#total.tests)
