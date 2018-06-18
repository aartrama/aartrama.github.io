---
layout: post
title:  "stringsAsFactors trouble in R"
date:   2018-06-02 01:05:27 -0400
categories: programming
---
Recently, I was reading a counts matrix into R -


{% highlight r %}
> counts <- read.table("htseq_counts_matrix.txt")
> head(counts)
                   Pool5_RNAseq_12_S33_L006 Pool5_RNAseq_19_S34_L006
ENSMUSG00000000001                     4676                     2314
ENSMUSG00000000003                        0                        0
ENSMUSG00000000028                      558                      172
ENSMUSG00000000031                    25272                     6334
ENSMUSG00000000037                       28                      118
ENSMUSG00000000049                        3                        0
                   Pool5_RNAseq_4_S29_L006 Pool5_RNAseq_5_S30_L006
ENSMUSG00000000001                    3422                    4300
ENSMUSG00000000003                       0                       0
ENSMUSG00000000028                     328                     581
ENSMUSG00000000031                    7878                   22343
ENSMUSG00000000037                     212                      21
ENSMUSG00000000049                       2                       3
                   Pool5_RNAseq_6_S31_L006 Pool5_RNAseq_7_S32_L006
ENSMUSG00000000001                    2221                     857
ENSMUSG00000000003                       0                       0
ENSMUSG00000000028                     158                     159
ENSMUSG00000000031                   27124                    3655
ENSMUSG00000000037                       5                      32
ENSMUSG00000000049                       0                       0
{% endhighlight %}

I required the counts for 2 gene IDs only. The 2 IDs were stored in a separate file called 'some_genes.txt'.

{% highlight r %}
> some_genes <- read.table("some_genes.txt")
> some_genes <- some_genes$V1
> some_genes
[1] ENSMUSG00000043587 ENSMUSG00000040276
Levels: ENSMUSG00000040276 ENSMUSG00000043587
{% endhighlight %}

The 2 IDs were ENSMUSG00000043587 and ENSMUSG00000040276. When I tried to subset the counts matrix to retain the counts of just these IDs, something unexpected happened.

{% highlight r %}
> some_genes_counts <- counts[some_genes, ]
> some_genes_counts
                   Pool5_RNAseq_12_S33_L006 Pool5_RNAseq_19_S34_L006
ENSMUSG00000000003                        0                        0
ENSMUSG00000000001                     4676                     2314
                   Pool5_RNAseq_4_S29_L006 Pool5_RNAseq_5_S30_L006
ENSMUSG00000000003                       0                       0
ENSMUSG00000000001                    3422                    4300
                   Pool5_RNAseq_6_S31_L006 Pool5_RNAseq_7_S32_L006
ENSMUSG00000000003                       0                       0
ENSMUSG00000000001                    2221                     857
{% endhighlight %}

Instead of obtaining the counts for the 2 IDs, I obtained the counts of 2 totally random genes! When I investigated further -

{% highlight r %}
> typeof(some_genes)
[1] "integer"
{% endhighlight %}

The variables in 'some_genes' were being converted to integers, and the integers were being used as the row index to subset the counts matrix. This is totally undesirable! But once I included 'stringsAsFactors = F' while reading the file into R, the problem was fixed. 

{% highlight r %}
> some_genes <- read.table("some_genes.txt", stringsAsFactors = F)
> some_genes <- some_genes$V1
> some_genes
[1] "ENSMUSG00000043587" "ENSMUSG00000040276"
> some_genes_counts <- counts[some_genes, ]
> some_genes_counts
                   Pool5_RNAseq_12_S33_L006 Pool5_RNAseq_19_S34_L006
ENSMUSG00000043587                      385                      510
ENSMUSG00000040276                        5                      942
                   Pool5_RNAseq_4_S29_L006 Pool5_RNAseq_5_S30_L006
ENSMUSG00000043587                     836                     365
ENSMUSG00000040276                    1021                       4
                   Pool5_RNAseq_6_S31_L006 Pool5_RNAseq_7_S32_L006
ENSMUSG00000043587                      44                     229
ENSMUSG00000040276                      12                     515
> typeof(some_genes)
[1] "character"
{% endhighlight %}

This time, I obtained the counts of the right set of IDs. R by default sets stringsAsFactors = T because this setting is convenient while running models using the glm() or lm() function. 

An alternative to including stringsAsFactors = F for every file you read into R is to just set -

{% highlight r %}
> options(stringsAsFactors = FALSE)
{% endhighlight %}

at the beginning of the R script

[This](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/){:target="_blank"} article was also very helpful in getting a better understanding of this problem.














<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
