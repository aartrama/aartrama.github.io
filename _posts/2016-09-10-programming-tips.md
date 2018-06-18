---
layout: post
title:  "Programming tips"
date:   2016-09-11 01:05:27 -0400
categories: programming
---
I've been learning to program in Python for the past 2 years, and following are some of the lessons I would like to share, and remind myself of from time to time:

* Start coding! The only way you will ever learn to code is by actually writing some code. I started to learn programming from the website [Codecademy](https://www.codecademy.com/){:target="_blank"}. Going through the python module a couple of times really helped me get a firm grip on the basic concepts. Parsing different kinds of files to extract useful information from them is a good exercise too.

* For big programming tasks, write the problem's pseudo code in a word document or on a sheet of paper. If you do not have time to write one, at least write the goal of your programming task, and how you are going to go about accomplishing it in a few simple sentences. Only then, start writing the actual code. Otherwise, you will get pretty lost in your code and/or will end up writing an inefficient one.

* If the data that you are handling is huge (many giga bytes), work with a smaller version of the dataset first. For example, just work on a test file containing just the first 10 lines from the original file.

* When working with any type of formula which you would like to incorporate in your code, be careful with where you place the brackets. 

* Avoid reinventing the wheel as much as possible. This will significantly decrease both errors as well as lines of code. For instance, instead of writing your own functions for computing the average of a list, import numpy instead.

* Comment comment comment! It is the key to writing good code. It will also help you a lot later in time, when you would want to reuse the same code.

* Naming a variable appropriately is very crucial. Give it a name that anyone can understand what it represents. 

* Print command is your best friend. Use it as often as you need for debugging/while writing codes. 

* DO NOT write nested 'if' and 'for' loop statements. It slows down your program considerably.

* Use dictionaries (python) or hashes (perl) whenever you can. These are really efficient data structures. 

* Using a good editor is really important. It makes your life a hundred times easier. I personally use [Sublime text](http://www.sublimetext.com/){:target="_blank"} to write code. If possible, master using the 'vi' editor. 

* Sometimes, you assume that you have already written a step in your code, and run the program. But do not make assumptions! Check again if you have written all the required steps for the code to run. 

* NEVER copy and paste a code from a pdf file. The pasted code will give unnecessary errors.

* Use functions whenever you can. Do NOT copy and paste the same blocks of code in your program.


<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>
