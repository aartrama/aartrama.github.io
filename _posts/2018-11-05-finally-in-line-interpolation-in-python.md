---
layout: post
title:  "Finally! In line interpolation in Python"
date:   2017-11-05 01:05:27 -0400
categories: programming
---
In Bash, one can often pass a variable in an echo statement as follows:

{% highlight bash %}
VARIABLE1="Text1"
VARIABLE2="Text2"
echo This is an example string: $VARIABLE1, $VARIABLE2
{% endhighlight %}

This is really convenient in Bash. But in python 2, it is a little more complicated than that. Following is the only way one could format a string:

{% highlight python %}
variable1 = "TEXT1"
variable2 = "TEXT2"
print "This is an example string: {0}, {1}".format(variable1, variable2)
{% endhighlight %}

The above becomes tedious if one were to pass more than 10 arguments for format. Following is a better way (albeit in Python 3):

{% highlight python %}
variable1 = "TEXT1"
variable2 = "TEXT2"
print(f"This is an example string: {variable1}, {variable2}")
{% endhighlight %}

