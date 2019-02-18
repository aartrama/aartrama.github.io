---
layout: post
title:  "Bioinformatics tools"
date:   2017-12-24 01:05:27 -0400
categories: programming
---

1) Tools for quality control and adapter trimming - 

**FastQC** - Checking the quality of raw reads, requires little memory,

**cutadapt** - Trimming the adapter sequences, supports wider range of sequencing platforms compared to fastx toolkit

**Fastx toolkit** - Checking read quality, trimming adapter sequences

**RNA-Seqc** - RNA-SeQC is used after FASTQC, which allows users to investigate the yield, alignment and duplication rate, GC bias, rRNA contamination rate, exon vs intron region vs intragenic alignment, 3’5’ bias, coverage, computationally intensive

**ngsplot** - Finding overall coverage of raw RNA-seq reads from transcription start site to transcription end site

**TrimGalore** - wrapper of cutadapt and fastqc

<br>

2) Tools for alignment - 


**Bowtie** - Aligner, not splice aware

**Bowtie2** - Aligner, not splice aware

**Tophat** - Aligner, splice aware, successor of bowtie (wraps around bowtie), splice detection

**Tophat2** - Aligner, splice aware

**HISAT** (Hierarchical indexing for spliced alignment of Transcripts) - A fast aligner, splice aware, specific to RNA, does NOT do soft clipping

**HISAT2** - A fast aligner, splice aware, specific to RNA, Soft clipping done

**STAR** (Spliced Transcripts Alignment to a Reference) - A fast aligner (similar to HISAT), splice aware

**BWA** (Burrow wheeler aligner) - DNA aligner

**Trinity** - De novo transcriptome assembly

**BSMAP** - tolerate conversion of c to t in bisulfite sequencing

**Bismark** - tolerate conversion of c to t in bisulfite sequencing

**Cufflinks** - denovo transcriptome assembly

<br>

3) Misc -

**SAMtools** - conversion of sam to bam, bam to sorted bam, removal of duplicate reads

**Bedtools** - bedintersect, 

**Cuffmerge**

**picard** - removal of duplicate reads, merging sam files

**diffRepeats** - quantify repeat element enrichment / differential analysis of repeat elements in the DNA, algning short reads to a database of repeat sequences

**diffReps** - differential enrichment of a histone mark/transcription factor

**mirdeep** - de novo prediction of miRNA from RNA-seq data

**ngsplot** - can accept large files, runs with small memory footprints

**phantompeek** 

**chippeekanno** 

**region_analysis** 

**GeneOverlap** - used to find the overlap between 2 sets of genes

<br>

4) Identification of splicing events - 

**rMATS** - exon skipping, intron retention

**MISO** - Mixture of isoforms, intron retention, skipped exon, mutually exclusive and alternative 3' UTR, splicing ratio b/w isoforms of same gene, splicing ratio between same isoform from 2 different conditions, uses bayesian theorem to iteratively infer splicing ratio. Allows to infer splicing ratios, both among isoforms of the same gene and between 2 conditions for the same isoform. Helps to identify contribution of histone/tf in regulation of AS.

<br>

5) Peak calling -

**DANPOS**

**MACS**

**Homer**

<br>

6) Quantification of aligned reads -

**Cufflinks** - Transcriptome abundance, de-novo transcriptome assembly, based on maximum likelihood principle, groups transcripts with the same transcription start site

**StringTie** - Transcriptome abundance, exon level quantification

**Sailfish** - no need of aligner, direct quantification

<br>

7) Differential expression analysis - 

**Cuffdiff** - following cufflinks, generates high false positives

**Cuffdiff2** - generates high false positives

**edgeR** - Based on bayesian methods, negative binomial testing

**DEseq** - Based on bayesian methods, local regression, generates high false negatives (highly conservative output)

**Limma** 

**Voom** - models the mean variance relationship on log transformed read counts

**htseq count**

<br>
8) Differential chip-seq analysis -

**diffReps** - to compare differential enrichment of a histone mark/transcription factor b/w 2 conditions, takes into account biological variations between a group of samples

<br>
9) Remove batch or unwanted effects from RNA-seq datasets - 

**ComBat**

**BatchQC**

<br>
10) Bioinformatics databases -

**repbase** - documents repetitive DNA sequences across eukaryotic species

**miRbase** 

**piRNAbank** 

**lncRNAdb** 

**snornabase** 

**SILVA** 

**Rfam** 

**NONCODE** 

**fRNAdb** 

<br>
11) Tool for sampling reads from a fastq file -

**seqtk**

<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
