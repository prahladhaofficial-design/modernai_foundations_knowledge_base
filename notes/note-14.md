# Modernaiintro 14


Recurrent Neural Networks,Unsupervised Learning
and Transfer Learning,Applications
Pappuri Prahladha
1 Recurrent Neural Networks
The Recurrent neural networks features cycles in their computation graph, so that allowing them
to maintain an internal memory that is influenced by past inputs.these are specifically designed for
processing seauential data, with inputs from coming at each time. The markov assumption is that the
hidden state state at any time step encapsulates all relevent information from previous inputs.RNNs
can be unrolled for multiple time steps, transforming them into a feedforward like structure while
sharing weights across time.The gradients can be computated for training although weight sharing
adds complexity to the process and here the model updates its hidden state and produces outputs
using defined functions for input and hidden states.In training a RNN for loss function, typically
utilizes a squared error loss function, summed over all steps and in gradient calculation, there involves
calculating gradients similar to feedforward networks, but with added steps for handling recurrent
connections. Long Short-Term Memory (LSTM) networks are specialized forms of recurrent neural
networks designed to effectively preserve information across many time steps, thereby addressing
the limitations associated with basic RNNs. A key component of LSTMs is the memory cell, which
retains information over time and allows for additive updates rather than the multiplicative updates
typical in standard RNNs.the LSTMs incorporate a mechanism that plays a very important role in
controlling the flow of information. the forget gate determines which information in the memory cell
should be retained or forgotten, while the input gate manages how new information is integrated into
the memory cell.finally, the output gate regulates what information is passed from the memory cell to
the hidden state. Importantly, these gates output values between 0 and 1, enabling a nuanced control
over memory retention.the updated equations for LSTMs specify the operations performed by the
gates and the memory cell updates, so that it facilitates an efficient flow of information throughout the
networka and also LSTMs are effective in various tasks such as speech and handwriting recognition
and are widely used in NLP.
2 Unsupervised Learning and Transfer Learning
The deep learning systems which are based on supervised learning require more amounts of labeled
data, which is more expensive and also time consuming to obtain. as a result, there is significant
interest in alternative solutions, including unsupervised learning, transfer learning, and semisupervised
learning, to reduce dependent on labeled data.
2.1 Unsupervised Learning
The unsupervised learning algorithms have two basic and primary goals: first, to learn new represen-
tations, such as features that facilitate the identification of objects in images, and second, to learn
generative models capable of producing realistic data. these algorithms often learn a joint model
P (x, z), where z represents latent variables that capture underlying content in the data x.one simple
W
generative model is Probabilistic Principal Components Analysis (PPCA), which employs Gaussian
distributions to model data and derive low-dimensional representations.this allows for the generation
of new samples based on learned parameters.another approach is the use of autoencoders, which
consist of an encoder that maps input x to a representation z and a decoder that reconstructs x from z


.these can be either linear or deep networks, with linear autoencoders relating closely to classical PCA.
variational Autoencoders (VAEs) enhance this framework by approximating the posterior distribution
of latent variables and optimizing the evidence lower bound (ELBO) for effective learning. Deep
autoregressive models predict each element of the data vector based on other elements using deep
networks, with applications in time series analysis and speech generation (e.g., waveNet). generative
Adversarial Networks (GANs) comprise a generator that produces data and a discriminator that
classifies it. The training process involves adversarial learning, enabling the generator to produce
increasingly realistic samples. Furthermore, unsupervised translation techniques leverage these
methods to map data x to y without requiring corresponding pairs, often utilizing GANs.
2.2 Transfer Learning and Multitask Learning
In the transfer learning involves using experience from one task to improve learning in another.for
instance, skills acquired in one sport can facilitate learning in related sports.in neural networks, this
typically means copying weights from a pretrained model and adapting them for a new task, which
allows for effective learning even with limited data.practical applications of transfer learning include
leveraging pretrained models such as ResNet for image classification or ROBERTA for natural
language processing tasks.fine-tuning these models involves updating their parameters based on new,
task-specific data.multitask learning expands on this concept by simultaneously training a model on
multiple related tasks, allowing it to learn a common representation that captures shared features
across those tasks.this approach can be particularly beneficial in areas like language processing,
where understanding the interplay between different tasks enhances overall performance.
3 Applications
3.1 Vision
The computer vision has greatly influenced and benefited from deep learning.a great and important
moment was marked by the success of AlexNet in the 2012 ImageNet competition.this competition
involved 1.2 million images across 1,000 categories, evaluated on "top-5" accuracy. AlexNet achieved
a remarkable 15.3% error rate, while competitors exceeded 25%. Its architecture comprised five
convolutional layers, max-pooling layers, and three fully connected layers, utilizing ReLU activa-
tions.since around 2012, advancements have lowered the top-5 error rates to under 2%.CNNs have
found applications in various tasks, including self-driving cars and object recognition.the driving
applications demand real time detection and classification with high accuracy.
3.2 Natural Language Processing
The deep learning has significantly impacted NLP applications, such as machine translation and
speech recognition.key advantages include end-to-end learning, where entire systems are learned as a
single function, automatic generation of internal representations for words, and the interchangeability
of learned encoders and decoders.end-to-end translation has outperformed classical pipeline methods,
reducing errors by around 60%.machine translation is nearing human-level performance for well-
resourced language pairs, and word embeddings allow for effective generalization by capturing
meanings in high-dimensional space.
3.3 Reinforcement Learning
In the field of reinforcement learning we can observe that,agents learn from reward signals to optimize
future rewards. deep learning enhances the representation of complex functions within RL. the field
of deep reinforcement learning emerged from traditional RL methods. a best example is DeepMinds
DQN, which achieved superhuman performance in Atari games. Similarly, ALPHAGO utilized
deep RL to defeat top human players in the game of Go.despite its impressive potential, dRL faces
challenges in achieving consistent performance and adapting to environmental changes. it is rarely
employed in commercial settings, yet remains an active area of research.
2
