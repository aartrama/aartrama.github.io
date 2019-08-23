---
layout: post
title:  "Issue with different Python versions"
date:   2019-08-23 01:05:27 -0400
categories: programming
---

Recently, I found that using different python versions to run the same code can lead to different results. I created 2 environments (using Anaconda) on my computer - one with Python 3.5.1, and the other with Python 3.6.7 (latest) as follows:

{% highlight bash %}
conda create -n python351 python=3.5.1
conda create -n python374 python=3.7.4
{% endhighlight %}

First, I loaded the environment python351 -

{% highlight bash %}
conda activate python351
{% endhighlight %}

I next saved the following python code in a file called code.py.

{% highlight python %}
from collections import defaultdict

dictionary = defaultdict(list)

dictionary['one'] = 1
dictionary['two'] = 2
dictionary['three'] = 3

for keys in dictionary:
	print(keys)
{% endhighlight %}


Upon running the above code by typing `python code.py` on the terminal, I found that the results are different each time I run it! The order of the printed keys of the dictionary is different in each run. 

When I switched to python 3.7.4 using `conda activate python374` and ran the above code in a similar manner, the results in each run stayed the same. One must be very careful regarding such nuances while dealing with different python versions.





<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>