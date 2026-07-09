# Project 15


Reinforcement Learning
Pappuri Prahladha
1 Reinforcement Learning and Examples
The facilitation of understanding the RL can be from the events and the following applications. the
master chess player makes informed moves based on a combination of planning anticipating power
replies and intuitive judgments regarding the desirability of specific positions. the adaptive controller,
operating in a petroleum refinery, adjusts parameters in real-time to optimize the trade-off between
yield, cost, and quality based on specified marginal costs rather than sticking strictly to set points. we
can observe in the natural world,a gazelle calf demonstrates rapid learning by standing and running
shortly after birth.similarly, a mobile robot must decide whether to explore a new room for trash
collection or return to its charging station, using its current battery level and past experiences to
inform its decision and again finally, consider Phil preparing his breakfast this seemingly mundane
activity involves a complex web of conditional behaviors and interlocking goals. He navigates
through a series of tasks walking to the cupboard, selecting a cereal box, and obtaining a bowl, spoon,
and milk constantly making rapid judgments based on his needs and the state of his environment.
From all these examples share fundamental characteristics that are easy to overlook. each involves
interaction between an active decision-making agent and its environment, where the agent seeks to
achieve a goal despite uncertainties.the agents actions influence the future state of the environment,
necessitating consideration of indirect and delayed consequences, which may require foresight or
planning. However, the effects of actions remain unpredictable, prompting the agent to monitor its
environment and react appropriately. For instance, phil must keep an eye on the milk he pours to
prevent overflow. adding to that,the goals in each scenario are explicit, allowing agents to assess their
progress based on direct sensory feedback. Importantly, all agents can improve their performance
over time by learning from their experiences.
2 Elements of Reinforcement Learning
In the Reinforcement learning systems we can observe that it consists of four main subelements, a
policy, a reward signal, a value function, and, optionally, a model of the environment.
The policy subelement defines the agents behavior at any given time, mapping perceived states of
the environment to specific actions.it can range from a simple lookup table to a complex function that
involves extensive computation. Policies may also be stochastic, specifying probabilities for each
action.
The reward signal subelement represents the primary goal of the reinforcement learning problem. at
each time step, the environment provides a numerical reward, and the agents objective is to maximize
the total reward over time.this reward can be thought of as analogous to the experiences of pleasure
and pain in biological systems, serving as the basis for modifying the policy when certain actions
yield low rewards.
in contrast, the value function specifies the long-term desirability of states.it indicates the expected
total amount of reward an agent can accumulate in the future from a given state. While rewards
determine immediate desirability, values account for future potential rewards, making them a more
refined judgment. for example, a state might yield a low immediate reward but have a high value if it
frequently leads to states with high rewards. we may observe although rewards are directly given by
the environment, values must be estimated over time from an agents experiences. This distinction


highlights the complexity of decision-making, as actions are chosen based on value judgments aimed
at maximizing long-term rewards.finally, while not always included, a model of the environment
can be useful for predicting future states and rewards based on current actions and circumstances.
Ultimately, the most critical component of many reinforcement learning algorithms is a method for
estimating these values from the agents observations.
3 Limitations and Scope
In Rl we can observe that the concept of "state" is important because as it conveys information
about the environment at a specific time.the formal definition of state is based on the framework
of Markov Decision Processes. here we primarily make the focus on decision making rather than
the representation of states, leaving aside the issues of state construction and learning and also we
can see that most RL methods estimate value functions, this is not strictly necessary for solving
RL problems.evolutionary methods, such as genetic algorithms and simulated annealing, do not
estimate value functions instead, they operate through multiple static policies over time.these methods
can be effective in small policy spaces and when the agent cannot sense the complete state of its
environment.learning approaches leverage detailed behavioral interactions, enhancing the efficiency
of the search for optimal policies. Consequently, evolutionary methods are excluded from the
discussion as they are considered less suited for RL problems.
4 Example: Tic-Tac-Toe game
we know that the Tic-Tac-Toe game is two players taking turns on a 3x3 board to achieve three
evaluation points in a row. the main challenge is constructing a player that can identify imperfections in its
opponents strategy to maximize winning chances.classical techniques like the minimax algorithm
assume specific strategies, making them ineffective against imperfect play.dynamic programming,
while able to compute optimal solutions, requires a complete specification of the opponents strategy,
which is often unavailable.RL offers an alternative approach by allowing the player to learn a model of
the opponents behavior through experience, which can then inform a dynamic programming solution.
Evolutionary methods search the policy space for strategies with high win probabilities, evaluating
multiple policies against the opponent.In addition to that, the value function method involves creating
a table that estimates the winning probabilities for each game state.this approach updates state values
based on game experiences, moving towards accurate probabilities through a temporal difference
learning technique and the key features of reinforcement learning include its focus on learning
through interaction with the environment, which allows for planning and foresight regarding delayed
outcomes, such as setting traps for opponents. This method is applicable to both finite and infinite
state spaces, as demonstrated in games like backgammon. Reinforcement learning also accommodates
prior knowledge, which can enhance learning efficiency. mainly, model free methods do not require
an accurate representation of the environment and instead learn from experience. Furthermore,
reinforcement learning can function at various levels of complexity, enabling it to address a wide
range of problems.atlast as a summray we can observe the following points and things, reinforcement
learning is a computational approach aimed at automating goal directed learning and decision-making
through direct interaction with the environment. Utilizing Markov decision processes, it defines the
relationships between states, actions, and rewards, capturing essential features of artificial intelligence,
such as causality and uncertainty. The use of value functions is crucial for efficient policy search,
distinguishing reinforcement learning from evolutionary methods that search directly in policy space.
2
