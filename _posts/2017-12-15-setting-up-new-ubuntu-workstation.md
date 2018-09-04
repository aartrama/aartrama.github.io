---
layout: post
title:  "Setting up a new Ubuntu workstation for Bioinformatics"
date:   2017-12-15 01:05:27 -0400
categories: programming
---
1. Add the following to ~/.bash_profile:

`alias rm='rm -i'`

set aliases for various servers you use. For example:

`alias minerva='ssh -l ramaka02 minerva.hpc.mssm.edu'`

2. Install Unity Tweak Tool to use 4 split screens.

3. Download and install [Anaconda](https://www.anaconda.com/download/#linux){:target="_blank"}.

4. Install [Sublime text](https://www.sublimetext.com/){:target="_blank"} and add license.

5. Enable minimize on click for applications on launcher. 

6. Set firefox to open new tabs to the far right. Follow [this](https://support.mozilla.org/en-US/questions/971529){:target="_blank"} tutorial.

<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
