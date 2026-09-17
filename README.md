# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
'''
Program to QR decomposition using the Gram-Schmidt method
Developed by: Nather Nabeel S A C
RegisterNumber: 212224100040
'''

import os
os.environ["OPENBLAS_NUM_THREADS"] = "1"

import numpy as np

# Input matrix
A = np.array([[1, 1, 0],
              [1, 0, 1],
              [0, 1, 1]], dtype=float)

# Number of rows and columns
m, n = A.shape

# Initialize Q and R
Q = np.zeros((m, n))
R = np.zeros((n, n))

# Gram-Schmidt process
for j in range(n):
    v = A[:, j].copy()

    for i in range(j):
        R[i, j] = np.dot(Q[:, i], A[:, j])
        v = v - R[i, j] * Q[:, i]

    R[j, j] = np.linalg.norm(v)

    if R[j, j] != 0:
        Q[:, j] = v / R[j, j]

# Display result
print("The Q Matrix is")
print(Q)

print("The R Matrix is")
print(R)

## Output

<img width="1205" height="968" alt="image" src="https://github.com/user-attachments/assets/374c0426-17e6-4fab-9e45-7aad02e60e6b" />




## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
