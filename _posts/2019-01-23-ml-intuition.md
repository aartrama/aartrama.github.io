---
layout: post
title:  "Machine Learning Intuition"
date:   2019-01-23 01:05:27 -0400
categories: programming
---

Let's assume we have a matrix of 1000 training examples (houses) as rows, and 10 features (distance to downtown, sq. foot of house, no. of schools...) as columns. The last column y denotes the house's affordability - expensive (1) or cheap (0). 

**Houses** | **Dist. to downtown** | **Sq. Foot** | **No. of schools** | .. | **y** | 
house #1 | 24 | 2000 | 3 | .. | 1 |
house #2 | 54 | 1500 | 2 | .. | 1 |
house #3 | 23 | 1000 | 5 | .. | 0 |
.. | .. | .. | .. | .. | .. |
house #1000 | 78 | 1200 | 3 | .. | 0 | 

The above is our training set. Our aim is to predict the affordability (cheap or expensive) of 50 test houses, which is our test set. 
<br>
<br>
**Step 1: Initialization** 

We initialize an equation  `y = σ(β0 + β1*x1 + β2*x2 ... β10*x10)`. β0 is the price of the house when we don't have information on the features of the house, or the average cost of the house. The following variables are initialized to zero -
 - β0, β1, β2 ... β10
 - dJ/dβ0, dJ/dβ1 ... dJ/dβ10 (Derivative/slope of cost function J w.r.t. dβX, where X = 0, 1, 2 ... 10)
 - Cost function J

<br>

Steps 2 and 3 are carried out for each training example in a vectorized manner -

<br>
**Step 2: Computation of loss** 

We calculate ŷ (predicted y) using x1, x2, x3 ... and βs, where ŷ ranges from 0 to 1. Using ŷ and y, we compute the loss, and add it to the initialized J. Loss is computed using the cross-entropy loss formula `loss = −(ylog(ŷ)+(1−y)log(1−ŷ))`.
<br>
<br>

**Step 3: Gradient Descent** 

Using y, we compute the derivative of J w.r.t. z, or dJ/dz, where `z = σ(β0 + β1*x1 + β2*x2 ...β10*x10`, z being the affordability of a single house. Using dJ/dz, we compute the derivative of J w.r.t. βX, and add them to initialized dJ/dβX (where X = 0, 1, 2 ... 10). 
<br>
<br>
**Step 4: Update Parameters**

Initialized βs get updated: β0 += (alpha * dJ/dβ0) / m, β1 += (alpha * dJ/dβ1) / m ...

Cost function J also gets updated: J = J/m 

dJ/dβ0, dJ/dβ1, dJ/dβ2 ... are reset to 0. Values of J for each iteration are stored in a list, and J is reset to 0.
<br>
<br>

Steps 2, 3 and 4 are repeated until J is minimized (or until the no. of iterations are exhausted). In the end, we have the optimal values for β0, β1, β2 ... which we may use to make predictions on the test set. 
<br>
<br>
<br>


<div class="Previous-next">
  {% if page.previous.url %}
    <a class="previous" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" style="float:right" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>