---
layout: post
title:  "Gene Set Enrichment Analysis"
date:   2018-01-17 01:05:27 -0400
categories: 
---
Gene set enrichment analysis is an improved version of functional enrichment analysis. This analysis considers the ranking of genes, whereas a traditional functional enrichment analysis does not. Following is the background of the analysis using an RNA-seq gene list as an example:

The following explanation is based on the paper [REPA: Applying Pathway Analysis to Genome-wide Transcription Factor Binding Data](https://ieeexplore.ieee.org/document/7152849/){:target="_blank"}

 - Gene set enrichment analysis requires a gene list where genes are ranked by the most significantly upregulated, to the most significantly downregulated. This is done by multiplying the sign of fold change with -log(p-value).

**RNA-seq gene list**

gene1 |   rank1         <-- Most significantly upregulated
gene2 |   rank2	
gene3 |   rank3
gene4 |   rank4
gene5 |   rank5        <-- Most significantly downregulated

 - HPO (Human Phenotype Ontology) is an example of a gene set collection. It has close to 7,000 gene sets; each containing a large number of genes. Gene sets are converted to GMT format text files to facilitate extraction of gene names in each gene set.

 - Genes in each gene set are compared with RNA-seq gene list.

 - The ranks of common genes are compared to equal number of random genes which have been assigned random ranks. Therefore, we have the following: 


**List of genes common b/w RNA-seq gene list and HPO gene set**

gene1 |   rank1
gene3 |   rank3
gene5 |   rank5
..    |    ..

**Random genes**

randomgene1  |  rank10
randomgene2  |  rank2
randomgene3  |  rank5
..           |    ..

Note: random genes are chosen from the same gene set.

 - The ranks of genes in the 2 lists are compared using Mann-Whitney U Test. Upon comparison, a p-value is obtained. This test is repeated for 1000 times. 

 - After 1000 p-values are obtained upon comparison of the RNA-seq gene list with each gene set, corrected p-values are calculated as follows:

Corrected P-value =  max($$ \frac{1- \#sign.test}{\#total.tests}, \frac{1}{\#total.tests} $$)

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
