### Quantum Path-wise Neural Network

Load |x_i > - - V -- 

Transformer with a trivial attention mechanism where each patch pays attention only to itself.

    each input patch is multiplied by the same trainable matrix V
    and one circuit is used for each patch
                    |
                    V
    Each circuit has N = d qubits and each patch x_i is encoded in a quantum state with     
    a vector data loader
                    |
                    V
    A Quantum orthogonal layer is used to perform multiplication of each
    path with V
                    |
                    V
    The output of each circuit is a quantum state encoding
    V_xi- vector acheved through tomography.
                    |
                    V
      this deals with states of linear size in relation
      to the number of qubits - avoiding the exponential
      complexity often associated with quantum tomography

### Quantum Orthogonal Transformer




