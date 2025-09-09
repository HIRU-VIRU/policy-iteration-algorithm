# POLICY ITERATION ALGORITHM

## AIM
To develop a Python program to find the optimal policy for the given MDP using the policy iteration algorithm.


## PROBLEM STATEMENT
The aim of this experiment is to find optimal policy for the mdp using policy iteration. Policy iteration includes policy evaluation and policy improvement where evaluation function is used to find optimal value function of each state and then improvement function is used to find best policy by comparing all the action value function as well as policy.
## POLICY ITERATION ALGORITHM

# Step1 :
we are going to do policy evaluation of each state to get the state value function where the initial policy is defined randomly to the mdp.

# Step2:
Once we obtain convergence in the policy evaluation then implement policy improvement where we are going to find best optimal policy until the previous and current policy are same

## POLICY IMPROVEMENT FUNCTION
### Name: HIRUTHIK SUDHAKAR
### Register Number: 212223240054
```
def policy_improvement(V, P, gamma=1.0):
  Q=np.zeros((len(P),len(P[0])))
  for s in range(len(P)):
      for a in range(len(P[s])):
          for prob, next_state, reward, done in P[s][a]:
              Q[s][a] += prob * (reward + gamma * V[next_state] * (not done))
  new_pi = lambda s: {s:a for s, a in enumerate(np.argmax(Q, axis=1))}[s]
  return new_pi

```
## POLICY ITERATION FUNCTION
### Name: HIRUTHIK SUDHAKAR
### Register Number: 212223240054
```
def policy_iteration(P, gamma=1.0, theta=1e-10):
    # Write your code here for policy iteratioN
    random_actions= np.random.choice(tuple(P[0].keys()), len(P))
    pi = lambda s: {s:a for s, a in enumerate(random_actions)}[s]
    while True:
      old_pi={s:pi(s) for s in range(len(P))}
      V = policy_evaluation(pi, P, gamma, theta)
      pi = policy_improvement(V, P, gamma)
      if old_pi == {s:pi(s) for s in range(len(P))}:
        break




    return V, pi
```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy


<img width="712" height="251" alt="image" src="https://github.com/user-attachments/assets/2fed93f5-327a-47cd-8929-396878598321" />

<img width="500" height="135" alt="image" src="https://github.com/user-attachments/assets/82ef2f9a-d476-4d99-9ae9-544caf919a7f" />

### 2. Policy, Value function and success rate for the Improved Policy
<img width="809" height="282" alt="image" src="https://github.com/user-attachments/assets/ff02eb2f-f12c-4432-be25-ab17157e77a4" />
<img width="604" height="149" alt="image" src="https://github.com/user-attachments/assets/d50b588c-1b1e-48aa-9cf3-a7c4c66f5425" />
<img width="510" height="169" alt="image" src="https://github.com/user-attachments/assets/d3aaf95d-c5d9-4262-bd6f-879ed7e15577" />



### 3. Policy, Value function and success rate after policy iteration
<img width="769" height="299" alt="image" src="https://github.com/user-attachments/assets/0b2caa7c-0d35-4b76-8a79-5af628fea2bb" />


<img width="800" height="129" alt="image" src="https://github.com/user-attachments/assets/f802564a-fa8f-465b-aec9-623488e74b5e" />



## RESULT:

Thus, The Python program to find the optimal policy for the given MDP using the policy iteration algorithm is successfully executed.
