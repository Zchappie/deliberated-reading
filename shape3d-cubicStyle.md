# Cubic Stylization

## Questions:
* Is there any quantitative measurement to evaluate the result of this method? As it is somehow closely related to artistic creation, the evaluation of stylization is highly rely on the subjective opinion. But I guess this is quite common in computer graphics?
* How to understand the *discriminative geometric styles*? And *generative*? Discriminative means given two styles of a same shape, and to find the transformation from one to the other?
* Why voxelization fails to capture the details and the wide specttrum of cubeness? Is voxelization the same as polycube maps?
* A more general question, since I am totally a newbie in the field of computer graphics, are the geometry and lighting the fundamental building blocks of demostrating a shape? In our case, a method raised from geometry perspective is discussed.
* Related to the energy function
  * $minimize_{\hat{V}, \{R_i\}} \sum_{i\in V}\sum_{j\in N(i)} \frac{w_{ij}}{2} \lVert R_id_{ij} - \tilde{d}_{ij}\rVert_F^2 + \lambda a_i\lVert R_i \hat{n}_i\rVert_1$
  * What does the cotangent weight $w_{ij}$ mean? [Pinkall and Polthier 1993]
  * $\hat{n}_i$ denoted the unit area-weighted normal vector of a vertex in $\R^3$, what does **area-weighted** mean?
  * What is the barycentric area, $a_i \in \R^+$?
  * Is the Frobenius norm used in ASAP part in the energy function a custormized one? Or it comes from the original ASAP? Why using it?
  * The trivial solution of this energy function $\hat{n}_i = 0$ is not achievable because of the ASAP term.
* What is a `lasso` problem?
* What does warm startig mean? `Warm starting the local-step parameters from the previous iteration` 

## Motivation
This is a very interesting paper. It's interesting in the sense that the results of this scientific work narrow down the gap a little bit between an interested layman and an artist in 3D stylization. 

## Related works/terminologies
### ASAP (As-rigid-as-possible)

### Sparsity effect of L1 norm

### ADMM (alternating direction method of multipliers)
What is ADMM method?

### Affine progressive mesh

### Additional 
1. Bump mapping: [Bump mapping](https://en.wikipedia.org/wiki/Bump_mapping) is a technique in computer graphics for simulating bumps and wrinkles on the surface of an object. This is achieved by **perturbing the surface normals** of the object and using the perturbed normal during lighting calculations.