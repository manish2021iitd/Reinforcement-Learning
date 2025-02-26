**Derivation of Double Q-Learning from Q-Learning**  

### **1. Standard Q-Learning Update Rule**  
Q-learning is a value iteration algorithm where the Q-value of a state-action pair \( Q(s, a) \) is updated using the Bellman equation:  

$\[ Q(s,a) \leftarrow Q(s,a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') - Q(s,a) \right] \]$

where:  
- \( s, a \) are the current state and action,  
- \( s' \) is the next state,  
- \( r \) is the received reward,  
- \( $\alpha$ \) is the learning rate,  
- \( $\gamma$ \) is the discount factor,  
- \( $\max_{a'} Q(s', a')$ \) is the highest estimated Q-value for the next state.  

### **2. Overestimation Bias in Q-Learning**  
The key issue with standard Q-learning is that it uses the same Q-function for both:  
1. **Selecting the action** \( $\max_{a'} Q(s', a')$ \)  
2. **Estimating its value** \( $Q(s', a^*)$ \)  

This causes an **overestimation bias** because the max operator tends to select actions with **overestimated** values. This can lead to instability in training.

### **3. Double Q-Learning Solution**  
To reduce this bias, **Double Q-Learning** (Hasselt, 2010) introduces two separate Q-functions:  
- \( $Q_1(s, a)$ \) and \( $Q_2(s, a)$ \), which are updated separately.  

#### **Step 1: Action Selection using \( $Q_1$ \)**  
Instead of using the same Q-function for both action selection and evaluation, we use one Q-function (e.g., \( $Q_1$ \)) to select the action:

$\[ a^* = \arg\max_{a'} Q_1(s', a') \]$

#### **Step 2: Value Estimation using \( Q_2 \)**  
The second Q-function (e.g., \( $Q_2$ \)) is used to estimate the value of the chosen action:

$\[ Q_1(s,a) \leftarrow Q_1(s,a) + \alpha \left[ r + \gamma Q_2(s', a^*) - Q_1(s,a) \right] \]$

Similarly, the updates for $\( Q_2 \)$ are done by swapping their roles:

$\[ a^* = \arg\max_{a'} Q_2(s', a') \]$

$\[ Q_2(s,a) \leftarrow Q_2(s,a) + \alpha \left[ r + \gamma Q_1(s', a^*) - Q_2(s,a) \right] \]$

### **4. Summary of Double Q-Learning Update Rules**  
- **Use $\( Q_1 \)$ to select the action but $\( Q_2 \)$ to evaluate it:**  
  $\[ Q_1(s,a) \leftarrow Q_1(s,a) + \alpha \left[ r + \gamma Q_2(s', \arg\max_{a'} Q_1(s',a')) - Q_1(s,a) \right] \]$  
  
- **Use $\( Q_2 \)$ to select the action but $\( Q_1 \)$ to evaluate it:**  
  $\[ Q_2(s,a) \leftarrow Q_2(s,a) + \alpha \left[ r + \gamma Q_1(s', \arg\max_{a'} Q_2(s',a')) - Q_2(s,a) \right] \]$  

### **5. Why Does Double Q-Learning Reduce Overestimation?**  
- By **splitting the selection and evaluation** between two different Q-functions, the method **reduces bias** in action evaluation.  
- The two Q-functions independently estimate values, preventing **consistent overestimation** of action values.  
- This leads to more **stable learning** and better policy convergence.  

### **6. Conclusion**  
Double Q-Learning is a simple yet powerful improvement over Q-learning that mitigates overestimation bias, leading to better training stability and improved performance in reinforcement learning tasks.

