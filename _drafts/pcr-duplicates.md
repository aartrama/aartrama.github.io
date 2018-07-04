---
layout: post
title:  "Duplicate reads in sequencing data"
---

Duplicate reads are those which map to the exact same location in the genome. It is always recommended to remove duplicate reads from ChIP-seq data, but not so much for RNA-seq. Why so?

During sample preparation for ChIP-seq, it is highly unlikely for sonication to break the genomic sequence at the same location more than two times. So the redundant reads are most likely PCR duplicates.

http://seqanswers.com/forums/showthread.php?t=6854


<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>