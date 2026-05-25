###  Understanding Linear Transformations and Matrices in 2D

### Core Concepts and Definitions

- **Linear Transformation**: A special type of function that takes an input vector and outputs another vector, with two key properties:
  1. **Lines remain lines** (no curvature introduced).
  2. **The origin remains fixed**.
  
- **Transformation Visualization**: Instead of viewing vectors as arrows, consider each vector as a point in space where the arrow tip lands. The transformation can be understood by watching how an infinite grid of these points moves.

- **Grid Lines Behavior in Linear Transformations**: Grid lines after a linear transform remain parallel and evenly spaced, preserving linearity and spatial relationships. Nonlinear transformations cause curvature or move the origin, violating linearity.

---

### Relationship Between Linear Transformations and Matrices

- Any 2D linear transformation is **completely determined by where the basis vectors**, $\hat{i}$ (1,0) and $\hat{j}$ (0,1), land after the transformation.

- For any vector $$ \mathbf{v} = x \hat{i} + y \hat{j}, $$ its transformed position is:

  $$
  \mathbf{T}(\mathbf{v}) = x \mathbf{T}(\hat{i}) + y \mathbf{T}(\hat{j})
  $$

  Thus, knowing $\mathbf{T}(\hat{i})$ and $\mathbf{T}(\hat{j})$ determines the transformation of all vectors.

- The coordinates of transformed basis vectors are packaged into a **$2 \times 2$ matrix** as columns:

  | Matrix Form | Description            |
  |-------------|------------------------|
  | $ \begin{bmatrix} A & B \\ C & D \end{bmatrix} $ | Columns are images of $\hat{i}$ and $\hat{j}$ respectively: $ \mathbf{T}(\hat{i}) = \begin{bmatrix} A \\ C \end{bmatrix} $, $ \mathbf{T}(\hat{j}) = \begin{bmatrix} B \\ D \end{bmatrix} $ |

- The transformation applied to vector $$\mathbf{v} = \begin{bmatrix} x \\ y \end{bmatrix}$$ is:

  $$
  \begin{bmatrix} A & B \\ C & D \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} Ax + By \\ Cx + Dy \end{bmatrix}
  $$

- This defines the **matrix-vector multiplication** process as applying a linear transformation.

---

### Examples of Linear Transformations and Their Matrices

| Transformation       | $\mathbf{T}(\hat{i})$   | $\mathbf{T}(\hat{j})$   | Matrix Representation                   |
|----------------------|-------------------------|-------------------------|-----------------------------------------|
| 90° Counterclockwise Rotation | $\begin{bmatrix}0 \\ 1\end{bmatrix}$        | $\begin{bmatrix} -1 \\ 0 \end{bmatrix}$       | $\begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$  |
| Shear                | $\begin{bmatrix}1 \\ 0\end{bmatrix}$        | $\begin{bmatrix}1 \\ 1\end{bmatrix}$          | $\begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$   |
| Given matrix example  | $ \begin{bmatrix}1 \\ 2 \end{bmatrix}$      | $ \begin{bmatrix}3 \\ 1 \end{bmatrix}$         | $\begin{bmatrix} 1 & 3 \\ 2 & 1 \end{bmatrix}$   |

- If the columns of a matrix (transformed basis vectors) are **linearly dependent** (one is a scalar multiple of the other), the transformation "squishes" 2D space onto a line, the one-dimensional span of those vectors.

---

### Key Insights and Takeaways

- **Linear transformations keep the origin fixed and preserve straight lines**, making them geometrically interpretable instead of arbitrary functions.

- **Matrices are a compact representation of linear transformations**, where columns correspond to images of basis vectors.

- **Matrix-vector multiplication is the computational method** to find where any vector lands after applying a linear transformation.

- This perspective allows visual understanding and prevents rote memorization of matrix operations; instead, the operations become intuitively linked to geometric transformations.

- Understanding this foundational idea is crucial for deeper linear algebra topics such as matrix multiplication, determinants, change of basis, and eigenvalues.

---



