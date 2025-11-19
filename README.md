# Kissing Number Problem

This repository explores the **Kissing Number Problem**, a fundamental question in geometry and number theory.

## Introduction

The **Kissing Number** (denoted as K(n)) is defined as the maximum number of non-overlapping unit spheres that can simultaneously touch a central unit sphere in an $n$-dimensional Euclidean space. 

This problem famously originated from a disagreement between Isaac Newton and David Gregory in 1694 regarding the kissing number in 3 dimensions ($n=3$). Newton correctly conjectured the answer was 12, while Gregory believed 13 might be possible. The problem connects deeply to sphere packing, error-correcting codes, and information theory.

While the answer is known for a few specific dimensions (e.g., 1, 2, 3, 4, 8, and 24), finding the exact kissing number for general high-dimensional spaces remains an open mathematical challenge.

## Mathematical Statements

The problem can be formulated in two equivalent ways: using explicit coordinates or using a Gram matrix.

### 1. Coordinate Formulation
*Source: [KissingNumber-Wikipedia](https://en.wikipedia.org/wiki/Kissing_number#Mathematical_statement)*

In the coordinate domain, the problem is to determine the maximal number of $N$ vectors in $D$-dimensional space that satisfy specific distance constraints.

Let $x_1, x_2, \dots, x_N \in \mathbb{R}^D$ be the position vectors of the centers of the $N$ surrounding spheres. Assuming the central sphere and all surrounding spheres have a radius of $1/2$ (so the centers are at distance 1 from the origin), the conditions are:

1.  **Tangent with Central Sphere:** All centers must lie on the unit sphere.

$$x_i^T x_i = 1 \quad \forall i \in \{1, \dots, N\}$$

2.  **Non-overlapping Condition:** The distance between any pair of surrounding spheres must be at least twice the radius (i.e., $\ge 1$).

$$(x_i - x_j)^T (x_i - x_j) \ge 1 \quad \forall i, j : i \neq j$$

These two requirements can be combined into a single existential logical statement:

$$\exists x \ \{ \forall _ n \{ x_n^T x_n = 1 \} \land \forall _ {m, n : m \neq n} \{ (x_n - x_m)^T (x_n - x_m) \ge 1 \} \}$$

### 2. Gram Matrix Formulation
*Formulation used in our PackingStar Paper ([PackingStar paper](https://arxiv.org/abs/2511.13391v1))*

In our Gram matrix formulation, the problem is equivalent to determine the maximal size $N$ of a Gram matrix $G \in \mathbb{R}^{N \times N}$ that satisfies certain constraints in $D$-dimensional space. 

Let $G$ be the Gram matrix of the sphere center vectors $x_1, x_2, \dots, x_N \in \mathbb{R}^D$, where the entry $G_{ij} = \langle x_i, x_j \rangle$ represents the pairwise cosine between vectors $i$ and $j$. The Gram matrix $G$ must satisfy the following constraints:

1.  **Unit Vectors:** The diagonal entries must be 1.

$$G_{ii} = 1 \quad \forall i$$

2.  **Geometric Constraint (Kissing Condition):** The off-diagonal entries (pairwise cosines) must not exceed $1/2$ (corresponding to the $60^\circ$ separation).

$$G_{ij} \le 1/2 \quad \forall i \neq j$$

    *(Note: In specific settings of our PackingStar approach, entries may be drawn from a discrete "cosine set" $C$ derived from geometric simulations. Here we show the basic constraints required by the kissing number problem).*

3.  **Positive Semidefinite:** The matrix must be a valid inner product matrix.

$$G \succeq 0$$

4.  **Rank Constraint:** 
    For $N \le D$:   

$$\text{rank}(G) = N $$

    For $N > D$:  

$$\text{rank}(G) = D $$
