# POLICY ITERATION ALGORITHM

## AIM
To develop a Python program to find the optimal policy for the given MDP using the policy iteration algorithm.

## PROBLEM STATEMENT
The slippery walk problem in reinforcement learning involves an agent navigating a 7-state environment to reach a target state. Due to the environment’s unpredictable nature, the agent might end up moving in the opposite direction of its intended move, adding an extra layer of complexity to the task.

## POLICY ITERATION ALGORITHM
Initialize Policy:

Start with an arbitrary policy. In the provided code, the initial policy pi is randomly generated, where each state is assigned a random action. Policy Evaluation:

Evaluate the current policy by calculating the value function 𝑉 V for each state. This involves determining how good it is to be in each state under the current policy. This is done using the policy_evaluation function, which computes the value function 𝑉 V by solving a system of linear equations or using iterative methods until convergence (based on a threshold theta). Policy Improvement:

Improve the policy based on the value function 𝑉 V obtained from the evaluation step. This involves calculating the action-value function 𝑄 Q for each state-action pair and updating the policy to choose the action that maximizes the 𝑄 Q value. This is handled by the policy_improvement function, which returns a new policy pi where each state is assigned the action that has the highest value according to 𝑄 Q. Check for Convergence:

Compare the newly improved policy with the old policy. If the policy does not change (i.e., it is stable), then the algorithm has converged, and the process can stop. If the policy has changed, repeat the policy evaluation and policy improvement steps. Return Results:

Once the policy has converged, return the final value function 𝑉 V and the optimal policy pi.

## POLICY IMPROVEMENT FUNCTION
### Name : SANJAY 
### Register Number : 212222230132
```
def policy_improvement(V,P,gamma=1.0):
  Q=np.zeros((len(P),len(P[0])),dtype=np.float64)
  for s in range(len(P)):
    for a in range(len(P[s])):
      for prob,next_state,reward,done in P[s][a]:
        Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))
  new_pi=lambda s:{s:a for s,a in enumerate(np.argmax(Q,axis=1))}[s]
  return new_pi
```

## POLICY ITERATION FUNCTION
### Name : PRAVEEN CK
### Register Number : 212222243003
```
def policy_iteration(P, gamma=1.0, theta=1e-10):
    random_actions = np.random.choice(tuple(P[0].keys()), len(P))
    # Write your code here to implement the policy iteration algorithm
    pi=lambda s:{s:a for s,a in enumerate(random_actions)}[s]
    while True:
      old_pi={s:pi(s) for s in range(len(P))}
      V=policy_evaluation(pi,P,gamma,theta)
      pi=policy_improvement(V,P,gamma)
      if old_pi=={s:pi(s) for s in range(len(P))}:
        break
    return V, pi
```

## OUTPUT:
#### optimal policy
![image](https://github.com/user-attachments/assets/48a04e69-2c5c-4266-aee9-0118c636f078)
#### optimal value function
![image](https://github.com/user-attachments/assets/c1122a58-ecb7-4c19-be5d-79a3e7774c3f)
#### success rate for the optimal policy
![image](https://github.com/user-attachments/assets/6d2aea89-7a47-46c9-a986-002b30fa341b)


## RESULT:
Thus, a Python program is developed to find the optimal policy for the given MDP using the policy iteration algorithm.
