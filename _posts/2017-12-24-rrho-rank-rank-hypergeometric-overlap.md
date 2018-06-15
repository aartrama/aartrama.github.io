---
layout: post
title:  "RRHO (Rank Rank Hypergeometric Overlap)"
date:   2017-12-24 01:05:27 -0400
categories: programming
---
RRHO is used to find the overlap between two gene lists. To generate an RRHO, every gene in each gene list should have a log fold change and a p-value associated to it. This test does not consider a fold change or a p-value cutoff. Rather, it uses ALL the genes in the gene lists.

**Steps to generate RRHO -**

1. The first step is to identify the common genes between the 2 gene lists. If the first gene list has 300 genes, and second gene list has 290 genes, 289 genes remain in gene list 1 and 289 genes remain in gene list 2 (assuming 289 genes are common b/w the two lists).

2. Next, genes in each gene list are ranked based on the signed negative log of p-value. 'Signed' here refers to assigning a '+' or a '-' sign to the - log (p-value), depending on whether the gene is up or down-regulated. The genes at the top of the list would have the most significantly up-regulated genes, and the genes at the bottom would have the most significantly down-regulated genes.

	**Gene list 1**

	gene8  |    rank1  |   <- most significantly up-regulated
	gene53  |  rank2|
	gene6   |   rank3|
	gene1   |   rank4|
	gene5   |   rank5   | <- most significantly down-regulated
	    ...    |        ...|

	**Gene list 2**

	gene5  |    rank1|
	gene10  |  rank2|
	gene31 |   rank3|
	gene94  |  rank4|
	gene8   |   rank5|
	    ...   |          ...|


3. The ranks are then used to generate a scatter plot and to compute spearman correlation between the 2 gene lists. This is done to know whether there is a positive or a negative correlation between the 2 gene lists.

4. A step size is calculated. Step size depends upon the length of each gene list. We can consider the square root of 289, which is 17, as the step size.

5. Considering the top 17 genes in gene list 1 and top 17 genes in gene list 2, a hypergeometric test is carried out to find the significance of overlap. Next, top 17 genes from gene list 1 and top 34 genes in gene list 2 are considered, and hypergeometric test is used to find the significance. This step is carried out until we are through all 289 genes, and obtain 289 p-value measurements.

	Gene list 1  |  Gene list 2   |   p-value|
	17 genes     |   17 genes      |    ..|
	17 genes    |    34 genes     |     ..|
	17 genes     |   51 genes       |   ..|
	    ...     |              ...   |              ..|
	34 genes   |     17 genes       |   ..|
	34 genes    |    34 genes    |      ..|
	34 genes    |    51 genes     |     ..|
	    ...      |             ...         |        ..|
	289 genes  |    289 genes     |   ..|

We use this list of p-values to fill the RRHO matrix, starting from the bottom left corner. We should also apply a bonferroni correction to the p-values in the RRHO matrix. 

In the end, we obtain a 17x17 matrix for -log(p-values). This matrix is typically represented as a heat map; the color scale ranging from red (for most significant) to blue (least significant). 

 ![RRHO]({{ aartrama.github.io }}/assets/images/RRHO.gif)

[Source](https://openi.nlm.nih.gov/detailedresult.php?img=PMC4396151_12964_2015_96_Fig6_HTML&req=4){:target="_blank"}

This RRHO has a red signal in the bottom left quadrant, which represents the presence of significantly co up-regulated genes. Red denotes high significance, and blue denotes poor significance of overlap.


The 4 quadrants of the RRHO map represent the following -

| Up in list1, down in list2 | Co down-regulated |
| Co up-regulated | Up in list2, Down in list1 |


Reference: [https://academic.oup.com/nar/article/38/17/e169/1033168](https://academic.oup.com/nar/article/38/17/e169/1033168){:target="_blank"}

Caveat: The RRHO cannot represent negative correlations, i.e., if the spearman correlation is negative, the RRHO map would appear blue.
