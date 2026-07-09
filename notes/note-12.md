# Project 12


Deep learning
Pappuri Prahladha
The deep learning is a subset of machine learning that is about complex algebraic structures,known
as neural networks,with adjustable connection strengths.The term "deep" refer to the structure being
organized in multiple layers,which facilitates long computation paths from inputs to outputs.this
approach has found wide applications in areas such as visual object recognition, machine translation,
speech recognition, speech synthesis, image synthesis, and reinforcement learning.its origins can
be traced back to early models that aimed to replicate neural networks in the brain.in deep learning
we have significant advantages over simpler models.it is particularly effective in handling high-
dimensional data, such as images, and allows for complex interactions between input variables,
enabling it to capture intricate patterns in real world data.in contrast,linear models are limited to short
computation paths and can only represent linear functions, while decision trees can accommodate
longer paths but often become inefficient for larger sets of input variables.the core structure of deep
learning includes feedforward networks,which serve as the basic architecture,as well as convolutional
neural networks (CNNs) that are especially designed for vision tasks,and recurrent neural networks
(RNNs) that are adept at handling sequential data.the training process involves algorithms that
enhance generalization and performance across various tasks.
1 Simple Feedforward Networks
The feedforward networks operate with connections flowing in one direction,from input to output,and
do not contain loops.in contrast, recurrent networks allow for outputs to be fed back into inputs, cre-
ating a system with internal memory.an example of a feedforward network is a boolean circuit,which
utilizes binary inputs (0 and 1). neural networks, on the other hand, work with continuous input
values and learn by adjusting parameters to fit the training data.each node in a network,refer to as
a unit, computes a weighted sum of its inputs and applies a nonlinear activation function.common
activation functions include the sigmoid function, defined as (x) = 1 , the rectified linear unit
1+ex
given by ReLU(x) = max(0, x),the softplus function represented as softplus(x) = log(1 + ex),
and the hyperbolic tangent function, expressed as tanh(x) = e2x1 .the universal approximation
e2x+1
theorem states that two layer networks can approximate any continuous function.the computation
graph provides a structured representation of the network, making each computation explicit.in terms
of learning, gradient descent is employed for supervised learning, adjusting weights to minimize the
loss function, which can be calculated using the squared loss function L (y, hw(x)) = y  y2.the
2
chain rule from calculus is applied for gradient calculations, particularly concerning weights.however,
deep networks can encounter the vanishing gradient problem, where gradients become too small,
hampering effective learning.automatic differentiation simplifies gradient calculations across various
network architectures.additionally, end-to-end learning allows for the training of complex systems as
a whole using input/output pairs, reducing the necessity for detailed design of individual subsystems.
2 Summary of Computation Graphs for Deep Learning
we can see thet in deep learning,hypotheses are represented as computation graphs with tunable
weights,and gradients of the loss function are computed with respect to these weights for training.


2.1 Input Encoding
THe input nodes are directly connected to input data x.for factored data,boolean attributes are
represented with n input nodes, where 0 means to false and 1 to true.numeric attributes are typically
used as is, although they may be scaled or transformed to fit a specific range.image data is viewed as
3XY integer attributes, but adjacency is important.internal structures, such as convolutional layers,
maintain this semantic adjacency.categorical attributes are often encoded using one hot encoding
to avoid misleading numerical adjacency,ensuring that the relationships between categories are not
represented inaccurately.
2.2 Output Layers and Loss Functions
we can observe that on the output side, raw data values are encoded similarly to input values, and one
hot encoding is also used for categorical outputs, such as weather predictions. while the squared-error
loss function is simple, it is not always ideal, thus, the negative log likelihood is commonly used
as a loss function.this approach maximizes the probability of observed data and is equivalent to
minimizing cross entropy loss, which measures the dissimilarity between the true distribution P and
the predicted distribution Q.for binary classification, sigmoid activation functions give probabilities,
while softmax layers output categorical distributions for multi-class problems.in regression tasks,
linear output layers are employed for continuous targets, making them equivalent to classical linear
regression. additionally, mixture density layers can represent outputs using mixtures of gaussian
distributions for more complex and difficult predictions.
2.3 Hidden Layers
During the training process,each layer of a neural network transforms representations from the
previous layer, decomposing complex transformations into simpler, learnable functions.networks
can discover meaningful intermediate features, such as edges and shapes, during this process. in
the previous days,sigmoid and tanh activation functions were preferred, however, there has been a
shift towards using ReLU and softplus functions since around 2010.deep, narrow networks often
outperform shallow, wide networks for a fixed number of weights. Despite limited understanding
of why certain structures work better, practitioners gain intuition for designing and fixing networks
through experience.
2
