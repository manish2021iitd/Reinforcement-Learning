#  About Reinforcement Learning
## 1 The Reinforcement Learning Problem
* Learning from interaction
* Learn by interacting with our environment
* a computational approach to learning from interaction
* how people or animals learn?
* An approach, called reinforcement learning, is much more focused on goal-directed learning from interaction than are other approaches to machine learning.

### 1.1 Reinforcement Learning 
* Reinforcement learning problems involve learning what to do — how to map situations to actions — so as to maximize a numerical reward signal.
* RL Problems are are closed-loop problems because the learning system’s actions influence its later inputs:
* The learner is not told which actions to take, as in many forms of machine learning, but instead must discover which actions yield the most reward by trying them out.
* In RL, actions may affect not only the immediate reward but also the next situation and, through that, all subsequent rewards.
* Three characteristics, not having direct instructions as to what actions to take, and where the consequences of actions,including reward signals, play out over extended time periods—are the three most important distinguishing features of reinforcement learning problems.
* RL problems in terms of optimal control of Markov decision processes 
### 1.2 Examples 
### 1.3 Elements of Reinforcement Learning
* Main elements : Agent and Environment
* Subelements : a policy, a reward signal, a value function, and a model of the environment.
* A **policy** defines the learning agent’s way of behaving at a given time i.e. a policy is a mapping from perceived states of the environment to actions to be taken when in those states. Policy may be a simple function or lookup table, it may involve extensive computation such as a search process. policies may deterministic  or may be stochastic.
* A **reward** signal defines the goal in a reinforcement learning problem. On each time step, the environment sends to the reinforcement learning agent a single number, a reward.
* The agent’s sole objective is to maximize the total reward it receives over the long run. The reward signal thus defines what are the good and bad events for the agent. They are the immediate and defining features of the problem faced by the agent.
* The reward sent to the agent at any time depends on the agent’s current action and the current state of the agent’s environment. The agent cannot alter the
process that does this. The only way the agent can influence the reward signal is through its actions, which can have a direct effect on reward, or an indirect effect through changing the environment’s state.
* In example of Phil eating breakfast, the reinforcement learning agent directing his behavior might receive different reward signals when he eats his breakfast depending on how hungry he is, what mood he is in, and other features of his of his body, which is part of his internal reinforcement learning agent’s environment.
* The reward signal is the primary basis for altering the policy. If an action selected by the policy is followed by low reward, then the policy may be changed to select
some other action in that situation in the future.
* In general, reward signals may be stochastic functions of the state of the environment and the actions taken. Whereas the reward signal indicates what is good in an immediate sense
* A **value function** specifies what is good in the long run. Roughly, the value of a state is the total amount of reward an agent can expect to accumulate over the future, starting from that state. Whereas rewards determine the immediate, intrinsic desirability of environmental states, values indicate the long-term desirability of states after taking into account the states that are likely to follow, and the rewards available in those states.
* For example, a state might always yield a low immediate reward but still have a high value because it is regularly followed by other states that yield high rewards. Or the reverse
could be true.
* To make a human analogy, rewards are somewhat like pleasure (if high) and pain (if low), whereas values correspond to a more refined and farsighted judgment of how pleased or displeased we are that our environment is in a particular state.
* Rewards are in a sense primary, whereas values, as predictions of rewards, are secondary. Without rewards there could be no values, and the only purpose of estimating values is to achieve more reward. Nevertheless, it is values with which we are most concerned when making and evaluating decisions.
* Action choices are made based on value judgments. We seek actions that bring about states of highest value, not highest reward, because these actions obtain the greatest amount of reward for us over the long run.
* In decision-making and planning, the derived quantity called value is the one with which we are most concerned. Unfortunately, it is much harder to determine values than it is to
determine rewards.
* Rewards are basically given directly by the environment, but values must be estimated and re-estimated from the sequences of observations an agent makes over its entire lifetime.
* In fact, the most important component of almost all reinforcement learning algorithms we consider is a method for efficiently estimating values.
* The central role of value estimation is arguably the most important thing in reinforcement learning.
* A **model of the environment** is something that mimics the behavior of the environment, or more generally, that allows inferences to be made about how the environment will behave.
* For example, given a state and action, the model might predict the resultant next state and next reward.
* Models are used for planning, by which we mean any way of deciding on a course of action by considering possible future situations before they are actually experienced.
* Methods for solving reinforcement learning problems that use models and planning are called model-based methods, as opposed to simpler model free methods that are explicitly trial-and-error learners—viewed as almost the opposite of planning.
* In Chapter 9 we explore reinforcement learning systems that simultaneously learn by trial and error, learn a model of the environment, and use the model for planning.
* Modern reinforcement learning spans the spectrum from low-level, trial-and-error learning to high-level, deliberative planning.
  
### 1.4 Limitations and Scope 
* Most of the reinforcement learning methods are structured around estimating value functions, but it is not strictly necessary to do this to solve reinforcement learning problems. 
For example, methods such as genetic algorithms, genetic programming, simulated annealing, and other optimization methods have been used to approach reinforcement learning problems
without ever appealing to value functions. These methods evaluate the “lifetime” behavior of many non-learning agents, each using a different policy for interacting with its environment, and select those that are able to obtain the most reward. We call these evolutionary methods because their operation is analogous to the way biological evolution produces organisms with skilled behavior even when they do not learn during their individual lifetimes. If the
space of policies is sufficiently small, or can be structured so that good policies are common or easy to find—or if a lot of time is available for the search—thencevolutionary methods can be effective. In addition, evolutionary methods have advantages on problems in which the learning agent cannot accurately sense the state of its environment.
* The focus  on reinforcement learning methods is that involve learning while interacting with the environment, which evolutionary methods do not do (unless they evolve learning algorithms, as in some of the approaches that have been studied). It is our belief that methods able to take advantage of the details of individual behavioral interactions can be much more efficient than evolutionary methods in many cases. Evolutionary methods ignore much of the useful structure of the reinforcement learning problem: they do not use
the fact that the policy they are searching for is a function from states to actions; they do not notice which states an individual passes through during its lifetime, or which actions it selects. In some cases this information can be misleading (e.g., when states are misperceived), but more often it should enable more efficient search. Although evolution and learning share many features and naturally work together, we do not consider evolutionary methods
by themselves to be especially well suited to reinforcement learning problems.


* However, we do include some methods that, like evolutionary methods,
do not appeal to value functions. These methods search in spaces of policies
defined by a collection of numerical parameters. They estimate the directions
the parameters should be adjusted in order to most rapidly improve a policy’s
performance. Unlike evolutionary methods, however, they produce these estimates while the agent is interacting with its environment and so can take
advantage of the details of individual behavioral interactions. Methods like
this, called policy gradient methods, have proven useful in many problems, and
some of the simplest reinforcement learning methods fall into this category. In
fact, some of these methods take advantage of value function estimates to improve their gradient estimates. Overall, the distinction between policy gradient
methods and other methods we include as reinforcement learning methods is
not sharply defined.
* Reinforcement learning’s connection to optimization methods deserves some
additional comment because it is a source of a common misunderstanding.
When we say that a reinforcement learning agent’s goal is to maximize a numerical reward signal, we of course are not insisting that the agent has to
actually achieve the goal of maximum reward. Trying to maximize a quantity
does not mean that that quantity is ever maximized. The point is that a reinforcement learning agent is always trying to increase the amount of reward
it receives. Many factors can prevent it from achieving the maximum, even if
one exists. In other words, optimization is not the same a optimality.

### 1.5 An Extended Example: Tic-Tac-Toe 
* To illustrate the general idea of reinforcement learning and contrast it with other approaches, we next consider a single example in more detail.
* Consider the familiar child’s game of tic-tac-toe. Two players take turns playing on a three-by-three(3x3) board. One player plays **X**s and the other **O**s until one player wins by placing three marks in a row, horizontally, vertically, or diagonally, as the X player has in this game:
 
                                                                          X | O | O
                                                                          _________
                                                                          O | X | X
                                                                          _________
                                                                          O | X | O
  
If the board fills up with neither player getting three in a row, the game is a draw. Because a skilled player can play so as never to lose, let us assume that we are playing against an imperfect player, one whose play is sometimes incorrect and allows us to win. For the moment, in fact, let us consider draws and losses to be equally bad for us. 
* How might we construct a player that will find the imperfections in its opponent’s play and learn to maximize its chances of winning?
* Although this is a simple problem, it cannot readily be solved in a satisfactory way through classical techniques. For example, the classical “minimax”
solution from game theory is not correct here because it assumes a particular
way of playing by the opponent. For example, a minimax player would never
reach a game state from which it could lose, even if in fact it always won from
that state because of incorrect play by the opponent. Classical optimization
methods for sequential decision problems, such as dynamic programming, can
compute an optimal solution for any opponent, but require as input a complete specification of that opponent, including the probabilities with which
the opponent makes each move in each board state. Let us assume that this
information is not available a priori for this problem, as it is not for the vast
majority of problems of practical interest. On the other hand, such information can be estimated from experience, in this case by playing many games
against the opponent. About the best one can do on this problem is first to
learn a model of the opponent’s behavior, up to some level of confidence, and
then apply dynamic programming to compute an optimal solution given the
approximate opponent model. In the end, this is not that different from some
of the reinforcement learning methods we examine later in this book.
* An evolutionary method applied to this problem would directly search the
space of possible policies for one with a high probability of winning against
the opponent. Here, a policy is a rule that tells the player what move to make
for every state of the game—every possible configuration of Xs and Os on the
three-by-three board. For each policy considered, an estimate of its winning
probability would be obtained by playing some number of games against the
opponent. This evaluation would then direct which policy or policies were
considered next. A typical evolutionary method would hill-climb in policy
space, successively generating and evaluating policies in an attempt to obtain
incremental improvements. Or, perhaps, a genetic-style algorithm could be
used that would maintain and evaluate a population of policies. Literally
hundreds of different optimization methods could be applied.
* Here is how the tic-tac-toe problem would be approached with a method
making use of a value function. First we set up a table of numbers, one for
each possible state of the game. Each number will be the latest estimate of
the probability of our winning from that state. We treat this estimate as the
state’s value, and the whole table is the learned value function. State A has
higher value than state B, or is considered “better” than state B, if the current
estimate of the probability of our winning from A is higher than it is from B.
* Assuming we always play Xs, then for all states with three Xs in a row the
probability of winning is 1, because we have already won. Similarly, for all
states with three Os in a row, or that are “filled up,” the correct probability
is 0, as we cannot win from them. We set the initial values of all the other
states to 0.5, representing a guess that we have a 50% chance of winning.
We play many games against the opponent. To select our moves we examine
the states that would result from each of our possible moves (one for each blank
space on the board) and look up their current values in the table. Most of the
time we move greedily, selecting the move that leads to the state with greatest
value, that is, with the highest estimated probability of winning. Occasionally,
however, we select randomly from among the other moves instead. These are
called exploratory moves because they cause us to experience states that we
might otherwise never see. A sequence of moves made and considered during
a game can be diagrammed as in Figure 1.1.
* While we are playing, we change the values of the states in which we find
ourselves during the game. We attempt to make them more accurate estimates
of the probabilities of winning. To do this, we “back up” the value of the state
after each greedy move to the state before the move, as suggested by the arrows
in Figure 1.1. More precisely, the current value of the earlier state is adjusted
to be closer to the value of the later state. This can be done by moving the
earlier state’s value a fraction of the way toward the value of the later state.
If we let s denote the state before the greedy move, and s
0
the state after
the move, then the update to the estimated value of s, denoted V (s), can be
written as
V (s) ← V (s) + α
h
V (s
0
) − V (s)
i
,
where α is a small positive fraction called the step-size parameter, which influences the rate of learning. This update rule is an example of a temporaldifference learning method, so called because its changes are based on a difference, V (s
0
) − V (s), between estimates at two different times.
* The method described above performs quite well on this task. For example,
if the step-size parameter is reduced properly over time, this method converges,
for any fixed opponent, to the true probabilities of winning from each state
given optimal play by our player. Furthermore, the moves then taken (except
on exploratory moves) are in fact the optimal moves against the opponent. In
other words, the method converges to an optimal policy for playing the game.
If the step-size parameter is not reduced all the way to zero over time, then
this player also plays well against opponents that slowly change their way of
playing.

* This example illustrates the differences between evolutionary methods and
the methods that learn value functions. To evaluate a policy an evolutionary
method holds the policy fixed and plays many games against the opponent, or
simulate many games using a model of the opponent. The frequency of wins
gives an unbiased estimate of the probability of winning with that policy, and
can be used to direct the next policy selection. But each policy change is made
only after many games, and only the final outcome of each game is used: what
happens during the games is ignored. For example, if the player wins, then
all of its behavior in the game is given credit, independently of how specific
moves might have been critical to the win. Credit is even given to moves that
never occurred! Value function methods, in contrast, allow individual states
to be evaluated. In the end, evolutionary and value function methods both
search the space of policies, but learning a value function takes advantage of
information available during the course of play.
* This simple example illustrates some of the key features of reinforcement
learning methods. First, there is the emphasis on learning while interacting with an environment, in this case with an opponent player. Second, there is a
clear goal, and correct behavior requires planning or foresight that takes into
account delayed effects of one’s choices. For example, the simple reinforcement learning player would learn to set up multi-move traps for a shortsighted
opponent. It is a striking feature of the reinforcement learning solution that it
can achieve the effects of planning and lookahead without using a model of the
opponent and without conducting an explicit search over possible sequences
of future states and actions.
* While this example illustrates some of the key features of reinforcement
learning, it is so simple that it might give the impression that reinforcement
learning is more limited than it really is. Although tic-tac-toe is a two-person
game, reinforcement learning also applies in the case in which there is no external adversary, that is, in the case of a “game against nature.” Reinforcement
learning also is not restricted to problems in which behavior breaks down into
separate episodes, like the separate games of tic-tac-toe, with reward only at
the end of each episode. It is just as applicable when behavior continues indefinitely and when rewards of various magnitudes can be received at any time.
Reinforcement learning is also applicable to problems that do not even break
down into discrete time steps, like the plays of tic-tac-toe. The general principles apply to continuous-time problems as well, although the theory gets more
complicated and we omit it from this introductory treatment.
* Tic-tac-toe has a relatively small, finite state set, whereas reinforcement
learning can be used when the state set is very large, or even infinite. For
example, Gerry Tesauro (1992, 1995) combined the algorithm described above
with an artificial neural network to learn to play backgammon, which has
approximately 1020 states. With this many states it is impossible ever to
experience more than a small fraction of them. Tesauro’s program learned to
play far better than any previous program, and now plays at the level of the
world’s best human players (see Chapter 15). The neural network provides
the program with the ability to generalize from its experience, so that in new
states it selects moves based on information saved from similar states faced
in the past, as determined by its network. How well a reinforcement learning
system can work in problems with such large state sets is intimately tied to
how appropriately it can generalize from past experience. It is in this role that
we have the greatest need for supervised learning methods with reinforcement
learning. Neural networks are not the only, or necessarily the best, way to do
this.
* In this tic-tac-toe example, learning started with no prior knowledge beyond the rules of the game, but reinforcement learning by no means entails a
tabula rasa view of learning and intelligence. On the contrary, prior information can be incorporated into reinforcement learning in a variety of ways that can be critical for efficient learning. We also had access to the true state in the
tic-tac-toe example, whereas reinforcement learning can also be applied when
part of the state is hidden, or when different states appear to the learner to be
the same. That case, however, is substantially more difficult, and we do not
cover it significantly in this book.
* Finally, the tic-tac-toe player was able to look ahead and know the states
that would result from each of its possible moves. To do this, it had to have
a model of the game that allowed it to “think about” how its environment
would change in response to moves that it might never make. Many problems
are like this, but in others even a short-term model of the effects of actions
is lacking. Reinforcement learning can be applied in either case. No model is
required, but models can easily be used if they are available or can be learned.
* On the other hand, there are reinforcement learning methods that do not
need any kind of environment model at all. Model-free systems cannot even
think about how their environments will change in response to a single action.
The tic-tac-toe player is model-free in this sense with respect to its opponent:
it has no model of its opponent of any kind. Because models have to be
reasonably accurate to be useful, model-free methods can have advantages over
more complex methods when the real bottleneck in solving a problem is the
difficulty of constructing a sufficiently accurate environment model. Modelfree methods are also important building blocks for model-based methods. In
this book we devote several chapters to model-free methods before we discuss
how they can be used as components of more complex model-based methods.
* But reinforcement learning can be used at both high and low levels in a system. Although the tic-tac-toe player learned only about the basic moves of the game, nothing prevents reinforcement learning from working at higher levels where each of the “actions” may itself be the application of a possibly elaborate problem-solving method. In hierarchical learning systems, reinforcement learning can work simultaneously on several levels.

### 1.6 Summary   
* Reinforcement learning is a computational approach to understanding and automating goal-directed learning and decision-making.
* It is distinguished from other computational approaches by its emphasis on learning by an agent from direct interaction with its environment, without relying on exemplary supervision or complete models of the environment.
* Reinforcement learning is the first field to seriously address the computational issues that arise when learning from interaction with an environment in order to achieve long-term goals.
* Reinforcement learning uses a formal framework defining the interaction between a learning agent and its environment in terms of states, actions, and rewards. This framework is intended to be a simple way of representing essential features of the artificial intelligence problem. These features include a sense of cause and effect, a sense of uncertainty and nondeterminism, and the existence of explicit goals.
* The concepts of value and value functions are the key features of most of the reinforcement learning methods. The value functions are important for efficient search in the space
of policies. Their use of value functions distinguishes reinforcement learning methods from evolutionary methods that search directly in policy space guidedby scalar evaluations of entire policies.


# I Tabular Solution Methods 
* The core ideas of reinforcement learning algorithms in their simplest forms, that in which the **state and action spaces are small enough** for the approximate action-value function to be represented as **an array, or table**.
* These methods can often find **exact solutions**, that is, they can often find exactly the optimal value function and the optimal policy.
* 
## 2 Multi-arm Bandits 
*  Solution methods for the special of the reinforcement learning problem in which there is only a single state, called bandit problems
*  Reinforcement learning is different from other types of learning because it uses training information that evaluates the actions taken rather than instructs by giving correct actions. That's why we need for active exploration, for an explicit trial-and-error search for good behavior.
*  Purely **evaluative feedback** indicates how good the action taken is, but not whether it is the best or the worst action possible. Evaluative feedback is the basis of methods for function optimization, including evolutionary methods.
*  Purely **instructive feedback**, on the other hand, indicates the correct action to take, independently of the action actually taken. This kind of feedback is the basis of supervised learning, which includes large parts of pattern classification, artificial neural networks, and system identification.
*  In their pure forms, these two kinds of feedback are quite distinct: evaluative feedback depends entirely on the action taken, whereas instructive feedback is
independent of the action taken.
* There are also interesting intermediate cases in which evaluation and instruction blend together.
* We will learn evaluative aspect of reinforcement learning in a simplified setting, one that does not involve learning to act in more than one situation. This **nonassociative** setting is the one in which most prior work involving evaluative feedback has been done, and it avoids much of the complexity of the full reinforcement learning problem. This case will
enable us to see most clearly how evaluative feedback differs from, and yet can be combined with, instructive feedback.
* The particular **nonassociative, evaluative feedback problem** that we explore is a **simple version of the n-armed bandit problem**. We use this problem to introduce a number of basic learning methods which we extend to the **full reinforcement learning problem**.
* What happens when the bandit problem becomes associative, that is, when actions are taken in more than one situation?

### 2.1 An n-Armed Bandit Problem 
*  **Learning problem:** Suppose we are faced repeatedly with a choice among n different options, or actions. After each choice we receive a numerical reward chosen from a stationary probability distribution that depends on the action we selected. Our objective is to maximize the expected total reward over some time period, for example, over 1000 action selections, or time steps.
*  This is the original form of the **n-armed bandit problem**, so named by analogy to a **slot machine**, or **ne-armed bandit,** except that it has n levers instead of one. Each action selection is like a play of one of the slot machine’s levers, and the rewards are the payoffs for hitting the jackpot. Through repeated action selections we are to maximize our winnings by concentrating our actions on the best levers.
*  Another analogy is that of a doctor choosing between experimental treatments for a series of seriously ill patients. Each action selection is a treatment selection, and each reward is the survival or well-being of the patient.
*  Today the term “n-armed bandit problem” is sometimes used for a generalization of the problem described above, but we use it to refer just to this simple case.
*  In our n-armed bandit problem, **each action has an expected or mean reward given that that action is selected**; let us call this the **value of that action**.
*  If we knew the value of each action, then it would be trivial to solve the n-armed bandit problem: we would always select the action with highest value. We assume that we do not know the action values with certainty, although we may have estimates.
*  If we maintain estimates of the action values, then at any time step there is at least one action whose estimated value is greatest. We call this a **greedy action**.
*  If we **select a greedy action**, then we are **exploiting our current knowledge of the values of the actions**.
*  If we **select one of the nongreedy actions**, then we are **exploring**, because this enables us to improve our estimate of the nongreedy action’s value.
*  Exploitation is the right thing to do to maximize the expected reward on the one step, but exploration may produce the greater total reward in the long run.
*  For example, suppose the greedy action’s value is known with certainty, while several other actions are estimated to be nearly as good but with substantial uncertainty. The uncertainty is such that at least one of these other actions probably is actually better than the greedy action, but you don’t know which one. If we have many time steps ahead on which to make action selections, then it may be better to explore the nongreedy actions and discover which of them are better than the greedy action.
*  Reward is lower in the short run, during exploration, but higher in the long run because after we have discovered the better actions, we can exploit them many times. Because it is not possible both to explore and to exploit with any single action selection, one often refers to the “conflict” between exploration and exploitation.
*  In any specific case, whether it is better to explore or exploit depends in a complex way on the precise values of the estimates, uncertainties, and the number of remaining steps.
*  There are many sophisticated methods for balancing exploration and exploitation for particular mathematical formulations of the n-armed bandit and related problems. However, most of these methods make strong assumptions about stationarity and prior knowledge that are either violated or impossible to verify in applications and in the full reinforcement learning problem that we consider in subsequent chapters. The guarantees of optimality or bounded loss for these methods are of little comfort when the assumptions of their theory do not apply.
  
### 2.2 Action-Value Methods 
#### Methods for estimating the values of actions and for using the estimates to make action selection decisions.
* Let true (actual) value of action a = **q(a)**,
  
   and the estimated value on the t-th time step = **Q<sub>t</sub>(a)**
  
   As the true value of an action is the **mean reward received when that action is selected**. One natural way to estimate this is by **averaging the rewards actually received when the action was selected**.
  
   In other words, if by the t-th time step action a has been chosen **N<sub>t</sub>(a)** times prior to **t**, yielding rewards **R1, R2, . . . , R<sub>N <sub>t</sub> (a)</sub>**, then its value is estimated to be **Q<sub>t</sub>(a) = R1 + R2 + · · · +  R<sub>N <sub>t</sub> (a)</sub> /N<sub>t</sub>(a)**.
* If **N<sub>t</sub>(a) = 0**, then we define Q<sub>t</sub>(a) instead as some default value, such as **Q<sub>1</sub>(a) = 0**. As **N<sub>t</sub>(a) → ∞**, by the law of large numbers, Q<sub>t</sub>(a) converges to q(a).
* We call this the **sample-average method** for estimating action values because each estimate is a **simple average** of the sample of relevant rewards.**(not necessarily the best method)**.
* Nevertheless, for now let us stay with this simple estimation method and turn to the question of **how the estimates might be used to select actions?**.
* The simplest **action selection rule** is to select the action (or one of the actions) with **highest estimated action value**, that is, to select at step t one of the greedy actions, **A<sup>*</sup><sub>t</sub>**, for which
  
  <div align="center"> 
    Q<sub>t</sub>(A<sup>∗</sup><sub>t</sub>) = max<sub>a</sub> Q<sub>t</sub>(a).
  </div>

  This **greedy action selection method** can be written as
  <div align="center"> 
    A<sub>t</sub> = argmax<sub>a</sub> Q<sub>t</sub>(a)
  </div>

* **Greedy action selection** always exploits current knowledge to maximize immediate reward; it spends no time at all sampling apparently inferior actions to see if they might really be better.
* A simple alternative is to behave greedily most of the time, but every once in a while, say with small probability **ε**, instead to select randomly from amongst all the actions with equal probability independently of the action value estimates. We call methods using this near-greedy action selection rule **ε-greedy methods**. An advantage of these methods is that, in the limit as the number of plays increases, every action will be sampled an infinite number of times, guaranteeing that N<sub>t</sub>(a) → ∞ for all a, and thus ensuring that all the Q<sub>t</sub>(a) converge to q(a). This of course implies that the probability of selecting the optimal action converges to greater than **1 − ε** , that is, to near certainty. (These are just asymptotic guarantees),
#### **The practical effectiveness of these methods**:
* To roughly assess the relative effectiveness of the **greedy and ε-greedy methods**, we compared them numerically on a suite of test problems.
* This was a set of **2000 randomly generated n-armed bandit tasks** with **n = 10**.
* For each bandit, the action values, **q(a), a = 1, . . . , 10**, were selected according to a **normal (Gaussian) distribution with mean 0 and variance 1**.
* On t-th time step with a given bandit, the actual reward **R<sub>t</sub>** was the **q(A<sub>t</sub>)** for the bandit **(where A<sub>t</sub> was the action selected)** plus a **normally distributed** noise term that was **mean 0** and **variance 1**.
* Averaging over bandits, we can plot the performance and behavior of various methods as they improve with experience over 1000 steps, as in Figure. We call this suite of test tasks the **10-armed testbed**.

<img width="1034" alt="Image" src="https://github.com/user-attachments/assets/15f07ebe-5261-4a2c-8286-cd2e7ee8ff3b" />

<img width="1034" alt="Image" src="https://github.com/user-attachments/assets/f83def72-b4ca-4f3d-ba7b-65880ab841af" />


* figure: Average performance of ε-greedy action-value methods on the 10-armed testbed. These data are averages over 2000 tasks. All methods used sample averages as their action-value estimates. The detailed structure at the beginning of these curves depends on how actions are selected when multiple actions have the same maximal action value. Here such ties were
broken randomly. An alternative that has a similar effect is to add a verysmall amount of randomness to each of the initial action values, so that ties effectively never happen.



* This figure **compares a greedy method with two ε-greedy methods (ε = 0.01 and ε = 0.1)**, as described above, on the 10-armed testbed.
* Both methods formed their action-value estimates using the sample-average technique.
* The **upper graph shows the increase in expected reward with experience**.
* The **greedy method improved slightly faster** than the other methods **at the very beginning**, but then **leveled off at a lower level**. It achieved **a reward per step of only 
  about 1**, compared with the **best possible of about 1.55** on this testbed.
* The **greedy method performs significantly worse in the long run** because it often gets stuck performing suboptimal actions.
* The **lower graph shows that the greedy method found the optimal action in only approximately one-third of the tasks**. In the other two-thirds, its initial samples of the optimal action were disappointing, and it never returned to it.
* The **ε-greedy methods eventually perform better** because they **continue to explore**, and to improve their chances of recognizing the optimal action.
* The ε = 0.1 method explores more, and usually finds the optimal action earlier, but never selects it more than 91% of the time.
* The ε = 0.01 method improves more slowly, but eventually performs better than the ε = 0.1 method on both performance measures.
*   It is also possible to reduce ε over time to try to get the best of both high and low values.
* The advantage of ε-greedy over greedy methods depends on the task.
* For example, suppose the **reward variance** had been **larger**, say **10** instead of 1. With noisier rewards it takes **more exploration** to find the optimal action, and ε-greedy 
  methods should fare even better relative to the greedy method.
* On the other hand, if the **reward variances were zero**, then the greedy method would know the true value of each action after trying it once. In this case the greedy method might 
  actually perform best because it would soon find the optimal action and then never explore.
* But even in the deterministic case, there is a large advantage to exploring if we weaken some of the other assumptions.
* For example, suppose the bandit task were nonstationary, that is, that the true values of the actions changed over time. In this case exploration is needed even in the deterministic case to make sure one of the nongreedy actions has not changed to become better than the greedy one. As we will see in the next few chapters, **effective nonstationarity is the case most commonly encountered in reinforcement learning**. Even if the underlying task is stationary and deterministic, the learner faces a set of banditlike decision tasks each of which changes over time due to the learning process itself. Reinforcement learning requires a balance between exploration and exploitation.
  
### 2.3 Incremental Implementation
* As all estimate action values are sample averages of observed rewards. 
* The obvious implementation is to maintain  for each action a, a record of all the rewards that have followed the selection of that action.
*  Then, when the estimate of the value of action a is needed at time t, it can be computed according to (2.1), which we repeat here:

$$
Q_t(a)=\frac{R_1+R_2+\cdots+R_{N_t(a)}}{N_t(a)}
$$

   where  $R_1, \ldots, R_{N_t(a)}$ are all the rewards received following all selections of action $a$ prior to play $t$. 
* A problem with this straightforward implementation is that its memory and computational requirements grow over time without bound. That is, each additional reward following a selection of action $a$ requires more memory to store it and results in more computation being required to determine $Q_t(a)$.
* As you might suspect, this is not really necessary. It is easy to devise incremental update formulas for computing averages with small, constant computation required to process each new reward. For some action, let $Q_k$ denote the estimate for its $k$ th reward, that is, the average of its first $k-1$ rewards.
* Given this average and a $k$ th reward for the action, $R_k$, then the average of all $k$ rewards can be computed by

$$
\begin{aligned}
Q_{k+1} & =\frac{1}{k} \sum_{i=1}^k R_i \\
& =\frac{1}{k}\left(R_k+\sum_{i=1}^{k-1} R_i\right) \\
& =\frac{1}{k}\left(R_k+(k-1) Q_k+Q_k-Q_k\right) \\
& =\frac{1}{k}\left(R_k+k Q_k-Q_k\right) \\
& =Q_k+\frac{1}{k}\left[R_k-Q_k\right],
\end{aligned}
$$

which holds even for k = 1, obtaining Q2 = R1 for arbitrary Q1. This implementation requires memory only for Q_{k} and k, and only the small computation  for each new reward.
This update rule is of a form that occurs frequently throughout this study. The general form is

$$
\text { NewEstimate } \leftarrow \text { OldEstimate }+ \text { StepSize }[\text { Target }- \text { OldEstimate }] .
$$


* The expression **[Target - OldEstimate]** is an **error** in the estimate. It is reduced by taking a step toward the "Target." The target is presumed to indicate a desirable direction in which to move, though it may be noisy.
* In the case above, for example, the target is the kth reward. Note that the step-size parameter (StepSize) used in the incremental method described above changes from time step to time step. In processing the kth reward for action a, that method uses a step-size parameter of 1/k.
* In this book we denote the step-size parameter by the symbol α or, more generally, by αt(a). We sometimes use the informal shorthand α =1/k to refer to this case, leaving the dependence of k on the action implicit
### 2.4 Tracking a Nonstationary Problem
* The averaging methods discussed so far are appropriate in a stationary environment, but not if the bandit is changing over time.
* As noted earlier, we often encounter reinforcement learning problems that are effectively nonstationary. In such cases it makes sense to weight recent rewards more heavily than long-past ones. One of the most popular ways of doing this is to use a constant step-size parameter.
* For example, the incremental update rule for updating an average Qk of the k − 1 past rewards is modified to be

$$
Q_{k+1}=Q_k+\alpha\left[R_k-Q_k\right]
$$

  where the step-size parameter $\alpha \in(0,1]^1$ is constant. This results in $Q_{k+1}$ being a weighted average of past rewards and the initial estimate $Q_1$ :

$$
\begin{aligned}
Q_{k+1}= & Q_k+\alpha\left[R_k-Q_k\right] \\
= & \alpha R_k+(1-\alpha) Q_k \\
= & \alpha R_k+(1-\alpha)\left[\alpha R_{k-1}+(1-\alpha) Q_{k-1}\right] \\
= & \alpha R_k+(1-\alpha) \alpha R_{k-1}+(1-\alpha)^2 Q_{k-1} \\
= & \alpha R_k+(1-\alpha) \alpha R_{k-1}+(1-\alpha)^2 \alpha R_{k-2}+ \\
& \cdots+(1-\alpha)^{k-1} \alpha R_1+(1-\alpha)^k Q_1 \\
& =(1-\alpha)^k Q_1+\sum_{i=1}^k \alpha(1-\alpha)^{k-i} R_i .
\end{aligned}
$$

* We call this a weighted average because the sum of the weights is $(1-\alpha)^k+$ $\sum_{i=1}^k \alpha(1-\alpha)^{k-i}=1$, as you can check yourself. Note that the weight, $\alpha(1-$ $\alpha)^{k-i}$, given to the reward $R_i$ depends on how many rewards ago, $k-i$, it was observed. The quantity 1 − α is less than 1, and thus the weight given to Ri
decreases as the number of intervening rewards increases. In fact, the weight decays exponentially according to the exponent on 1 − α. (If 1 − α = 0, then all the weight goes on the very last reward, $R_{k}$, because of the convention that $0^{0} = 1$.) Accordingly, this is sometimes called an exponential, recency-weighted average.
* Sometimes it is convenient to vary the step-size parameter from step to step. Let αk(a) denote the step-size parameter used to process the reward received after the kth selection of action a. As we have noted, the choice αk(a) = 1/k results in the sample-average method, which is guaranteed to converge to the true action values by the law of large numbers. But of course convergence is not guaranteed for all choices of the sequence {αk(a)}. A wellknown result in stochastic approximation theory gives us the conditions required to assure convergence with probability 1:

$$
\sum_{k=1}^{\infty} \alpha_k(a)=\infty \quad \text { and } \quad \sum_{k=1}^{\infty} \alpha_k^2(a)<\infty
$$

The first condition is required to guarantee that the steps are large enough to eventually overcome any initial conditions or random fluctuations. The second condition guarantees that eventually the steps become small enough to assure convergence.

* Note that both convergence conditions are met for the sample-average case, $αk(a) = 1/k$ , but not for the case of constant step-size parameter, $α({k}(a) = α$.
* In the latter case, the second condition is not met, indicating that the estimates never completely converge but continue to vary in response to the most recently received rewards. As we mentioned above, this is actually desirable in a nonstationary environment, and problems that are effectively nonstationary are the norm in reinforcement learning. In addition, sequences of step-size parameters that meet the conditions (2.7) often converge very slowly or need considerable tuning in order to obtain a satisfactory convergence rate. Although sequences of step-size parameters that meet these convergence conditions are often used in theoretical work, they are seldom used in applications and empirical research.
### 2.5 Optimistic Initial Values 
* All the methods we have discussed so far are dependent to some extent on the initial action-value estimates, Q1(a). In the language of statistics, these methods are biased by their initial estimates. For the sample-average methods,
  
<img width="794" alt="Image" src="https://github.com/user-attachments/assets/dbe747aa-95a0-4113-b591-b27804f0d728" />
* Figure : The effect of optimistic initial action-value estimates on the 10- armed testbed. Both methods used a constant step-size parameter, α = 0.1.
* the bias disappears once all actions have been selected at least once, but for
methods with constant α, the bias is permanent, though decreasing over time
as given by (2.6). In practice, this kind of bias is usually not a problem, and
can sometimes be very helpful. The downside is that the initial estimates
become, in effect, a set of parameters that must be picked by the user, if only
to set them all to zero. The upside is that they provide an easy way to supply
some prior knowledge about what level of rewards can be expected.
Initial action values can also be used as a simple way of encouraging exploration. Suppose that instead of setting the initial action values to zero, as
we did in the 10-armed testbed, we set them all to +5. Recall that the q(a)
in this problem are selected from a normal distribution with mean 0 and variance 1. An initial estimate of +5 is thus wildly optimistic. But this optimism
encourages action-value methods to explore. Whichever actions are initially
selected, the reward is less than the starting estimates; the learner switches
to other actions, being “disappointed” with the rewards it is receiving. The
result is that all actions are tried several times before the value estimates converge. The system does a fair amount of exploration even if greedy actions are
selected all the time.
Figure 2.2 shows the performance on the 10-armed bandit testbed of a
greedy method using Q1(a) = +5, for all a. For comparison, also shown is an
ε-greedy method with Q1(a) = 0. Initially, the optimistic method performs
worse because it explores more, but eventually it performs better because its
exploration decreases with time. We call this technique for encouraging exploration optimistic initial values. We regard it as a simple trick that can be
quite effective on stationary problems, but it is far from being a generally useful approach to encouraging exploration. For example, it is not well suited to
nonstationary problems because its drive for exploration is inherently temporary. If the task changes, creating a renewed need for exploration, this method
cannot help. Indeed, any method that focuses on the initial state in any special
way is unlikely to help with the general nonstationary case. The beginning
of time occurs only once, and thus we should not focus on it too much. This
criticism applies as well to the sample-average methods, which also treat the
beginning of time as a special event, averaging all subsequent rewards with
equal weights. Nevertheless, all of these methods are very simple, and one of
them or some simple combination of them is often adequate in practice. In the
rest of this book we make frequent use of several of these simple exploration
techniques.


### 2.6 Upper-Confidence-Bound Action Selection
* Exploration is needed because the estimates of the action values are uncertain.
  * Uncertainty in Action Value Estimates:
  * Initially, the agent has no knowledge of the environment and therefore has uncertain estimates of the action values.
  * This uncertainty arises from two main sources:
    * Limited data: The agent has only observed a limited number of state-action transitions and their corresponding rewards. As a result, its estimates of the action values are based on a small sample of data and are therefore uncertain.
    * Stochasticity of the environment: The environment may be inherently stochastic, meaning that the same action in the same state can lead to different outcomes. This stochasticity introduces further uncertainty into the action value estimates.
    
* The greedy actions are those that look best at present, but some of the other actions may actually be better. ε-greedy action selection forces the non-greedy actions to be tried, but indiscriminately, with no preference for those that are nearly greedy or particularly uncertain. It would be better to select among the non-greedy actions according to their potential for actually being optimal, taking into account both how close their estimates are to being maximal and the uncertainties in those estimates. One effective way of doing this is to select actions as

<div align="center">
A<sub>t</sub> = argmax<sub>a</sub>(Q(a) + c * sqrt(ln(t) / N(a)))
</div>
  
  * where c > 0 controls the degree of exploration. 
  * If Nt(a) = 0, then a is considered to be a maximizing action.
    
* The **idea of this upper confidence bound (UCB) action selection** is that **the square-root term is a measure of the uncertainty or variance in the estimate of a’s value**.
  * The quantity being max’ed over is thus a sort of **upper bound on the possible true value of action a**, with the **c parameter determining the confidence level**.
  * Each time a is selected the uncertainty is presumably reduced; Nt(a) is incremented and, as it appears in the denominator of the uncertainty term, the term is decreased.
  * On the other hand, each time an action other a is selected t is increased; as it appears in the numerator the uncertainty estimate is increased.
  * The use of the natural logarithm means that the increase gets smaller over time, but is unbounded; all actions will eventually be selected, but as time goes by it will be a longer 
    wait, and thus a lower selection frequency, for actions with a lower value estimate or that have already been selected more times.

<img width="977" alt="Image" src="https://github.com/user-attachments/assets/27bdc6a9-6129-4f0d-9e41-76d2cd1b2e85" />

Figure 2.3: Average performance of UCB action selection on the 10-armed testbed. As shown, UCB generally performs better that ε-greedy action selection, except in the first n plays, when it selects randomly among the as-yet unplayed actions. UCB with c = 1 would perform even better but would not show the prominent spike in performance on the 11th play. Can you think of an explanation of this spike?

* Results with UCB on the 10-armed testbed are shown in Figure 2.3. UCB will often perform well, as shown here, but is more difficult than ε-greedy to extend beyond bandits to the more general reinforcement learning settings considered in the rest of this book.
* One difficulty is in dealing with nonstationary problems; something more complex than the methods presented in Section 2.4 would be needed. Another difficulty is dealing with large state spaces, particularly function approximation as developed in Part III of this book. In these more advanced settings there is currently no known practical way of utilizing the idea of UCB action selection.
  
### 2.7 Gradient Bandits
* We have seen methods that estimate action values and use those estimates to select actions.(a good approach, but it is not the only one possible.)
* Now, we consider learning a numerical preference **H<sub>t</sub>(a)** for each action a.

  The larger the preference, the more often that action is taken, but the preference has no interpretation in terms of reward.

  Only the relative preference of one action over another is important; if we add 1000 to all the preferences there is no affect on the action probabilities, which are determined 
  according to a soft-max distribution (i.e., Gibbs or Boltzmann distribution) as follows:

<img width="913" alt="Image" src="https://github.com/user-attachments/assets/e55204d5-a299-4601-a4a0-5bd98f2b0636" />

### 2.8 Associative Search (Contextual Bandits)
* Nonassociative tasks, in which there is no need to associate different actions with different situations. In these tasks the learner either tries to find a single best action when the task is stationary, or tries to track the best action as it changes over time when the task is nonstationary.
* In a general reinforcement learning task there is more than one situation, and the goal is to learn a policy: a mapping from situations to the actions that are best in those situations.
* To extend nonassociative tasks into the associative setting:
  
  Example:

  Suppose there are several different n-armed bandit tasks, and that on each play you confront one of these chosen at random. Thus, the bandit task changes randomly from play 
  to play. This would appear to us as a single, nonstationary n-armed bandit task whose true action values change randomly from play to play. We could try using one of the methods 
  that can handle nonstationarity, but unless the true action values change slowly, these methods will not work very well.

  Now suppose, however, that when a bandit task is selected for us, we are given some distinctive clue about its identity (but not its action values). Maybe we are facing an actual 
  slot machine that changes the color of its display as it changes its action values. Now you can learn a policy associating each task, signaled by the color you see, with the best 
  action to take when facing that task—for instance, if red, play arm 1; if green, play arm 2. With the right policy we can usually do much better than we could in the absence of any 
  information distinguishing one bandit task from another.

* This is **an example of an associative search task**, so called because **it involves both trial-and-error learning in the form of search for the best actions and association of these actions with the situations in which they are best**(Associative search tasks are often now termed contextual bandits in the literature).
* Associative search tasks are intermediate between the n-armed bandit problem and the full reinforcement learning problem. They are like the full reinforcement learning problem in that they involve learning a policy, but like our version of the n-armed bandit problem in that each action affects only the immediate reward. If actions are allowed to affect the next situation as well as the reward, then we have the full reinforcement learning problem.
* 
  
### 2.9 Summary
* several simple ways of balancing exploration and exploitation.
* The ε-greedy methods choose randomly a small fraction of the time, whereas UCB methods choose deterministically but achieve exploration by subtly favoring at each step the actions that have so far received fewer samples.
* Gradient-bandit algorithms estimate not action values, but action preferences, and favor the more preferred actions in a graded, probabalistic manner using a soft-max distribution.
* The simple expedient of initializing  estimates optimistically causes even greedy methods to explore significantly
  
This idea is called **optimistic initial values**, a simple yet effective technique in reinforcement learning (RL) and multi-armed bandit problems. By initializing action-value estimates Q(a) with high values, the agent is encouraged to explore more in the early stages.

<img width="944" alt="Image" src="https://github.com/user-attachments/assets/f8bb203a-29b7-4dc1-a968-fc549a0a7a15" />

Why Does This Work?

If an agent starts with a high estimate for all actions, it will initially pick actions greedily.
Since these values are overly optimistic, the agent will observe lower rewards than expected, causing the estimated value to decrease.
As it updates its estimates, it will naturally explore other actions to find better ones.

Example: k-Armed Bandit
Consider a 10-armed bandit problem where the true action values are normally distributed with mean 0. If we: Initialize 
Q(a)=5 for all actions (optimistic), Use a greedy action selection strategy, The agent will try different actions because the initially chosen action will have its estimate lowered after a few trials, making other actions more appealing.
* Gradient Bandit vs Epsilon Greddy vs UCB, which methods is best?
*  A complication is that they all have a parameter ⍺/c/Q ; to get a meaningful comparison we will have to consider their performance as a function of their parameter.
*  Graphs for each algorithm are too visually confusing to show such a learning curve for each algorithm and parameter value. Instead we summarize **a complete learning curve by its
average value over the 1000 steps**; this value is **proportional to the area under the learning curves**.( all the algorithms perform best at an intermediate value of their parameter, neither too large nor too big. ) Overall, UCB seems to perform best.


## 3 Finite Markov Decision Processes (RL problems in terms of optimal control of Markov decision processes)
* The general problem formulation that is—**finite markov decision processes**—and its main ideas including **Bellman equations** and **value functions**.
* This problem defines the field of reinforcement learning: any method that is suited to solving this problem we consider to be a reinforcement learning method.

### 3.1 The Agent–Environment Interface
* The RL problem is meant to be a straightforward framing of the problem of learning from **interaction** to achieve a goal.
* The learner and decision-maker is called the **agent**.
* The thing it interacts with, comprising everything outside the agent, is called the **environment**.
* The agent selecting actions and the environment responding to those actions and presenting new situations to the agent.
* 
###  3.2 Goals and Rewards
### 3.3 Returns 
### 3.4 Unified Notation for Episodic and Continuing Tasks 
* Two kinds of reinforcement learning tasks:
  * one in which the agent–environment interaction naturally breaks down into a sequence of separate episodes (episodic tasks), and
  * one in which it does not (continuing tasks).
* The **Epsisodic task** is mathematically **easier** because **each action affects only the finite number of rewards subsequently received during
the episode**.
* The episodic tasks requires some additional notation. Rather than one long sequence of time steps, we need to consider a series of episodes, each of which consists of a finite sequence of time steps. We number the time steps of each episode starting a new from zero. Therefore, we have to refer not just to **S<sub>t</sub>**, the state representation at time t, but to **S<sub>t,i</sub>**, the state representation at time t of episode i (and similarly for **A<sub>t,i</sub>**, **R<sub>t,i</sub>**, **π<sub>t,i</sub>**, **T<sub>i</sub>**, etc.).
* However, it turns out that, when we discuss episodic tasks we will almost never have to distinguish between different episodes. We will almost always be considering a particular single episode, or stating something that is true for all episodes.
* Accordingly, in practice we will almost always abuse notation slightly by dropping the explicit reference to episode number. That is, we will write **S<sub>t</sub>** to refer to **S<sub>t,i</sub>**, and so on.
* We need one other convention to obtain a single notation that covers both episodic and continuing tasks. We have defined the **return as a sum over a finite number of terms in one case (G<sub>t</sub> = R<sub>t+1</sub> + R<sub>t+2</sub> + R<sub>t+3</sub> + · · · + R<sub>T</sub> )** and as a **sum over an infinite number of terms in the other (G<sub>t</sub> = R<sub>t+1</sub> + γR<sub>t+2</sub> + γ<sup>2</sup>R<sub>t+3</sub> + · · · )**. These can be unified by considering episode termination to be the entering of a special absorbing state that transitions only to itself and that generates only rewards of zero.
* For example, consider the state transition diagram

<img width="858" alt="Image" src="https://github.com/user-attachments/assets/3b7c6fa0-79a5-415d-a85e-4559d23b4fa6" />

  * solid square represents the special absorbing state corresponding to the end of an episode. Starting from $S_{0}$, we get the reward sequence **+1, +1, +1, 0, 0, 0, . . .**.
  * Summing these, we get the same return whether we sum over the first T rewards (here T = 3) or over the full infinite sequence.
  * This remains true even if we introduce discounting.
  * Thus, we can define the return, in general, according to (3.2), using the convention of omitting episode numbers when they are not needed, and including the possibility that γ = 1 
     if the sum remains defined (e.g., because all episodes terminate)
   Alternatively, we can also write the return as

including the possibility that T = ∞ or γ = 1 (but not both6
). We use these
conventions throughout the rest of the book to simplify notation and to express
the close parallels between episodic and continuing tasks.
### 3.5 The Markov Property 
### 3.6 Markov Decision Processes 
* A reinforcement learning task that satisfies the Markov property is called a Markov decision process, or MDP.
* If the state and action spaces are finite, then it is called a finite Markov decision process (finite MDP).
* A particular finite MDP is defined by its state and action sets and by the one-step dynamics of the environment. Given any state and action s and a, the probability of each possible pair of next state and reward, s', r, is denoted

<div align="center">
\left(s^{\prime}, r \mid s, a\right)=\operatorname{Pr}\left\{S_{t+1}=s^{\prime}, R_{t+1}=r \mid S_t=s, A_t=a\right\} .
</div>


### 3.7 Value Functions 
### 3.8 Optimal Value Functions 
### 3.9 Optimality and Approximation 
### 3.10 Summary 
* The elements of the reinforcement learning problem:
* Reinforcement learning is about learning from interaction how to behave in order to achieve a goal.
* The reinforcement learning agent and its environment interact over a sequence of discrete time steps.
* The specification of their interface defines a particular task:
  * the actions are the choices made by the agent;
  * the states are the basis for making the choices;
  * and the rewards are the basis for evaluating the choices.
* Everything inside the agent is completely known and controllable by the agent; everything outside is incompletely controllable but may or may not be completely known.
* A policy is a stochastic rule by which the agent selects actions as a function of states.
* The agent’s objective is to maximize the amount of reward it receives over time.
* The return is the function of future rewards that the agent seeks to maximize. It has several different definitions depending upon the nature of the task and whether one wishes to discount delayed reward.
* The undiscounted formulation is appropriate for episodic tasks, in which the agent–environment interaction breaks naturally into episodes; the discounted formulation is appropriate for continuing tasks, in which the interaction does not naturally break into episodes but continues without limit.
* An environment satisfies the Markov property if its state signal compactly summarizes the past without degrading the ability to predict the future. This is rarely exactly true, but often nearly so; the state signal should be chosen or constructed so that the Markov property holds as nearly as possible. We assume that this has already been done and focus on the decision making problem: how to decide what to do as a function of whatever state signal is available.
* If the Markov property does hold, then the environment is called a **Markov decision process (MDP)**.
* A finite MDP is an MDP with finite state and action sets. Most of the current theory of reinforcement learning is restricted to finite MDPs, but the methods and ideas apply more
generally.
* A policy’s value functions assign to each state, or state–action pair, the expected return from that state, or state–action pair, given that the agent uses the policy.
* The optimal value functions assign to each state, or state–action pair, the largest expected return achievable by any policy.
* A policy whose value functions are optimal is an **optimal policy**. Whereas the **optimal value functions for states and state–action pairs are unique for a given MDP**, there can be many optimal policies.
* Any policy that is greedy with respect to the optimal value functions **must be an optimal policy**.
* The **Bellman optimality equations are special consistency condition** that the optimal value functions must satisfy and that can, in principle, be solved for the optimal value functions, from which an optimal policy can be determined with relative ease.
* A reinforcement learning problem can be posed in a variety of different ways depending on assumptions about the level of knowledge initially available to the agent.
* In problems of complete knowledge, the agent has a complete and accurate model of the environment’s dynamics. If the environment is an MDP, then such a model consists of the one-step transition probabilities and expected rewards for all states and their allowable actions.
* In problems of incomplete knowledge, a complete and perfect model of the environment is not available.
* Even if the agent has a complete and accurate environment model, the agent is typically unable to perform enough computation per time step to fully use it.
* The memory available is also an important constraint. Memory may be required to build up accurate approximations of value functions, policies, and models. In most cases of practical interest there are far more states than could possibly be entries in a table, and approximations must be made.
* A well-defined notion of optimality organizes the approach to learning and provides a way to understand the theoretical properties of various learning algorithms, but it is an ideal that reinforcement learning agents can only approximate to varying degrees.
* In reinforcement learning we are very much concerned with cases in which optimal solutions cannot be found but must be approximated in some way.

## 4 Dynamic Programming 
* method for solving finite Markov decision problems
* Dynamic programming methods are well developed mathematically, but **require a complete and accurate model of the environment**.
* We can easily obtain optimal policies once we have found the optimal value functions, v_{∗} or q_{∗}, which satisfy the Bellman optimality equations:

$$
\begin{aligned}
&\begin{aligned}
v_*(s) & =\max _a \mathbb{E}\left[R_{t+1}+\gamma v_*\left(S_{t+1}\right) \mid S_t=s, A_t=a\right] \\
& =\max _a \sum_{s^{\prime}, r} p\left(s^{\prime}, r \mid s, a\right)\left[r+\gamma v_*\left(s^{\prime}\right)\right]
\end{aligned}\\
&\text { or }\\
&\begin{aligned}
q_*(s, a) & =\mathbb{E}\left[R_{t+1}+\gamma \max _{a^{\prime}} q_*\left(S_{t+1}, a^{\prime}\right) \mid S_t=s, A_t=a\right] \\
& =\sum_{s^{\prime}, r} p\left(s^{\prime}, r \mid s, a\right)\left[r+\gamma \max _{a^{\prime}} q_*\left(s^{\prime}, a^{\prime}\right)\right]
\end{aligned}
\end{aligned}
$$

for all s ∈ S, a ∈ A(s), and s^{'} ∈ S^{+}. 
* As we shall see, **DP algorithms are obtained** by **turning Bellman equations** such as these into assignments, that is, into update rules for improving approximations of the desired value functions.
* 
### 4.1 Policy Evaluation 
* First we consider how to compute the state-value function vπ for an arbitrary policy π. This is called policy evaluation in the DP literature. We also refer to it as the prediction problem. Recall from Chapter 3 that, for all s ∈ S,

$$
\begin{aligned}
v_\pi(s) & =\mathbb{E}_\pi\left[R_{t+1}+\gamma R_{t+2}+\gamma^2 R_{t+3}+\cdots \mid S_t=s\right] \\
& =\mathbb{E}_\pi\left[R_{t+1}+\gamma v_\pi\left(S_{t+1}\right) \mid S_t=s\right] \\
& =\sum_a \pi(a \mid s) \sum_{s^{\prime}, r} p\left(s^{\prime}, r \mid s, a\right)\left[r+\gamma v_\pi\left(s^{\prime}\right)\right]
\end{aligned}
$$

where π(a|s) is the probability of taking action a in state s under policy π, and the expectations are subscripted by π to indicate that they are conditional on π being followed. 
* The existence and uniqueness of vπ are guaranteed as long as either γ < 1 or eventual termination is guaranteed from all states under the policy π.
* If the environment’s dynamics are completely known, then (4.4) is a system of |S| simultaneous linear equations in |S| unknowns (the vπ(s), s ∈ S). In principle, its solution is a straightforward, if tedious, computation. For our purposes, iterative solution methods are most suitable. Consider a sequence of approximate value functions v_{0}, v_{1}, v_{2}, . . ., each mapping S^{+} to R. The initial approximation, v_{0}, is chosen arbitrarily (except t
### 4.2 Policy Improvement 
### 4.3 Policy Iteration 
### 4.4 Value Iteration 
### 4.5 Asynchronous Dynamic Programming
### 4.6 Generalized Policy Iteration 
* Policy iteration consists of two simultaneous, interacting processes:
  *  one making the value function consistent with the current policy (policy evaluation),
  *  the other making the policy greedy with respect to the current value function (policy improvement).
* In policy iteration, these two processes alternate, each completing before the other begins, but this is not really necessary.
* In value iteration, for example, only a single iteration of policy evaluation is performed in between each policy improvement.
* In asynchronous DP methods, the evaluation and improvement processes are interleaved at an even finer grain.
* In some cases a single state is updated in one process before returning to the other. As long as both processes continue to update all states, the ultimate result is typically the same—convergence to the optimal value function and an optimal policy.
* Generalized policy iteration (GPI) : **the general idea of policy evaluation and policy improvement processes**.
*  Almost all RL methods are well described as GPI. That is, all have identifiable policies and value functions, with the policy always being improved with respect to the value function and the value function always being driven toward the value function for the policy. This overall schema for GPI is:

    
* It is easy to see that if both the evaluation process and the improvement process stabilize, that is, no longer produce changes, then the value function and policy must be optimal.
* The value function stabilizes only when it is consistent with the current policy, and the policy stabilizes only when it is greedy with respect to the current value function. Thus, both processes stabilize only when a policy has been found that is greedy with respect to its own evaluation function. This implies that the Bellman optimality equation holds, and
thus that the policy and the value function are optimal.
* The evaluation and improvement processes in GPI can be viewed as both competing and cooperating. They compete in the sense that they pull in opposing directions.
* Making the policy greedy with respect to the value function typically makes the value function incorrect for the changed policy, and making the value function consistent with the policy typically causes that policy no longer to be greedy.
* In the long run, however, these two processes interact to find a single joint solution: the optimal value function and an optimal policy.
* One might also think of the interaction between the evaluation and improvement processes in GPI in terms of two constraints or goals—for example, as two lines in two-dimensional space.

### 4.7 Efficiency of Dynamic Programming 
* DP may **not be practical for very large problems**, but **compared with other methods for solving MDP**s, DP methods are actually **quite efficient**.
* The **(worst case) time** DP methods take **to find an optimal policy is polynomial** in the number of states and actions.
* If n and m denote the number of states and actions, this means that a DP method takes a number of computational operations that is less than some polynomial function of n and m.
* A DP method is **guaranteed to find an optimal policy in polynomial time** even though the total number of (deterministic) policies **is mn**.
* In this sense, DP is **exponentially faster than any direct search** in policy space could be, because direct search would have to exhaustively examine each policy to provide the same guarantee.
* Linear programming methods can also be used to solve MDPs, and in some cases their worst-case convergence guarantees are better than those of DP methods. But linear programming methods become impractical at a much smaller number of states than do DP methods (by a factor of about 100).
* For the largest problems, only DP methods are feasible.
* DP is sometimes thought to be of limited applicability because of the curse of dimensionality (Bellman, 1957a), the fact that the number of states often grows exponentially with the number of state variables. Large state sets do create difficulties, but these are inherent difficulties of the problem, not of DP as a solution method. In fact, DP is comparatively better suited to handling large state spaces than competing methods such as direct search and linear programming.
* In practice, DP methods can be used with today’s computers to solve MDPs with millions of states. Both policy iteration and value iteration are widely used, and it is not clear which, if either, is better in general. In practice, these methods usually converge much faster than their theoretical worst-case
run times, particularly if they are started with good initial value functions or policies.
* On problems with **large state spaces**, **asynchronous DP methods are often preferred**. To complete even one sweep of a synchronous method requires computation and memory for every state. For some problems, even this much memory and computation is impractical, yet the problem is still potentially solvable because only a relatively few states occur along optimal solution trajectories. Asynchronous methods and other variations of GPI can be applied in such cases and may find good or optimal policies much faster than synchronous methods can.

### 4.8 Summary 
* The basic ideas and algorithms of **dynamic programming** as they relate **to solving finite MDPs**.
* **Policy evaluation** refers to the (typically) **iterative computation of the value functions for a given policy**.
* **Policy improvement** refers to the **computation of an improved policy given the value function for that policy**.
* **Policy iteration/Value iteration  = Policy evaluation + Policy improvement**  (two most popular DP methods)
*  **Policy iteration/Value iteration** can be used to reliably **compute optimal policies and value functions for finite MDPs** given complete knowledge of the MDP.
* **Classical DP** methods operate in **sweeps through the state set**, performing a full backup operation on each state.
  * Each backup updates the value of one state based on the values of all possible successor states and their probabilities of occurring.
  * Full backups are closely related to Bellman equations: they are little more than these equations turned into assignment statements.
  * When the backups no longer result in any changes in value, convergence has occurred to values that satisfy the corresponding Bellman equation.
  * Just as there are four primary value functions (vπ, v∗, qπ, and q∗), there are four corresponding Bellman equations and four corresponding full backups.
  * An intuitive view of the operation of backups is given by backup diagrams.
* DP methods and almost all reinforcement learning methods, can be gained by viewing them as **generalized policy iteration (GPI)**.
* **GPI** is the general idea of two interacting processes revolving around an approximate policy and an approximate value function.
  * One process takes the policy as given and performs some form of policy evaluation, changing the value function to be more like the true value function for the policy.
  * The other process takes the value function as given and performs some form of policy improvement, changing the policy to make it better, assuming that the value function is its 
    value function.
* Although each process changes the basis for the other, overall they work together to find a joint solution: **a policy and value function that are unchanged by either process and, 
consequently, are optimal.**
* In some cases, GPI can be proved to converge, most notably for the classical DP methods.
* In other cases convergence has not been proved, but still the idea of GPI improves our understanding of the methods.
* It is not necessary to perform DP methods in complete sweeps through the state set.
* Asynchronous DP methods are in-place iterative methods that back up states in an arbitrary order, perhaps stochastically determined and using out-of-date information. Many of these methods can be viewed as fine-grained forms of GPI.
* Special property of DP methods: All of them update estimates of the values of states based on estimates of the values of successor states. That is, they update estimates on the basis of other estimates **(bootstrapping)**.
* Many reinforcement learning methods perform bootstrapping, even those that do not require, as DP requires, a complete and accurate model of the environment.
* In the next chapter we explore reinforcement learning methods that do not require a model and do not bootstrap. In the chapter after that we explore methods that do not require
a model but do bootstrap.

## 5 Monte Carlo Methods 
* method for solving finite Markov decision problems.
* Monte Carlo methods don’t require a model **(no model)** and are conceptually simple, but are not suited for step-by-step incremental computation **(not incremental)**.
*  learning methods for solving the full reinforcement learning problem.
*  methods that do not require a model and do not bootstrap.
### 5.1 Monte Carlo Prediction
### 5.2 Monte Carlo Estimation of Action Values 
### 5.3 Monte Carlo Control 
### 5.4 Monte Carlo Control without Exploring Starts 
### 5.5 Off-policy Prediction via Importance Sampling
### 5.6 Incremental Implementation 
### 5.7 Off-Policy Monte Carlo Control
### 5.8 Importance Sampling on Truncated Returns
### 5.9 Summary

## 6 Temporal-Difference Learning 
* method for solving finite Markov decision problems
* TD learning is a combination of Monte Carlo ideas and dynamic programming (DP) ideas
* Temporal-difference methods require **no model** and are **fully incremental**, but are more **complex** to analyze.
* methods that do not require a model but **do bootstrap**.
* Like Monte Carlo methods, TD methods can learn directly from raw experience without a model of the environment’s dynamics.
* Like DP, TD methods update estimates based in part on other learned estimates, without waiting for a final outcome (they bootstrap).
* we start by focusing on the **policy evaluation or prediction problem**, that of estimating the value function v_{π} for a given policy π. For the control problem (finding an optimal policy), DP, TD, and Monte Carlo methods all use **some variation of generalized policy iteration (GPI)**. The differences in the methods are primarily **differences in their approaches** to the prediction problem.
### 6.1 TD Prediction 
* As Both TD and Monte Carlo methods use experience to solve the prediction problem.
* Given some experience following a policy π, both methods updatetheir estimate v of v_{π} for the nonterminal states S_{t} occurring in that experience.
* Roughly speaking, Monte Carlo methods wait until the return following the visit is known, then use that return as a target for V (S_{t}).
* A simple every-visit Monte Carlo method suitable for nonstationary environments is

$$
\begin{equation}
V\left(S_t\right) \leftarrow V\left(S_t\right)+\alpha\left[G_t-V\left(S_t\right)\right]
\end{equation}
$$

where $G_t$ is the actual return following time $t$, and \alpha$ is a constant stepsize parameter .

  Let us call this method constant-$\alpha$ MC. 
  
  Whereas Monte Carlo methods must wait until the end of the episode to determine the increment to $V\left(S_t\right)$ (only then is $G_t$ known), TD methods need wait only until the 
  next time step. 
  
  At time $t+1$ they immediately form a target and make a useful update using the observed reward $R_{t+1}$ and the estimate $V\left(S_{t+1}\right)$. 

The simplest TD method, known as $T D(0)$, is
### 6.2 Advantages of TD Prediction Methods 
### 6.3 Optimality of TD(0) 
### 6.4 Sarsa: On-Policy TD Control 
### 6.5 Q-Learning: Off-Policy TD Control 
### 6.6 Games, Afterstates, and Other Special Cases
### 6.7 Summary

##### NOTE : DP, MC, TD methods are differ swith respect to their efficiency and speed of convergence.

## 7 Eligibility Traces(λ) 
* Describe how DP, MC, TD methods can be combined to obtain the best features of each of them.
* Describe how the strengths of Monte Carlo methods can be combined with the strengths of temporal-difference methods via the use of eligibility traces.
* TD(λ) algorithm, which seamlessly integrates TD and Monte Carlo methods.
* Eligibility traces are one of the basic mechanisms of reinforcement learning. For example, in the popular TD(λ) algorithm, the **λ refers to the use of an
eligibility trace**. Almost **any temporal-difference (TD) method, such as Qlearning or Sarsa, can be combined with eligibility traces** to obtain a more general method that may learn more efficiently.
* There are two ways to view eligibility traces.
  * One way is,they are a bridge from TD to Monte Carlo methods. When TD methods are augmented with eligibility traces, they produce a family of methods spanning a spectrum that has 
    Monte Carlo methods at one end and one-step TD methods at the other.In between are intermediate methods that are often better than either extreme method. In this sense eligibility 
    traces unify TD and Monte Carlo methods in a valuable and revealing way.
  * The other way to view eligibility traces is more mechanistic. From this perspective, an eligibility trace is a temporary record of the occurrence of an event, such as the visiting 
    of a state or the taking of an action. The trace marks the memory parameters associated with the event as eligible for undergoing learning changes. When a TD error occurs, only 
    the eligible states or actions are assigned credit or blame for the error. Thus, eligibility traces help bridge the gap between events and training information. Like TD methods 
    themselves, eligibility traces are a basic mechanism for temporal credit assignment.
* For reasons that will become apparent shortly, the more theoretical view of eligibility traces is called **the forward view**, and the more mechanistic view is called the **backward view**.
* The forward view is most useful for understanding what is computed by methods using eligibility traces, whereas the backward view is more appropriate for developing intuition about the algorithms them selves.
* We will see both views and then establish senses in which they are equivalent, that is, in which they describe the same algorithms from two points of view. As usual, we first consider the prediction problem and then the control problem. That is, we first consider **how eligibility traces are used to help in predicting returns as a function of state for a fixed policy** (i.e., in estimating v_{π}). Only after exploring the two views of eligibility traces within this prediction setting do we extend the ideas to action valuesand control 
 methods.
### 7.1 n-Step TD Prediction
### 7.2 The Forward View of TD(λ) 
### 7.3 The Backward View of TD(λ) 
### 7.4 Equivalences of Forward and Backward Views 
### 7.5 Sarsa(λ) 
### 7.6 Watkins’s Q(λ) 
### 7.7 Off-policy Eligibility Traces using Importance Sampling 
### 7.8 Implementation Issues 
### 7.9 Variable λ 
### 7.10 Conclusions 

## 8 Planning and Learning with Tabular Methods 
* Describe how DP, MC, TD methods can be combined to obtain the best features of each of them.
* We will see how MC, TD learning methods can be combined with model learning and planning methods (such as dynamic programming) for a complete and unified solution to the tabular reinforcement learning problem.
* 
### 8.1 Models and Planning 
### 8.2 Integrating Planning, Acting, and Learning 
### 8.3 When the Model Is Wrong 

### 8.4 Prioritized Sweeping 
### 8.5 Full vs. Sample Backups 
### 8.6 Trajectory Sampling 
### 8.7 Heuristic Search 
### 8.8 Monte Carlo Tree Search 
### 8.9 Summary 

# II Approximate Solution Methods 
*  The approximate methods only find approximate solutions, but which in return can be applied effectively to much larger problems.
*  
## 9 On-policy Approximation of Action Values(reinforcement learning systems that simultaneously learn by trial and error, learn a model of the environment, and use the model for planning)

### 9.1 Value Prediction with Function Approximation 
### 9.2 Gradient-Descent Methods
### 9.3 Linear Methods 
### 9.4 Control with Function Approximation 
### 9.5 Should We Bootstrap? 
### 9.6 Summary 

## 10 Off-policy Approximation of Action Values 

## 11 Policy Approximation 
### 11.1 Actor–Critic Methods 
### 11.2 Eligibility Traces for Actor–Critic Methods
### 11.3 R-Learning and the Average-Reward Setting 
