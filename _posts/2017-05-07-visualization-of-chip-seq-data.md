---
layout: post
title:  "Visualization of ChIP-seq data"
date:   2017-05-07 01:05:27 -0400
categories: programming
---
For visualization of ChIP-seq datasets, it is always recommended to convert bedgraph files obtained from MACS to bigwig format files prior to visualization on the UCSC genome browser. Following are the steps to be followed for the conversion: 

1. To sort bedgraph output files from MACS, use the following command

{% highlight bash %}
LC_COLLATE=C sort -k1,1 -k2,2n filename.bdg > sorted.filename.bdg
{% endhighlight %}

2. (OPTIONAL) Once all files (control and treated) have been sorted, the next step is to remove the last line from each of the sorted files. This can be done using the following code:

{% highlight bash %}
head -n -1 sorted.filename.bdg > temp.sorted.filename.bdg ; mv temp.sorted.filename.bdg sorted.filename.bdg
{% endhighlight %}

* credits - http://stackoverflow.com/questions/4881930/remove-the-last-line-from-a-file-in-bash


3. (OPTIONAL) Next, the sorted files should be clipped using the tool bedClip. Following is the command to be used:

{% highlight bash %}
bedClip sorted.filename.bdg hg38.chrom.sizes sorted.clipped.filename.bdg
{% endhighlight %}

Where hg38.chrom.sizes is a tab delimited text file that contains chromosome name (without 'chr' in the beginning of each line) in the first column and chromosome size in the second column. This information can be obtained from SAM files of the same datasets generated using a reference from ENSEMBL . 


4. (OPTIONAL) The next step would be to add 'chr' to each line in all bedgraph files, as UCSC file format requires 'chr' to be present before each chromosome name (for chromosomes 1-22, X and Y). I do this using a custom python script as follows:

{% highlight python %}
"""
This program is for adding
chr to each line of the bdg
file if line starts with
1-22, x or y
"""

# INSERTION OF FILE NAMES

files = ['sorted.clipped.filename.bdg', \
 'sorted.clipped.filename1.bdg', \
 'sorted.clipped.filename2.bdg', \
 'sorted.clipped.filename3.bdg']

# CREATION OF LIST OF CHROMOSOMES

list1 = ['X', 'Y', 'MT']

for i in range(1, 23):
    list1.append(str(i))

for file in files:
    with open(file, "r") as f, \
    open("chr."+file, "w") as outfile:
    for lines in f:
        lines = lines.strip().split()
        if lines[0] in list1:
            print>>outfile, "chr"+"\t".join(lines)
{% endhighlight %}

5. The final step is the conversion of bedgraph file to bigwig file. To do this, bedGraphToBigWig tool from UCSC can be utilized. Following is the command (note that hg38.chrom.sizes should have 'chr' at the beginning of each chromosome here):

{% highlight bash %}
bedGraphToBigWig sorted.clipped.filename.bdg hg38.chrom.sizes filename.bw
{% endhighlight %}

You can now upload the bw files in a web server and provide the link to these files in 'custom tracks' of UCSC Genome Browser.