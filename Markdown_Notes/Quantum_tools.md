*** Quantum Tools used in this implementation- 

RBS Gate : A Reversible Binary Switch gate is used to implement the quantum circuit. 

RBS(0) = ( 1    0   0       0)
        (  0 cos(0) sin(0)  0)
        (  0 -sin(0) cos(0) 0)
        (  0    0       0   1)

implemented by the hadamard gate and the controlled phase gate.

H -R_y(+0/2) H
H - R_y(-0/2) H
where H is the Hadamard gate and R_y(+0/2) is the controlled phase

** Data loaders for Matrics 

load a whole matix X E R^nxd in a quantum state  - designed quantum circuits to load input vectors using N = n + d qubits. with a unary amplitude encoding.

using a basis of states of hamming weight 1 where all qubits are in state 0 except one state which is in state 1. 

number of gates is O(n + d)- this is extended to 

-- pyramid nearest neighbor encoding where the depth is 2N - 3 number of gates is N(N-1)/2

-- X Nearest Neighbour Depth N - 1 number of gates 2N - 3

-- Butterfly All to all Depth Log(N) number of gates N/2 log(N)

the resulting state is a superposition of all possible input vectors.

| X > = 1/||x|| * sum_{i=1{n}}sum_{j=1{d}}{x_ij || e_j > | e_i >}

** Quantum Orthogonal Layers 
- quantum circuit applied to a state | x > (encoded in the unary basis) 

two types of new layers (in addition to pyramid) 
- X circuit
        -- smaller number of gates 
        -- less expressive with restrained set of possible orthogonal matrices but fewer trainable params ( may not be suitable given the level of control over params I want this may make that difficult and complex )
- butterfly
        -- logarithmic circuit depth 
        -- linear number of gates 
        -- higher level of expressivity

vector is loaded as a quantum state using only N qubits - output with encoded vector orthogonal to input vector

V is seen here as an expansion of V in the hamming weight bias (k)




