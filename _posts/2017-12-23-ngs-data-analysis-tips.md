---
layout: post
title:  "NGS Data analysis tips"
date:   2017-12-23 01:05:27 -0400
categories: programming
---
Following are some suggestions while analyzing NGS datasets -

1. NEVER delete the outputs of a particular step if the output generation has failed for SOME of the samples. Complete running the pipeline only for the samples which have failed. It might be tempting to delete everything and start all over again (for that particular step), but NEVER do that! It is a waste of your time and resource. Value what you already have! You never know, the next new set of runs might get stuck on queue on the cluster environment. You can always process the remaining samples later on, as managing a small number of samples is easier than managing a large number of samples.

2. Before submitting multiple jobs on a cluster, submit a job for one sample first. Also, submit by setting a small walltime. If that works, submit the remaining jobs.

3. On a cluster environment, leaving a job running is better than killing a job. Killing a job penalizes your account, and your subsequent jobs are accepted with delays.

4. Whenever you cannot get a bioinformatics tool working, try the following -
* Read the manual/command line options and check if you have missed something 
* Check for spelling mistakes when you manually edit files. AVOID MANUALLY EDITING FILES as much as possible in the first place!
* Check the file format of your input files. For example, format your BED files to have 6 fields instead of 3
* Check if 'chr1' is present in one input file and '1' is present in the other 
* Email the authors/google the query
* Look at the tool's source code 

5. To check whether a bam file is sorted, if you are able to index the file using `samtools index file_name`, then the file is sorted. The headers of the sam file are unreliable. The older versions of samtools report SO:unsorted even though the file could be actually sorted!

6. Fold change and log fold change are 2 different terms. Do not mistake one for the other.

7. Merging fastq files is not a good idea. Instead, merging the bam files is better.

8. Whenever you would like to visualize expression data as a heatmap, it is best to log transform the data before visualization. Vst or rlog transform can be used.

9. Automate your process wherever possible! Accomplishing tasks manually is not only error prone, but also a waste of time.

10. DO NOT copy a piece of code from the terminal window, paste it somewhere else and try to run it. The format of the copied code would have changed.


<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
