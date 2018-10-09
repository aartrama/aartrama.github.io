---
layout: post
title:  "Bioinformatics terms"
date:   2017-12-24 01:05:27 -0400
categories: programming
---
Following are some of the common bioinformatics terms one comes across in technical papers:

1. **Coverage** - total number of mapped reads divided by the size of the reference genome [https://www.biostars.org/p/5165](https://www.biostars.org/p/5165){:target="_blank"}

| 22 | 2 | 4  | 137928 | 2.9e-05  |
| 22 | 3 | 28 | 137928 | 6.4e-05  |
| 22 | 4 | 10 | 137928 | 7.25e-05 |

The above means that 4 bases in chr22 (out of 137928 bases) have a coverage of 2 (or have been covered 2 times), 28 bases have a coverage of 3, 10 bases have a coverage of 4 and so on. 
If you want to get the average coverage, add up the product of bases per coverage [2** 4+3* 28+4* 10+...] and divide by the total number of bases [137928].


2. **Contigs** - contigs include completed chromosomes as well as incomplete chromosomes

3. **Demultiplex** - differentiate reads from each sample

4. **Barcode/adapter sequence** - the sequences used to identify a sample

Note - adapter removal does NOT drastically improve the differential expression analysis results.


5. **Soft and hard clipped bases** - 

Soft-clipped: bases in 5' and 3' of the read are NOT part of the alignment.

Hard-clipped: bases in 5' and 3' of the read are NOT part of the alignment AND those bases have been removed from the read sequence in the BAM file. The 'real' sequence length would be length of sequence + count-of-hard-clipped-bases

6. **Sequencing depth** - The number of times a particular base has been sequenced.

7. **Tags (wrt peak calling)** - The no. of reads under a peak

8. **Summit (wrt peak calling)** - The highest position of a peak 


<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
