# ✨ Quantum Tools in This Implementation

## 🔁 RBS Gate (Reversible Binary Switch Gate)

The **RBS gate** is used to implement a quantum circuit with the following matrix representation:

\[
\text{RBS}(0) =
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & \cos(0) & \sin(0) & 0 \\
0 & -\sin(0) & \cos(0) & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
\]

This gate is **implemented using**:
- The **Hadamard gate** (H)
- The **Controlled Phase Rotation Gate** (specifically \( R_y(\pm 0/2) \))

### Gate Decomposition:
- \( H - R_y(+0/2) - H \)
- \( H - R_y(-0/2) - H \)

> Note: \( R_y(\cdot) \) refers to a rotation around the Y-axis on the Bloch sphere.

---

## 📦 Data Loaders for Matrices

To load an entire matrix \( X \in \mathbb{R}^{n \times d} \) into a quantum state, custom quantum circuits were designed using \( N = n + d \) qubits with **unary amplitude encoding**.

### Encoding Method:
- Unary basis using **Hamming weight 1 states**:
  - All qubits are in \(|0\rangle\) except one, which is in \(|1\rangle\).
- Number of gates: \( O(n + d) \)

### Extended Encoding Methods:

| Encoding Strategy                | Circuit Depth | Gate Count             |
|----------------------------------|---------------|------------------------|
| Pyramid Nearest Neighbor         | \(2N - 3\)     | \(\frac{N(N-1)}{2}\)   |
| X Nearest Neighbor               | \(N - 1\)      | \(2N - 3\)             |
| Butterfly All-to-All             | \(\log N\)     | \(\frac{N}{2} \log N\) |

### Final Quantum State:
\[
|X\rangle = \frac{1}{\|x\|} \sum_{i=1}^{n} \sum_{j=1}^{d} x_{ij} |e_j\rangle |e_i\rangle
\]

This forms a **superposition over all input vectors**.

---

## 🌀 Quantum Orthogonal Layers

These are quantum circuits applied to the state \(|x\rangle\), encoded in the **unary basis**.

### Types of Layers:

#### 1. **X Circuit**  
- Fewer gates  
- Less expressive (limited orthogonal matrices)  
- Fewer trainable parameters  
- ⚠️ May not allow fine-grained parameter control

#### 2. **Butterfly Circuit**  
- Logarithmic circuit depth  
- Linear gate count  
- ✅ Higher expressivity

---

## 📈 Summary

- Vectors are loaded into quantum states using only \( N \) qubits.
- The output state is an **orthogonal transformation** of the input.
- Matrix \( V \) represents an **expansion in Hamming weight basis** \( k \).