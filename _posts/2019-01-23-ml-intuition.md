---
layout: post
title:  "Machine Learning Intuition"
date:   2019-01-23 01:05:27 -0400
categories: programming
---

Let us assume that we have a matrix of 1000 training examples (houses) as rows, and 10 features (distance to downtown, sq. foot of house, no. of schools...) as columns. The last column is y, which denotes the house's affordability - expensive (1) or cheap (0). 

**Houses** | **Distance to DT** | **Sq. Foot** | **No. of schools** | .. | **y** | 
house 1 | 24 | 2313 | 3 | .. | 1 |
house 2 | 54 | 1234 | 2 | .. | 1 |
house 3 | 23 | 1000 | 5 | .. | 0 |
.. | .. | .. | .. | .. | .. |
house 1000 | 78 | 2590 | 3 | .. | 0 | 

Our aim is to predict the affordability (cheap or expensive) of 50 test houses. 
<br>
<br>
**Step 1: Initialization** 

We initializes an equation  `y = σ (β0 + β1*x1 + β2*x2 ... β10*x10)`. β0 is the price of the house when we don't have information on the features of the house (the average cost of the house). The following variables are initialized to zero -
 - all βs
 - Cost function (J)
 - d(J)/dβ1 (i.e. the derivative of cost function with respect to dβ1)
 - d(J)/dβ2 and so on ... d(J)/dβ10
 - d(J)/dβ0 

<br>
Steps 2 and 3 are carried out for each training example in a vectorized manner -


**Step 2: Computation of loss** 

The algorithm estimates y using x1, x2, x3 ... and βs. Upon estimating y, it computes the loss using the actual y value, and adds it to the initialized J.
<br>

**Step 3: Gradient Descent** 

Using  y, the algorithm computes the derivative (or slope) of J wrt z, or dJ/dz (where z = σ (β0 + β1*x1 + β2*x2 ...β10*x10, z being the affordability of THAT particular house). Using dJ/dz, the algorithm computes the derivative of J wrt each βs, and adds them to initialized dJ/dβs. Using dJ/dz, it also computes the derivative of dJ wrt β0 and adds it to the initialized dJ/dβ0. 
<br>

**Step 4: Update Parameters**

The initialized βs and β0 get updated 
 - βs += (alpha * dJ/dβs) / m , 
 - β0 += (alpha * dJ/dβ0) / m

<br>
Cost function J also gets updated
 - J = J/m 

<br>
dJ/dβ1 is reset to 0, dJ/dβ2 is reset to 0...., dJ/dβ0 is reset to 0. J values for each iteration are stored in a list, and J is reset to 0.
<br>
<br>

REPEAT step 2, 3 and 4 until J is minimized (or until the no. of iterations are exhausted). In the end, we have a set of optimal parameters βs, which we may use to make predictions on the test dataset. Note that predicted y (y_pred) would always be a number between 0 and 1. We may set a cutoff of y_pred < 0.5 to report the prediction to be cheap. 
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