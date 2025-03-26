Tags:  [[Coding]] [[Statistics]] [[Machine Learning]] [[Deep Learning]]
Date: Aug, 17, 2024

Sources:
- /home/amir/.nb/ISLP/1.md

# Statistical learning

## What is statistical learning

We have *input variables* and we have *output variables*,
for example in the provided example there is a guy----who 
wants to predict the *sales of his product* based on--his 
*advertisement budgets* so in this case the *sales* would
be the *output variable* and the *ads budget* would----be 
the *input variable* 

*** Tip1: the input variable can change but the output can't ***
*** Tip2: inputs can be named *predictors*,-------*variables*, 
*** *independent variables* or *features* *** 

the lines in the plots represent the model that can----be
used to predict the output

so therefore we have a Y outpu and p X variables as input
and their relationship can  be written like this:
    *** Y = f(X) + epsilon0 ***
### Epsilon
epsilon is a random *error term*, which is----independent 
from X and has mean zero.

### F 
*f* is an unknown function of Xs 
*f* is the systematic info that *X* provides about *Y*.

'/home/amir/Pictures/figure2-2.png'
In this situation one must estimate *f* based on----the 
observed points. Since *Income* is a simulated data set
, f is known and is shown by the blue curve in------the 
right-hand panel of Figure 2.2. The vertical------lines 
represent the *error terms*.

In essence, statistical learning refers to a set-----of
approaches for estimating *f*.

## Why Estimate **f**?
There are two main reasons that we may wish to-estimate
*f* : *prediction* and *inference*.

### Prediction
since the error term averages to zero, we can predict Y
using:
*** ˆY = ˆf(X), *** 
where *ˆf* represents our estimate for *f* , and----*ˆY*
represents the resulting prediction for *Y* . In---this
setting, *ˆf* is often treated as a black box, in---the
sense that one is not typically concerned with------the
exact form of *ˆf*, provided that it yields----accurate
predictions for *Y*.

The accuracy of *ˆY* as a prediction for *Y* depends-on
two quantities, which we will call the reducible--error
and the irreducible error. In general, *ˆf* will not be
a perfect estimate for *f* , and this inaccuracy---will
introduce some error. This error is reducible---because
we can potentially improve the accuracy of *ˆf*------by
using the most appropriate statistical---------learning
technique to estimate *f*.

Why is the irreducible error larger than zero?------The
quantity epsilon may contain unmeasured variables--that
are useful in predicting *Y* : since we don’t---measure
them, *f* cannot use them for its prediction.

"/home/amir/pictures/2-3.png"

where *E(Y − ˆY )2* represents the average, or-expected
value, of the squared expected value difference between
the predicted and actual value of *Y* ,-------------and 
*Var(epsilon)* represents the variance associated--with
the error term *epsilon*.

### Inference

We want to understand the relationship between *X*--and
*Y*, or more specifically, to understand how *Y* chang-
-es as a function of Xs.

Now *ˆf* cannot be treated as a blackbox, because----we
need to know its exact form. In this setting, one may--
be interested in answering the following questions:
 - Which predictors are associated with the response? It
is often the case that only a small fraction of-----the
available predictors are substantially associated--with
*Y* . Identifying the few important predictors among--a
large set of possible variables can be extremely useful
, depending on the application.
 - What is the relationship between the response and ea-
-ch predictor?
Some predictors may have a positive relationship with-
*Y*, in the sense that increasing the predictor is ass-
-ociated with increasing values of *Y* . Other predict-
-ors may have the opposite relationship. Depending on--
the complexity of *f* , the relationship between the---
response and a given predictor may also depend on the--
values of the other predictors. Can the relationship---
between *Y* and each predictor be adequately summarized
using a linear equation, or is the relationship more---
complicated? Historically, most methods for estimating-
*f* have taken a linear form. In some situations, such-
an assumption is reasonable or even desirable. But oft-
-en the true relationship is morecomplicated, in which-
case a linear model may not provide an accurate repres-
-entation of the relationship between the input and----
output variables.

[red until page 32]
