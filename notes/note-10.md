# Project 10


Learning from Examples-(linear regression and
classification)
Pappuri Prahladha
Now we are moving from decision trees to linear functions for continous-valued inputs.
1 Univariate linear regression
a univariate linear function relates input x to output y in the form:
y = w x + w
1 0
where w and w are coefficients (weights). our aim is to minimize the empirical loss by finding the
0 1
weights w = [w , w ]. the squared-error loss function is defined as:
0 1
N
(cid:88)
Loss(w) = (y  (w x + w ))2.
j 1 j 0
j=1
the loss is minimized when the partial derivatives with respect to w and w are zero:
0 1

Loss(w) = 0, Loss(w) = 0.
w w
0 1
the solutions for the weights are given by:
(cid:80) (cid:80) (cid:80)
N ( x y )  ( x )( y )
w = j j j j ,
1 N ( (cid:80) x2)  ( (cid:80) x )2
j j
(cid:80) (cid:80)
y  w ( x )
w = j 1 j .
0 N
The weight space defined by w and w is two-dimensional, the loss function forms a convex shape in
0 1
this space, indicating no local minima. In conclusion, linear regression with L2 loss is straightforward,
and we can use the derived equations to compute weights directly.
2 Gradient descent
Gradient descent is a method for minimizing loss that does not include dependence on finding zeros
of derivatives and can be applied to any loss function.the method begins by selecting any point in
weight space and computing the gradient.the algorithm then moves in the steepest downhill direction,
repeating this process until convergence to a local minimum is achieved.
the algorithm can be summarized as follows: initialize weights w and repeat until convergence:

w  w   Loss(w),
i i w
i
where  is the learning rate that controls the step size.
For one training example (x, y), the partial derivatives are computed as:

Loss(w) = 2(y  h (x))  (y  (w x + w )).
w w w 1 0
i i


this leads to the results:

Loss(w) = 2(y  h (x)), Loss(w) = 2(y  h (x))  x.
w w w w
0 1
The weight updates are given by:
w  w + (y  h (x)), w  w + (y  h (x))  x.
0 0 w 1 1 w
For N training examples, the batch gradient descent updates become:
(cid:88) (cid:88)
w  w +  (y  h (x )), w  w +  (y  h (x ))  x .
0 0 j w j 1 1 j w j j
j j
This approach guarantees convergence to the global minimum (given a suitable learning rate), but the
process may be slow.
an alternative method, stochastic gradient descent (SGD), randomly selects a small subset of training
examples for each update, often using minibatches for efficiency. This approach significantly reduces
computation time while maintaining effectiveness.
Convergence in minibatch SGD is not strictly guaranteed, as it may oscillate around the minimum.
However, using a decaying learning rate can help achieve convergence. SGD is particularly useful in
online learning scenarios where data arrives incrementally.
Gradient descent is widely applied across various models, especially in neural networks, even when
dealing with non-convex loss surfaces.
3 Multi variable linear regression
multivariable linear regression extends the topic of linear regression to cases where each example is
represented as an n-element vector. The hypothesis space is defined by the function:
(cid:88)
h (x ) = w + w x + . . . + w x = w + w x .
w j 0 1 j,1 n j,n 0 i j,i
i
to handle the intercept term w in a uniform manner, we can introduce a temporary input x = 1.
0 j,0
this allows us to express the hypothesis as:
(cid:88)
h (x ) = w  x = wT x = w x .
w j j j i j,i
i
the goal is to find the weight vector w that minimizes the squared-error loss over the training
examples:
(cid:88)
w = arg min L (y , w  x ).
2 j j
w
j
using gradient descent, the update rule for each weight w can be written as:
i
(cid:88)
w  w +  (y  h (x ))  x .
i i j w j j,i
j
alternatively, we can derive an analytical solution using linear algebra.the squared-error loss can be
expressed as:
L(w) = Xw  y2.
setting the gradient of this loss to zero, we have:
 L(w) = 2XT (Xw  y) = 0.
w
the minimum-loss weight vector can then be computed as:
w = (XT X)1XT y.
the term (XT X)1XT is known as the pseudoinverse of the data matrix, and this equation is referred
to as the normal equation.
2


4 Gradient method
The gradient method aims to minimize a continuous objective function u = f (x, y, z, . . .) to find
values that satisfy u = 0 by decreasing u until it vanishes. the process begins by selecting initial
values for the variables, and then using their derivatives to update these values iteratively.
the mathematical formulation involves deriving update formulas based on small increments applied
to the variables. The iteration process continues to decrease u until a minimum or zero is reached. If
the new value of u is not minimal, the method seeks smaller values.
while the method does not always guarantee a solution, it can lead to a local minimum or stationary
point through this iterative reduction.additionally,the method can be extended to systems of equations
by minimizing a combined function such as u2 + v2 + w2 + . . . = 0.
It is important to note that the continuity of the objective function is required for effective optimization,
and we must be cautious when choosing small increments.
3
