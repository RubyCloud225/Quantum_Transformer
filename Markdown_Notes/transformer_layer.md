x_0 x_1 x_2 x_3 ..... x_n
The above expression is a product of all the elements in the set. The product of all the elements
in a set is called the product of the set. The product of a set is denoted by
x_0 x_1 x_2 x_3 ..... x_n

normalization
|
V
|
V
|
Attention Mechanism
|
V
normalization
|
V
MLP
|
V
X^1_0 X^1_1 X^1_2 X^1_3 ..... X^1_n


attention mechanism

trainable matrices are denoted by V and W . The attention mechanism is used to weight the input.

A_ij = X_i^T WX_j
A^T_ij = softmax(A_ij)
y_i =         $$\sum_{ij}*{A^i_ij}{V_xj}


options are 
- trivial attention mechanism which each patch pays attention only to itself. - almost in silos -( individual handling which could work in this situation)

- Orthogonal Transformer - quantum analogue for each of the two main components of a classical attention layer - 
    -- Linear fully connected layer - and attention matrix to capture the interaction between patches. This approach follows the classical approach more closely - 
    -- (this may also work easier as I can change each component to a quantum analogue)
    -- (this is also a good option as it is a well known approach and it is easy to implement)

- Compound Transformer - second order compount matrix - 
    -- uses quantum layers to load all patches into a quantum circuit in uniform superposition and then apply a single unitary to multiple the input vector in the superposition. 

*** Data Loader 
X e R^nxd matrix where top register uses N quibits and the vector data loader to load the norms of each row ( ||x_1||, ...., ||x_n) to obtain the state 1/||x||$$\sum_{n}{i=1}*||x_i|| | e_i >

lower register is for d qubits to load each row x_i e r^d sequentially by applying the vector and their adjoint for each row x_i with CNOts controlled by the corresponding qubit i for the top register.

each one at the lower register has depth o(logd).s

Load ||X|| - load all patches into a quantum circuit in uniform superposition
Load |X_1 > Load < X_2| Load |X_2 > - - - - Load < X_n | Load | X_n >

each inteval send the data point back to the load ||X|| circuit 






