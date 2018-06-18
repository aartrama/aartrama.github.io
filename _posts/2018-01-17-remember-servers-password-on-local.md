---
layout: post
title:  "Setting up ssh keys"
date:   2018-01-17 01:05:27 -0400
categories: 
---
It is annoying to have to enter the password of a server each time you try to log in. You can set up ssh keys to avoid this:

1. On your local machine, type the following:

{% highlight bash %}
ssh-keygen -t rsa
{% endhighlight %}

When prompted for the filename to save the key in, hit enter. This will save the rsa key pair to a default file 'id_rsa'. When prompted for the password, hit enter (to leave it blank). Hit enter again to repeat the password.

The above step should be done only once on your local machine.

2. Once the key's image is generated, type the following:

{% highlight bash %}
ssh-copy-id username@server
{% endhighlight %}

For example, in my case it was

{% highlight bash %}
ssh-copy-id ramaka02@minerva.hpc.mssm.edu
{% endhighlight %}

Type the password for the server one last time, and you're all set! Next time, you will not be prompted for a password.

* To set up ssh key for another server, start from Step 2.

<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
