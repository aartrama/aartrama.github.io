---
layout: post
title:  "Git and GitHub Basics"
date:   2017-10-27 01:05:27 -0400
categories: programming
---
GitHub and Git may seem daunting at first, but is actually pretty straightforward. The following tutorial assumes that you have installed Git on you local machine and you have created a GitHub account.

**Create a repository on GitHub -**

1. Click on 'Create a new repository' (or go to [https://github.com/new](https://github.com/new){:target="_blank"} after logging in). Here, you can name your repository and add a description. Always initialize the repository with a README.
2. Once you create a repository, navigate to the right side of the screen. Click on the green 'clone or download' icon and copy the link.
3. Go to the terminal on your computer, change to the directory where you want to place the repository and type `git clone` followed by the information you just copied.

**Establish a connection between your GitHub account and Git -**

Type the following on your terminal -

{% highlight bash %}
git config --global user.name "github_username"
{% endhighlight %}

Replace github_username with your own GitHub username.

**Basic Git commands to know -**

Change into your cloned repository on your local machine, create a new .txt file with few lines in it, and try the following commands -

1. `git status` (to check the status of the repository)
2. `git add` (to add untracked files on your local machine to the respository)
3. `git commit -m "This is a commit"` (Replace 'This is a commit' with a useful commit message)
4. `git push` ('push' the changes you made on your local machine to the GitHub repository)
5. `git pull` (to sync with changes others in your team have made to the repository)


<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
