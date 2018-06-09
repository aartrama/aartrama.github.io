---
layout: post
title:  "DESeq2 for differential expression analysis"
date:   2017-10-24 01:05:27 -0400
categories: programming
---
Tools like DESeq2 and edgeR help demonstrate the enormous power of statistics in Bioinformatics. DESeq2 is a powerful Bioconductor package which helps us perform differential expression analysis using RNA-seq data.

Let us consider a hypothetical example:

| sample | sex | treatment |
|--------|-----|-----------|
| 1      | m   | morphine  |
| 2      | f   | morphine  |
| 3      | m   | saline    |
| 4      | f   | saline    |

The model for such an experiment would be log(exp) ~ sex + treatment. Here, sex and treatment represent features (also known as covariates or factors), and there are 2 levels for each feature in this example. But this model assumes that the effect of treatment is the same for both males and females (also known as additive effect in statistics). For each feature, we add an effect regardless of what the other feature is. This model is suitable just for pairwise comparisons (male vs. female, morphine vs. saline).

To account for the interaction between sex and treatment, an 'interaction term' can be added to the model. The updated model can helps us find sex specific treatment effect OR treatment specific sex effect (female specific and male specific morphine treatment effect for instance). To do this, following is the design of the linear model:

log(exp) ~ sex + treatment + sex:treatment

This is assuming that the model matrix is full rank, i.e., we have samples for all levels of all factors. The above equation can also be written as follows:

log(exp) ~ sex * treatment

The major issues I faced with DESeq2 while 'extracting results' were:

1) What if I want to change the control group? I would have to run the model again (in the case of 2 different control groups in the same factor).

2) What if I want to compare male morphine vs. female saline? Male morphine vs. female morphine can be done, male saline vs. female saline can be done, morphine vs. saline in males can be done and morphine vs. saline in females can be done. But male morphine vs. female saline and male saline vs. female morphine cannot be extracted. 