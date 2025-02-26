# Maximization Bias
* It refers to the tendency of Q-learning algorithms to overestimate action values due to the **max** operator used in action selection. This bias arises when estimating the expected return, leading to overly optimistic Q-values and suboptimal policy learning.
* Why Does maximization bias occur?
  * Q-learning update rule:

    **Q(s,a) <--- Q(s,a) + alpha[r + gamma * max_{a'} Q(s',a') - Q(s,a)]**

    As here the next state's Q-values are approximations(often learned from limited experiences), the **max** operator tends to select actions with overestimated values due to random noise or estimation errors. Overtime, this results in a bias where Q-values become systematically overestimated, leading to poor policy decisions.

* Effects of Maximization Bias:
   * Overestimation of Q-values: the agent may learn policies based on inflated action values.
   * Suboptimal Action Selection: The agent might repeatedly choose suboptimal actions because it believes they have a higher reward than they actually do.
   * Slower Convergence: The learning process can take longer due to incorrect value estimates.
* How to mitigate Maximization Bias?
  * Double Q-learning: instead of using single Q-network, two separate Q-netwroks are maintained:
    * One netwrok selects the action :

      **a^{*} = arg max Q_{1}(s', a)**
      
    * the other one evaluate the selected action:

       **Q_{2}(s', a*) **

    * the update is done using Q_{2}, reducing overestimation.
   
       **Q_{1} (s,a) <--- Q_{1} (s,a) + alpha[r + gamma * Q_{2} (s',max_{a'} Q_{1}(s',a')) - Q_{1}(s,a)]** 

        https://proceedings.neurips.cc/paper_files/paper/2010/file/091d584fced301b442654dd8c23b3fc9-Paper.pdf

  * Another way is **Self correcting Q-learning** https://arxiv.org/pdf/2012.01100
      
    
