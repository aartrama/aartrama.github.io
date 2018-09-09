---
layout: post
title:  "Handy Linux commands"
date:   2016-09-27 01:05:27 -0400
categories: programming
---

{% highlight bash %}
# Command to create a tar.gz file
tar -cvzf file_to_compress.tar.gz file_to_compress

# Command to unzip a tar.gz file
tar -xvzf file_to_uncompress.tar.gz

# Command to create a tar ball
tar -cvf file_to_compress.tar file_to_compress

# Check GLIBC version of your system
ldd --version

{% endhighlight %}

<br><br>
<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>

