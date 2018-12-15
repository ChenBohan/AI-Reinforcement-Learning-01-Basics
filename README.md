# AI-Reinforcement-Learning-01-Basics
Reinforcement Learning Course Offered at Georgia Tech as CS 8803

## Reinforcement Learning Basics

### Ref:

[Reinforcement Learning 第一周课程笔记](https://www.jianshu.com/p/881ab7e41adb)

[Reinforcement Learning 第二周课程笔记](https://www.jianshu.com/p/413691dcaa56)

[Reinforcement Learning 第三周课程笔记](https://www.jianshu.com/p/292ca663f7b0)

[Reinforcement Learning 1.初步介绍](https://blog.csdn.net/hellocsz/article/details/80833464)

[Reinforcement Learning 2.Multi-arm Bandits Problem](https://blog.csdn.net/coffee_cream/article/details/58034628)

[Reinforcement Learning 3.Finite Markov Decision Processes](https://blog.csdn.net/coffee_cream/article/details/60473789)

[Reinforcement Learning 4.Dynamic Programming](https://blog.csdn.net/coffee_cream/article/details/62892546)

[Reinforcement Learning 5.Monte Carlo Method](https://blog.csdn.net/coffee_cream/article/details/66972281)

[Deep Reinforcement Learning 基础知识](https://blog.csdn.net/songrotek/article/details/50580904)

[Reinforcement Learning 经典算法梳理1：policy and value iteration](https://blog.csdn.net/songrotek/article/details/51378582)


### Summary

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/what_have_we_learned.png" width = "70%" height = "70%" div align=center />

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/what_have_we_learned_2.png" width = "70%" height = "70%" div align=center />

### Basic

- Supervised Learning: y = f(x), given many x, y pairs, determine function f to determine the relationship between x and y.

- Unsupervised Learning: f(x), given a lot of x, determine function f to cluster or describe x.

- Reinforcement Learning: y = f(x) with z, given x and z, determine function f which can generate y. In Markov process, we know s and r, and we need to learn π to determine a. So, s-->x, r-->z, a-->y, π-->f

RL is one of the ways to perform decision making.

- States: set of tokens which describe every state that one could be in,

- Model/Transition Function: probability that you'll end up transition to s' given you are in state s and taking action a. This is 'physics' or rules of the world(not changeable) .

- Action: A(s), things you can do in a given state, a function of state, rule you can play; or A, a set actions not depends regardless of state.

- Reward: scalar value that you get for being in a state. Usefulness of entering a state/and taking an action/and ending up into s'
S, T, A and R define the problem, policy is the solution,

  - Reward is important to define learning behaviour. **Rewards depends on domain knowledge.** Changing the reward will change the goal of agent.

- Policy: the solution, a function that takes up a state and tells an action that you'll take <s,a> while a is the correct action you want to take to maximize the reward

- *Optimal policy: π*, optimized, maximize long term expected reward. (note, from <s,a,r>, you know s, a and then know the r, based on rewards, find π*)

- Markovian property:

  - only the present matters; the transition state only depends on the current state

  - Transition model is stationary, rules doesn't change

- Delayed reward: in each state, we need figure out what action should we take to get the ultimate best rewards at the end.

- Utility of Sequences: stationary preferences, Utility of all the states is the sum of the rewards of all states.


### Bellman equation

**Policy**

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/policies.png" width = "70%" height = "70%" div align=center />

Policy is A mapping from state to action

- Optimal policy π*: the policy allow us getting the largest expected discounted rewards when we follow the policy π* .

- Utility of a state U(s) is long term expected discounted rewards from this point on; It's delayed reward.

**Bellman equation**

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/bellman_equations.png" width = "70%" height = "70%" div align=center />

π*(s) is the optimal policy given current state. ** U(s)** is the utility of the state if follow π*. Thus we get the utility of the current state is reward of current state [R(s)] plus the discounted utility from this point on. This is the Bellman Equation.

**Relation**

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/The_realation_between_bellman_equation.png" width = "70%" height = "70%" div align=center />

- in value function, V is connected by transition T and reward r. we must know transition and the reward of current state s. V is updated with respect to a state.

- in quality function, we can rely on experience to update Q, this is useful in reinforcement learning when we do not know T and R ahead of time. Q-value is updated with respect to an action.


### Behavior structures

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/behavior_structures.png" width = "70%" height = "70%" div align=center />

- Plan is a set of fixed actions. Plan won't work during learning or when the environment is only partially known or stochastic.
- Conditional Plan includes "if" statements
- Stationary policy (or Universal Plan) are mapping from state to action. it can handle stochastic very well but it is very large. There always is an optimal stationary policy.


### Evaluate

**Evaluating a policy**

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/evaluating_a_policy.png" width = "70%" height = "70%" div align=center />

The numbers in the parentheses are probabilities of choosing the sequence. R(s,a) is reward function. Return is discounted rewards.

**Evaluating a learner**

<img src="https://github.com/ChenBohan/AI-Reinforcement-Learning-01-Basics/blob/master/readme_img/evaluating_a_learner.png" width = "70%" height = "70%" div align=center />
