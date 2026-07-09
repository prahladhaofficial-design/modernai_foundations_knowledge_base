# Modernaiintro 13


Neural Networks
Pappuri Prahladha
1 Convolutional Networks
Here we see about convulational networks.convolutional networks are made to address the unique
characteristics of image data.first,images should not be treated as just a simple vectors of pixel codes
or values due to the importance of pixel adjustancy. A fully connected layer using a megapixel
image would require an impractical number of weights(e.g., some 8-9 trillion for an RGB image),
necessitating vast training data and computational resources.
to make mitigate this, the first hidden layer is structured with local connections, where each hidden
unit only receives input from a small region of the image, thus respecting local pixel adjustancy.
additionally, features detected in one part of the image should be identifiable elsewhere,this can be
achieved by using shared weights across different hidden units for the same local region.
convolutional neural networks utilize spatially local connections and replicate weight patterns across
units. the process of applying a kernel to an image is known as convolution, which mathematically
involves a kernel sliding across the image, producing an output of reduced size depending on the
stride.
in CNNs, the output is a three-dimensional array of hidden units, where the third dimension represents
different feature detectors (kernels). The concept of receptive fields is crucial, as the receptive field
of a neuron increases with depth; deeper layers allow each unit to respond to a larger portion of the
input image. Pooling layers further influence the size of the receptive field, contributing to the overall
hierarchical feature extraction in CNNs. this structure enables CNNs to efficiently learn from images
while managing the models complexity some what easily.
1.1 Pooling and Downsampling
Pooling and downsampling are most important process in convolutional neural networks. a pooling
layer summarizes adjacent units from the preceding layer into a single value, operating similarly to a
convolution layer but using fixed operations. there are two common types of pooling, average pooling
and max pooling. average pooling computes the average of its inputs, effectively downsampling the
image by a factor equal to the stride s. this method makes us to multiscale recognition, allowing a
classifier to recognize objects at reduced sizes, which may have been too large to recognize in the
original image.max pooling, on the other hand, computes the maximum value of its inputs, indicating
the presence of a feature within the receptive field.while it can also be used for downsampling, max
pooling provides different semantic information, acting as a logical disjunction that signifies the
existence of a feature.
pooling decreases or reduces the number of weights required in subsequent layers, leading to lower
computational costs and potentially faster learning. tt is important for transitioning from image-sized
layers to the final classification layer, with both pooling and convolution layers that have strides
greater than 1 contributing to this reduction in layer size. the networks final layer typically employs
a softmax function with c output units for classification, often preceded by one or two fully connected
layers to further decrease the size of the layer.


1.2 Summary of Tensor Operations in CNNs
Tensors are multidimensional arrays that play a important role in tracking the shape of data as it
progresses through the layers of a convolutional neural network.this is important because convolution
relies on the assumption that adjacent data elements are semantically related, making it logical to
apply operations to local regions of data. additionally, describing CNNs in terms of tensor operations
enhances computational efficiency, as it allows for optimization in deep learning software, particularly
for high-performance hardware like GPUs and TPUs, which facilitate parallel processing. if we look
at an example, when training on 256256 RGB images with a minibatch size of 64, the input tensor
has a size of 256256364. When applying 96 kernels of size 553 with a stride of 2, the resulting
output tensor is 1281289664, commonly referred to as a feature map. This feature map consists
of 96 channels, each representing information extracted by one feature. Although it lacks dedicated
color channels, the feature map may still retain color information if the learning algorithm identifies
it as useful for predictions.
1.3 Residual Networks
The residual network are a powerful approach for constructing very deep networks that address the
vanishing gradient problem.traditional deep models learn representations by completely replacing
those of the previous layer, which can lead to issues if any layer fails to learn effectively.the key
idea of ResNets is to allow a layer to perturb rather than entirely replace the representation from the
previous layer, enabling better information flow throughout the network.
mathematically, this relationship is expressed as z(i) = g(i)(z(i1) + f (z(i1))), where f represents
the residual adjustment to the previous layers input.the residual function f (z) is typically modeled
as a neural network consisting of one nonlinear layer followed by a linear layer.
an important feature of ResNets is the ability to disable layers by setting certain weights to zero,
simplifying the output to z(i) = g(r)(z(i1)) and effectively allowing the input to pass through
unchanged. When using ReLU activation functions, a layer with zero weights acts as an identity
mapping, preserving the input signal.
While ResNets are frequently applied to convolutional layers in vision tasks, they are a versatile tool
applicable to various deep learning contexts, often comprising hundreds of layers. The design of
these networks is rapidly evolving, and researchers are encouraged to consult recent publications for
the latest architectures tailored to specific applications.
2 Learning algorithms
Training a neural network aims to modify its parameters to minimize the loss function on the training
set,typically using variants of stochastic gradient descent (SGD). each update in the gradient descent
process is performed as w  w   L(w), where  is the learning rate and L represents the loss
w
function.in the case of SGD, the loss is computed on a minibatch of m randomly chosen examples.this
approach helps the algorithm escape local minima and ensures that the computational cost per weight
update remains constant.the minibatch size is often selected to maximize the efficiency of parallel
computations on GPUs or TPUs, allowing independent gradient calculations.to improve convergence,
it is beneficial to use a learning rate that decreases over time, with the optimal schedule typically
determined through trial and error. However, near local or global minima, gradients estimated
from small minibatches can exhibit high variance, complicating convergence. Potential solutions
include increasing the minibatch size as training progresses or incorporating momentum to smooth
the gradients.additionally, it is important to address numerical instabilities that may arise, such as
overflow, underflow, and rounding errors, especially when using activation functions in deep networks.
Overall, the learning process often demonstrates diminishing returns, where continued training may
yield little reduction in test error, leading to potential overfitting or not accurate gradient estimates.
2.1 Computing gradients in computation graphs
The gradient of the loss function with respect to weights in a neural network is computed using
back-propagation,which passes error information from the output layer back to hidden layers.each
node in a computation graph computes a function from its inputs and sends values to subsequent
2


nodes.back-propagation involves calculating partial derivatives of the loss at each node.the backward
messages are partial derivatives of the loss, with the equation
L L L
= +
h h h
j k
allowing nodes to compute their gradients by summing incoming messages. Outgoing messages for
each node are computed using the chain rule, specifically
L L h
= .
f h f
h h
the back-propagation process begins at output nodes and propagates backward through the network,
summing gradients at internal nodes and terminating at weight nodes, providing the gradients needed
for weight updates.in networks with shared weights, such as convolutional or recurrent networks, each
shared weight is treated as a single node with multiple outgoing arcs, leading to gradient contributions
summed from each usage. back-propagation is efficient, with a computational cost linear to the
number of nodes, and can be optimized for parallel execution on GPUs or TPUs.asignificant drawback
is that back-propagation requires storing most intermediate values from the forward pass, leading to
high memory costs proportional to the number of units in the network.
2.2 Batch normalization
the batch normalization is a technique that enhance the convergence rate of stochastic gradient
descent by rescaling values at the internal layers of the network based on the examples within each
minibatch.specifically,it replaces each node value z with a new value z using the formula:
i i
z
z =  i +
i
 + 2
here,  represents the mean value of z across the minibatch,  is the standard deviation, is a small
constant added to prevent division by zero, and and  are learned parameters.this process standardize
the mean and variance of the values, making it significantly easier to train deep networks. batch
normalization helps prevent information loss when a layers weights are too small, ensuring that
the standard deviation at that layer does not decay to near zero.it also reduces the need for careful
initialization of all weights, allowing for better information propagation. finally, and  are treated
as parameters in the learning process and are fixed at their learned values after training.
3 Generalization in neural networks
for us the main goal in machine learning is not just to fit a model to the training data but to ensure
that it generalizes well to new, unseen data.this is evaluated using a separate test set.
3.1 Choosing a network architecture
The most significant focus in deep learning is on developing network architectures that generalize
effectively across various types of data, such as images, speech, text, and video. convolutional
networks are explicitly designed for spatial data, employing shared feature extraction at different
locations, while recurrent networks apply the same update rule over time for sequential data.empirical
findings show that deeper networks generally offer improved generalization performance. For
instance, an eleven-layer network often significantly outperforms a three-layer network in tasks
like image recognition. In high-dimensional input scenarios, deep learning models consistently
outperform traditional methods, demonstrating their capability to capture essential task characteristics
efficiently.
3.2 Neural Architecture Search
To choose the optimal network architecture for a specific problem is challenging, as clear guidelines
are lacking.therefore, experience and judgment play important roles in deploying effective deep
learning solutions.since the early days of neural network research, efforts have been made to automate
architecture selection.however, the vast number of potential architectures renders simple approaches
3


like grid search impractical.consequently, neural architecture search techniques have been developed
to explore this expansive state space.popular methods include evolutionary algorithms that combine
and mutate existing networks, as well as approaches framed as reinforcement learning or Bayesian
optimization.a major challenge in these methods is efficiently estimating the value of candidate
architectures, as training large networks can be time-consuming. Various strategies, such as training
on smaller datasets or learning heuristic evaluation functions, aim to expedite this evaluation process.
3.3 Weight Decay
The weight decay helps improve generalization by adding a penalty to the loss function for large
weights.this can be viewed as imposing a soft constraint on the hypothesis space, preferring models
with smaller weights unless the data strongly supports larger ones.it aligns with maximum a posteriori
(MAP) learning, where the weight distribution is treated as a Gaussian prior.
3.4 Dropout
The dropout is a technique employed to reduce test set error in neural networks by introducing
randomness during training. at each training step, dropout temporarily deactivates a randomly
selected subset of units, creating a thinned network for that iteration. This process serves as a
low-cost approximation to training an ensemble of various networks. Specifically, during training
with a minibatch size m, each node has a probability p of being multiplied by a factor of 1/p or being
set to zero. Dropout is commonly applied to hidden layer units with p = 0.5 and input units with
p = 0.8.this method encourages robustness by forcing the model to learn multiple representations
for each input, making it less reliant on any single feature.as a result, dropout promotes better
generalization, albeit at the expense of training complexity and the need for larger models.
the exploration of network architectures, regularization techniques like weight decay, and strategies
such as dropout are critical for improving performance and robustness in diverse tasks.
4
