# Cubic Stylization

## Questions:
1. Is there any quantitative measurement to evaluate the result of this method? As it is somehow closely related to artistic creation, the evaluation of stylization is highly rely on the subjective opinion. But I guess this is quite common in computer graphics?
2. How to understand the *discriminative geometric styles*? And *generative*? *Discriminative means given two styles of a same shape, and to find the transformation from one to the other.*
3. Why voxelization fails to capture the details and the wide specttrum of cubeness? Is voxelization the same as polycube maps?
4. A more general question, since I am totally a newbie in the field of computer graphics, are the geometry and lighting the fundamental building blocks of demostrating a shape? In our case, a method raised only from geometry perspective is discussed.
5. Why only manifold mesh is handled? What about non-manifold ones? Check [blog](http://3dprintingninja.blogspot.com/2014/07/non-manifolds-your-worst-nightmare.html) here about manifold and non-manifold.
6. Related to the energy function
     1. $minimize_{\hat{V}, \{R_i\}} \sum_{i\in V}\sum_{j\in N(i)} \frac{w_{ij}}{2} \lVert R_id_{ij} - \tilde{d}_{ij}\rVert_F^2 + \lambda a_i\lVert R_i \hat{n}_i\rVert_1$
     2. What does the cotangent weight $w_{ij}$ mean? How to understand it? [Pinkall and Polthier 1993](http://www.cs.jhu.edu/~misha/Fall09/Pinkall93.pdf) or check ASAP section 2.2. *$w_{i,j} = \frac{1}{2}(cot\alpha_{i,j} + cot\beta_{i,j})$, with $\alpha_{i,j},\beta_{i,j}$ are angles opposite of the mesh edge $(i,j)$*. Is the edge shared by two triangles?
     3. $\hat{n}_i$ denoted the unit area-weighted normal vector of a vertex in $\R^3$, what does **area-weighted** mean?
     4. What is the barycentric area, $a_i \in \R^+$? Related to barycentric coordinate?
     5. Is the Frobenius norm used in ASAP part in the energy function a custormized one? Or it comes from the original ASAP? Why using it? *It comes from the original ASAP paper and didn't explain why, I assume it is used to ease the optimization problem. Or somehow related to take different scales of variables into consideration.*
     6. Why cubeness is defined like that? Apart from L1-norm, the parameters.
     7. *The trivial solution of this energy function $R_i = 0_{3\times3}$ is not achievable because of the ASAP term.*
7. Related to ADMM
     1. What is a lasso problem? *Check the ADMM video at this [time](https://youtu.be/Xg0ozgCXXB8?t=3299), and [Wikipedia](https://en.wikipedia.org/wiki/Lasso_(statistics)). Least square problem subject to some constraints. So eq.4 is dual problem of weighted least square plus a constrait.*
     2. What is the ADMM method? Equation 4-7. *Alternating optimize the prime and the dual.* 
     3. Why this is chosen? No other solutions?
     4. How to go from eq.3 to eq.4? L1-norm to L2-norm?
     5. It guarantee to converge because the both parts of objective are convex?
     6. How eq.4 is solved? Can't wrap my head around the following steps.
8.  What does warm startig mean? "Warm starting the local-step parameters from the previous iteration." (after equation 9) *Using the previous step resulting value as the starting point.*
9.  `V` and `F` in Algorithm 1 mean Vertice and Face?
10. Why $A = (Q_iQ_i^T)^{-1}Q_i$ is the affine transformation?
11. Any explanation about why figure 17 happends? "A smaller number of faces keeps details across a wider frequency range; in contrast, a larger one doesn't."

# Motivation
This is a very interesting paper. It's interesting in the sense that the results of this scientific work narrow down the gap a little bit between an interested layman and an artist in 3D stylization. 

# Related works/terminologies

## What is the objective:
1. [ASAP (As-rigid-as-possible)](https://igl.ethz.ch/projects/ARAP/arap_web.pdf)

2. Sparsity effect of L1 norm

## How to reach the objective?
1. [ADMM (alternating direction method of multipliers)](https://web.stanford.edu/~boyd/papers/pdf/admm_distr_stats.pdf)

	Used for solving large scale optimization problems. Check video [here](https://www.youtube.com/watch?v=Xg0ozgCXXB8) and [slides](https://web.stanford.edu/~boyd/papers/pdf/admm_slides.pdf).

2. [Affine progressive mesh](http://faculty.cs.tamu.edu/schaefer/research/local_rigid.pdf)

	Used for fast convergence.

## Additional information
1. Bump mapping: [Bump mapping](https://en.wikipedia.org/wiki/Bump_mapping) is a technique in computer graphics for simulating bumps and wrinkles on the surface of an object. This is achieved by **perturbing the surface normals** of the object and using the perturbed normal during lighting calculations.
2. [Orthogonal Procrustes problem](https://en.wikipedia.org/wiki/Orthogonal_Procrustes_problem)