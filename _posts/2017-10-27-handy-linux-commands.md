---
layout: post
title:  "Handy Linux commands"
date:   2016-09-27 01:05:27 -0400
categories: programming
---
Command to create a tar.gz file

{% highlight bash %}
tar -cvzf file_to_compress.tar.gz file_to_compress
{% endhighlight %}

Command to unzip a tar.gz file

{% highlight bash %}
tar -xvzf file_to_uncompress.tar.gz
{% endhighlight %}

Check GLIBC version of your system

{% highlight bash %}
ldd --version
{% endhighlight %}

Command to create a tar ball

{% highlight bash %}
tar -cvf file_to_compress.tar file_to_compress
{% endhighlight %}