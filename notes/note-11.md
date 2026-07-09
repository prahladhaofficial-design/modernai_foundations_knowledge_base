# Modernaiintro 11


Introduction to Artificial Intelligence
Pappuri Prahladha
1 Pseudoinverse normal equation and Regularization for Linear Regression
Now we will see about regularization for linear regression. the expression (XT X)1XT is known as
the pseudoinverse of the data matrix, while the normal equation refers to the equation used in linear
regression. in high dimensional spaces, irrelevant dimensions can appear useful, leading to overfitting
in multivariable regression. to combat this, regularization is employed, minimizing both empirical
loss and hypothesis complexity:
cost(h) = empLoss(h) +   complexity(h).
complexity can be defined as L (w) = (cid:80) |w |q, where q = 1 corresponds to L1 regularization
q i i
(minimizing the sum of absolute values and producing sparse models), and q = 2 corresponds to L2
regularization (minimizing the sum of squares). L1 regularization tends to set many weights to zero,
identifying irrelevant attributes and potentially making models easier to interpret, while being less
likely to overfit compared to L2 regularization.
the visualization of regularization shows that L1 regularization leads to corner solutions with weights
of zero, whereas L2 regularization results in non-zero weights. The number of examples required
for good hypothesis performance varies: it is linear with the number of irrelevant features for L2
regularization but logarithmic for L1 regularization. L1 takes the dimensional axes seriously, leading
to different results with rotations, while L2 is rotationally invariant, treating axes as arbitrary.
2 Linear classifiers with a hard threshold
Now we will come to linear classifiers with a hard threshold.linear classifiers can utilize linear
functions for classification tasks, such as distinguishing between earthquakes and underground
explosions based on seismic data.a decision boundary, or linear separator, is defined as a line (or
surface) that separates classes. the classification hypothesis can be expressed using a vector dot
product:
h (x) = 1 if w  x  0, and 0 otherwise.
w
alternatively, it can be represented through a threshold function:
h (x) = threshold(w  x),
w
where threshold(z) = 1 if z  0 and 0 otherwise.
the perceptron learning rule updates weights according to the formula
w  w + (y  h (x))  x ,
i i w i
which allows convergence to a linear separator provided the data is linearly separable. The behavior
of this learning rule includes three cases: if the prediction is correct (y = h (x)), weights remain
w
unchanged; if the prediction is incorrect (y = 1 but h (x) = 0), weights are adjusted to increase
w
w  x; if y = 0 but h (x) = 1, weights are adjusted to decrease w  x.
w
typically, the learning rule is applied one example at a time, with random selection akin to stochastic
gradient descent. Training curves illustrate the classifiers performance improving over iterations.
The perceptron learning rule guarantees convergence to a perfect linear separator when the data is


linearly separable. However, if the data is not linearly separable, the perceptron may fail to converge,
displaying oscillations in weight updates.
to enhance convergence, a decaying learning rate  (e.g., (t) = 1000 ) can be employed, yielding
1000+t
better results compared to a fixed learning rate.it is also important to note that finding a minimum
error solution is NP-hard, often necessitating multiple presentations of examples for convergence to
be achieved.
3 Linear classification with logistic regression
Here we see about linear classification with logistic regression.linear classifiers that utilize hard
thresholds present several issues,they are not differentiable and are discontinuous, resulting in
unpredictable learning behaviors and overconfident predictions of 0 or 1. to addressing these
problems,a continuous, differentiable function can be used to replace the hard threshold.two common
functions that approximate this soft threshold are the probit function and the logistic function, with
the latter having more favorable mathematical properties.
the logistic function is defined as
1
logistic(z) = .
1 + ez
by using the logistic function, the classification hypothesis becomes
1
h (x) = logistic(w  x) = ,
w 1 + ewx
which outputs values between 0 and 1, interpretable as the probability of belonging to class 1. This
formulation results in a soft decision boundary, providing a probability of 0.5 at the center and
approaching 0 or 1 as we move away.
the process of fitting the weights in this model to minimize loss is known as logistic regression.
While there is no closed-form solution for the optimal weights, gradient descent is a straightforward
approach.the gradient is derived using the chain rule, leading to the weight update rule:
w  w + (y  h (x))  h (x)(1  h (x))  x .
i i w w w i
comparative experiments indicate that logistic regression, although somewhat slower to converge in
linearly separable cases, demonstrates more predictable behavior. In scenarios involving noise and
non-separability, logistic regression converges much more quickly and reliably. These advantages
have made logistic regression a popular choice in real world applications across various fields,
including medicine, marketing, survey analysis, credit scoring, and public health.
2
