---
layout: post
title:  "Vectorization"
date:   2017-12-26 01:05:27 -0400
categories: programming
---

In any programming language, vectorization is a much more efficient way of dealing with numbers over writing a for loop. Following is an example in python

{% highlight python %}
x = [1, 2, 3]
y = [4, 5, 6]

def sum_of_product(x, y):
    summation = 0
    for i in range(0, len(x)):
        summation += x[i] * y[i]
    return summation
{% endhighlight %}

The above for loop can be implemented much more efficiently as follows using numpy:

{% highlight python %}
import numpy as np

x = [1, 2, 3]
y = [4, 5, 6]
def sum_of_product(x, y):     
	return np.matmul(x,y) 
{% endhighlight %}

This way, the code is efficient as well as concise.