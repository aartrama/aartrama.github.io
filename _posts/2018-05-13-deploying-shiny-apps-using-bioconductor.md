---
layout: post
title:  "Deploying bioconductor shiny apps"
date:   2018-01-09 01:05:27 -0400
categories: 
---
When I was first trying to deploy my R shiny app (which uses bioconductor packages) on shinyapps.io, I received the following error:

{% highlight r %}
> rsconnect::deployApp()
Preparing to deploy application...DONE
Uploading bundle for application: 342263...DONE
Deploying bundle: 1371638 for application: 342263 ...
Waiting for task: 525534110
  error: Parsing manifest
################################ Begin Task Log ################################
################################# End Task Log #################################
Error: Unhandled Exception: Child Task 525534111 failed: Error parsing manifest: Unable to determine package source for Bioconductor package BiocGenerics: Repository must be specified
{% endhighlight %}

In order to get rid of this error, one must make sure that the bioconductor repository is configured properly -

{% highlight r %}
> getOption("repos")
                       CRAN
"https://cran.rstudio.com/"
attr(,"RStudio")
[1] TRUE
> options(repos = BiocInstaller::biocinstallRepos())
> getOption("repos")
                                               BioCsoft
           "https://bioconductor.org/packages/3.6/bioc"
                                                BioCann
"https://bioconductor.org/packages/3.6/data/annotation"
                                                BioCexp
"https://bioconductor.org/packages/3.6/data/experiment"
                                                   CRAN
                            "https://cran.rstudio.com/"
{% endhighlight %}

Once the repository was added, I tried deploying my app again -

{% highlight r %}
> deployApp()
Preparing to deploy application...
Update application currently deployed at
https://aartrama.shinyapps.io/genenames-to-geneids/? [Y/n] Y
DONE
Uploading bundle for application: 342263...DONE
Deploying bundle: 1371644 for application: 342263 ...
Waiting for task: 525534413
  building: Building image: 1384537
  building: Fetching packages
  building: Installing packages
  building: Installing files
  building: Pushing image: 1384537
{% endhighlight %}

This time, I did not receive any errors.

Source: [https://groups.google.com/forum/#!topic/shinyapps-users/zaUay_lM-lY](https://groups.google.com/forum/#!topic/shinyapps-users/zaUay_lM-lY){:target="_blank"}


<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
