**Name:** SOWMYA BADONI
**Register Number:** 212223230211

## Aim: 
Construct a Python code to find the sequence of hidden states by the known sequence of observances using Hidden Markov Model. Consider two hidden states Sunny and Rainy with observable states,happy and sad.

## Algorithm:

Step 1:Define the transition matrix, which specifies the probability of transitioning from  one hidden state to another.<br>
Step 2:Define the emission matrix, which specifies the probability of observing each possible observation given each hidden state.<br>
Step 3:Define the initial probabilities, which specify the probability of starting in each possible hidden state.<br>
Step 4:Define the observed sequence, which is the sequence of observations need to  be analyzed.<br>
Step 5:Initialize the alpha matrix with zeros, where each row represents a time step and each column represents a possible hidden state.<br>
Step 6:Calculate the first row of the alpha matrix by multiplying the initial  probabilities by the emission probabilities for the first observation.<br>
Step 7:Loop through the rest of the observed sequence and calculate the rest of the alpha matrix by multiplying the emission probabilities by the sum of the product of 
       the previous row of the alpha matrix and the corresponding row of the transition matrix.<br>
Step 8:Calculate the probability of the observed sequence by summing the last row of the alpha matrix.<br>
Step 9:Find the most likely sequence of hidden states by selecting the hidden state with the highest probability at each time step based on the alpha matrix.<br>

## Program:
```py
import numpy as np
trasition_matrix = np.array([[0.7,0.3],[0.4,0.6]])
emission_matrix = np.array([[0.1,0.9],[0.8,0.2]])
initial_probablities = np.array([0.5,0.5])
observed_sequence = np.array([1,1,1,0,0,1])
alpha = np.zeros((len(observed_sequence),len(initial_probablities)))
alpha[0, :] = initial_probablities * emission_matrix[:,observed_sequence[0]]
for t in range(1,len(observed_sequence)):
    for j in range(len(initial_probablities)):
        alpha[t,j] = emission_matrix[j,observed_sequence[t]] * np.sum(alpha[t-1,:] * trasition_matrix[:,j])
probability = np.sum(alpha[-1, :])
print("The probability of observed sequence is:",probability)
most_likely_sequence = []
for t in range(len(observed_sequence)):
    if alpha[t,0] > alpha[t,1]:
        most_likely_sequence.append("sunny")
    else:
        most_likely_sequence.append("rainy")
print("The most likely sequence of weather is:",most_likely_sequence)
```

## Output:

<img width="665" alt="Screenshot 2025-04-16 at 11 42 03 AM" src="https://github.com/user-attachments/assets/4a205a1d-b504-42f7-9702-ab360411eb8b" />

<img width="988" alt="Screenshot 2025-04-16 at 11 41 06 AM" src="https://github.com/user-attachments/assets/d17ec691-fb0f-465c-956e-b4ca6e117bd9" />


## Result:
Thus Hidden Markov Model is implemented using python.

