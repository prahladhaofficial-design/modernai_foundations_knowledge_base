# Project 9


Learning from Examples
Pappuri Prahladha
Goal is nothing but selection of a hypothesis that optimally fits future examples. some stationary
assumption are future examples will resemble past ones and Each example E has the same prior
j
probability distribution.optimal fit defination is that to minimize error rate(proportion of incorrect
predictions h(x)) and use a test to estimate error rates without "peeking".In data set division we have
training data(for creating hypothesis), validation data(to evaluate and choose the best hypothesis) and
test data(for final unbiased evaluation).for handling limited data we use k-fold cross validation in
this split data into k equal subsets,each dubset serves as a validation set in turn(averaging results for
memory),common values for k are 5 or 10, extreme case:k=n(leave one out cross validation).model
selection is to choose the hypothesis space and optimization means to find the best hypothesis
within that space.model selection algorithm gradually increase model complexity and evaluate using
validation error rates,if validation error starts increasing, stop and select the best complexity,return
the trained hypothesis and its error rate on the test set.cross validation function computes average
validation error across k rounds and each round holds out a different validation set and trains on the
remaining data.based on knowledge prefer polynomials over decisioin trees and empirically deter-
mine best parameters based on validation performance.(combination of qualitative and auantitative
approaches).
1 Model Selection
In model selection algorithm it takes a learning algorithm and a hyperparameter.(eg.,size) and size
defines model complexity(e.g., number of nodes for decision trees, degree for polynomials) and
iterates from smallest to larger size, selecting the model with the lowest average error on validation
data.coming to training vs validation errors, training error(decreases monotically as model complexity
increases). in validation error for example u-shaped erro(nitially decreases, reaches a minimum,
then increases due to overfitting,Optimal model complexity is at the lowest point of the curve)
and decreasing curve (Shows initial U-shape, but then validation error decreases with increased
complexity,Optimal model complexity is at the maximum capacity).here note that the curves are in
the book.lets see about overfitting dynamics- A model perfectly fitting training data is said to have
interpolated the data,Overfitting occurs as model capacity approaches interpolation,Overfitting is
often due to excess capacity focusing on training examples rather than generalizable patterns.Different
model classes have varying behaviors with increased capacity: Some, like decision trees, tend to
overfit as complexity increases. Others, like deep neural networks and random forests, often continue
to decrease validation error with more capacity.we can compare different model classes(eg.,decision
tree vs polynomial learner) and introduce multiple hyperparameters.
2 From Error Rates to Loss in MAchine Learning
The error rate limitations are minimizing error rate is better than maximizing it, but it doesnt account
for the costs of different types of errors.Example: Classifying non-spam as spam is more problematic
than the reverse.The loss function is defined as the utility lost by making a prediction y instead of
the correct answer y, in machine learning, minimizing error rates is a common goal; however, this
approach does not fully account for the varying costs associated with different types of errors. For
instance, misclassifying a non-spam email as spam is often more problematic than the reverse. To
address this, loss functions are used to quantify the utility lost when making a prediction. The general


form of a loss function can be expressed as L(x, y, y) = Utility(y)  Utility(y), with a simplified
version focusing solely on misclassifications.
Different loss functions are defined based on their characteristics: the absolute value loss (L1)
measures the absolute difference between predicted and true values, the squared error loss (L2)
squares this difference, and the zero/one loss (L0/1) penalizes incorrect predictions uniformly. The
theoretical aim is to minimize the expected generalization loss over all possible input-output pairs,
with the best hypothesis defined as h = arg min GenLoss (h).
hH L
In practice, however, the expected generalization loss is estimated using empirical data, leading to the
empirical loss formula. Several factors can cause discrepancies between the estimated best hypothesis
and the true function. These include unrealizability, where the true function does not reside within
the hypothesis space, variance due to differences in training sets, noise from nondeterministic outputs,
and the computational complexity of exploring large hypothesis spaces.
The distinction between small-scale and large-scale learning is also significant. In small-scale
scenarios, generalization loss typically stems from approximation and estimation errors, while large-
scale learning may reveal that computational limitations dominate generalization loss, despite having
sufficient data to closely approximate the true function.
3 Regularization
regularization is actually a technique used in model selection to find a hypothesis that minimizes a
combination of empirical loss and hypothesis complexity. this total cost can be expressed as:
Cost(h) = EmpLoss(h) + Complexity(h),
where  is a hyperparameter that balances the trade-off between loss and complexity. By penalizing
complex hypotheses, regularization helps to prevent overfitting, steering the model towards simpler,
more regular functions.
in this process, two choices are crucial: the selection of a loss function (such as L1 or L2) and the
choice of a regularization function that reflects the hypothesis space. For example, in polynomial
regression, using the sum of the squares of the coefficients serves as an effective regularization
function, discouraging overly complex models.
additionally to this, dimension reduction through feature selection can simplify models by removing
irrelevant attributes. A specific feature selection technique is 2 pruning.
interestingly, empirical loss and complexity can be measured on the same scale, using bits. This
approach involves encoding the hypothesis as a Turing machine program and counting the bits
required. The minimum description length (MDL) hypothesis aims to minimize the total bit count,
effectively balancing model complexity with predictive accuracy. While this method works well in
theory, practical implementation for smaller datasets can be affected by the chosen encoding strategy,
as further discussed in probabilistic interpretations in later chapters.
4 Hyperparameter tuning
hyperparameter tuning is important for optimizing machine learning models, especially when dealing
with multiple hyperparameters or continuous values. A basic method is hand-tuning, where prac-
titioners rely on intuition and past experiences to iteratively adjust parameters based on validation
performance. For a limited number of hyperparameters, grid search offers a systematic approach
by testing all possible combinations, although it can be resource-intensive.when the combination
space is vast, random search is more efficient, as it samples hyperparameter values uniformly and
is effective for continuous variables. For computationally expensive training runs, Bayesian opti-
mization provides a sophisticated method by modeling the relationship between hyperparameters
and validation loss as a function. It balances exploitation of known good values with exploration of
new settings, often using Gaussian processes for effective function approximation.another promising
method is population-based training (PBT), which begins with random search to create a diverse
model population. Subsequent generations evolve by selecting hyperparameters informed by previous
successful runs and introducing random mutations, combining the benefits of parallel execution and
informed decision-making.
2
