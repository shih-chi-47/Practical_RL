# Practical_RL
 My solution of Practical Reinforcement Learning by National Research University Higher School of Economics via [Coursera](https://www.coursera.org/learn/practical-rl).  

The [GitHub version](https://github.com/yandexdataschool/Practical_RL) of the course.



# Week 1: Intro

* Reinforcement Learning
  * Multi-armed bandit
  * Decision process & applications
* Black box optimization
  * Markov decision process (MDP)
  * Crossentropy method
    * rollout experiences with stochastic policy $\pi_i$ 
    * store <s,a> pair of better reward as elite
    * update policy $\pi_{i+1}$ proportional to the occurrences of <s,a> pair in elite group
  * Approximate crossentropy method
    * 
* Evolution strategies

### gym_interface.ipynb

* Practice basic interface of OpenAI gym environment.

### crossentropy_method.ipynb

* Solved 'Taxi-v3' with crossentropy method with a table representation of policy.

### deep_crossentropy_method.ipynb

* Approximate the policy of a continuous state space game 'CartPole-v0' by multi-layer neural network (MLP)
* Train the MLP with elite <s,a> pair selected by crossentropy method

# Week 2: Dynamic Programming 

* Reward
  * Reward design
  * Discount reward
* Bellman equations
  * Value functions
  * State action value function
* Generalized policy iteration
  * Policy evaluation & improvement
  * Policy and value iteration

### practice_vi.ipynb

* Implemented value **iteration algorithm** to solve MDP problem
  * $V_{i+1}(s) = max_a \Sigma_{s'} P(s'|s,a)\cdot [r(s,a,s')+\gamma V_i(s')]$

# Week 3: Model-free Methods


* Model-free learning
  * Monte-Carlo & temporal difference; Q-learning
  * Exploration vs exploitation
* On-policy vs off-policy

### qlearning.ipynb

* implement **vanilla Q-learning algorithm**
  * $Q(s,a) \leftarrow (1-\alpha)Q(s,a) + alpha *(r+\gamma V(s'))$
* on both discrete state space environment 'Taxi-v3' and discretized continuous state space environment 'CartPole-v0'

### sarsa.ipynb

* implement **Expected Value SARSA algorithm** 
  * sample <s,a,r,s'> from environment
  * $\hat{Q}(s,a) = r(s,a) + r\mathbb{E}_{a_i \sim \pi(a|s')}Q(s',a_i)$ with probability of $a_i \sim \pi(a|s')$ being $(1-\epsilon)$ optimal action and $\epsilon$ random action
  * update $Q(s,a) \leftarrow (1-\alpha)*Q(s,a) + \alpha*\hat{Q}(s,a)$
* compare the learning curve of Q-learning and SARSA

### experience_replay.ipynb

* implement **experiment replay** for off-line policy, Q-learning in this implementation

# Week 4: Approximate Value Based Methods

* Limitations of tabular methods
* Deep Q-network

### practice_approx_qlearning_pytorch.ipynb

* implement a neural network to approximate the action-value function $Q(s,a)$
* solving continuous state space environment 'CartPole-v0'

### dqn_atari_pytorch.ipynb (not finished)

* implement DQN for 'BreakoutNoFrameskip-v4' environment
  * image processing
  * frame buffer
  * deep Q-network
  * experience replay
  * target networks

# Week 5: Policy-based Methods

* Policy-based RL vs value-based RL
  * policy gradient
* REINFORCE
  * $\nabla_\theta\hat{J}(\theta) \approx \frac{1}{N}\Sigma_{s_i,a_i}\nabla_\theta \log\pi_\theta(a_i|s_i) \cdot G_t(s_i,a_i)$
* Actor-critic method
  * advantage actor-critic

### practice_reinforce_pytorch.ipynb

* implement policy gradient method REINFORCE to solve 'CartPole-v0'

  