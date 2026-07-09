# Project 8


LEARNING FROM EXAMPLES
Pappuri Prahladha
An agent improves performance by observing the world learning varies in complexity from simple
tasks to profound insights.machine learning simply means that When computers learn from data
to build models that help solve problems.now the reasons for machine learning are 1.unpredictable
situations(Designers cant foresee all future scenarios, e.g., a robot needs to learn new maze layouts,
or stock market predictions must adapt to changing conditions),2.complex tasks(ome tasks are difficult
to program explicitly, such as recognizing faces, making machine learning a practical solution)
1 Forms of Learning
Generally any component of an agent program can improve through machine learning.The improve-
ment depends on which component is being improved,the prior knowledge of the the agent and
available data and feedback.in agents components we have direct mapping from current state con-
ditions to actions,inference of relevant properties from percept sequences,Knowledge about world
evolution and action results,Utility information indicating desirability of world states,Action-value
information indicating desirability of actions,Goals describing desirable states and Mechanisms for
improvement (problem generator, critic, learning element).We can observe some learning examples
like a self-driving car learns to brake by observing human drivers and camera images,machine learn-
ing has dramatically improved various software applications, like galaxy image analysis and energy
efficiency in data centers.machine learning in software engineering is the integral part of modern
software systems,enhancing efficiency and effectiveness.generalizing from the specific observations is
called induction and deduction is that conclusions are guaranteed correct if premises are true.the input
representation is focused on factored representations (vectors of attributes) but can also include other
data structures.learning problems are divided into two classes classification problems (predicting
discrete outcomes) and regression(predicting continuos outcomes).In types of feed back we have
three classes, supervised learning(learn from input-output pairs),unsupervised learning(identifies
patterns without explicitly feedback like clustering similar images) and reinforcement learning(learns
form rewards and punishments, aiming to maximize future rewards like winning or loosing a chess)
2 Supervised Learning
The definition of supervised learning is that it aims to discover a function h that approximates function
f based on a training set of input-output pairs(x,y). Training set is composed of N example pairs
(x1,y1),(x2,y2),......,(xN,yN).Hypothesis is the function h drawn from a hypothesis space H.The
output y represents the true answer we want to predict(Ground truth).in choosing a hypothesis space,
utilize prior knowledge or perform explanatory data analysis through statistical tests and visualizations
and multiple hypothesis spaces can be tested to find the most effective one.In evaluating hypothesis,a
good hypothesis fits the training data but most also generalize well to unseen data(test set) and
generalization is the ability of h to accurately predict outputs for new inputs. Some examples of
hypothesis spaces are Straight lines, sinusoidal functions, piecewise-linear functions, and high-degree
polynomials,Higher-degree polynomials can fit training data perfectly but may not generalize well
(overfitting).The tendency of a hypothesis to deviate from expected values due to constraints of the
hypothesis space is called bias and High bias can lead to underfitting, where patterns in the data are not
captured.Variance is the sensitivity of the hypothesis to fluctuations in training data and High variance
can lead to overfitting, where the model performs poorly on unseen data.balancing complexity(low-
bias) and simplicity(low-variance) is crucial for effective learning.probabilistic approaches selects the


most probable hypothesis given the data using bayesian principles can guide hypothesis selection.there
is a tradeoff between the expressiveness of a hypothesis space and the complexity of finding a good
hypothesis.simpler hypothesis spaces are preferred for efficient computation and usability.
3 Example:Restaurant Waiting
The goal is to determine whether to wait for a table at a restaurent or not.the output will be a boolean
variable (WillWait)(true if waiting, false otherwise).input atributes is a vector of ten discrete values
alternate(is there a suitable alternative restaurant nearby?),bar(does the restaurant have a comfortable
bar area?),fri/sat(is it friday or saturday?),hungry(are we currently hungry?),patrons(how many
people are there in the restaurant?(none,some,full)),price(restaurants price range),raining(is it raining
outside?),reservation(did we make reservation?),type(type of restaurant(french,italian,thai,burger))
and WaitEstimate(hosts wait estimate(0-10,10-30,30-60,>60minutes)).these are all input attributes.in
the data set it containes 12 examples based on experiences,only a small fraction of the potential
combinations are represented(total combinations are 9216), only 12 examples provided,leaving 9204
unknown outputs.now the induction challenge is that the task is to infer the missing outputs for the
9204 combinations based on the limited evidence of the 12 examples.each example includes the
values for the 10 attributes and the corresponding output for WillWait.
2
