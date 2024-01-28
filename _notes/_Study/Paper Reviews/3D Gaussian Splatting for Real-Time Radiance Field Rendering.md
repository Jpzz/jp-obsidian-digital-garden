
#NeRF #3DGaussians

## Abstract
Achieving high visual quality still requires neural networks that are costly to train and render, while recent faster methods inevitably trade off speed for quality. For unbounded and complete scenes and 1080p resolution rendering, no current method can achieve real-time display rates.

<mark style="background: #ADCCFFA6;">Three key points</mark>
- [b] Starting from sparse points produced during camera calibration, we represent the scene with 3D Gaussians that preserve desirable properties of continuous volumetric radiance fields for scene optimization while avoiding unnecessary computation in empty space.
- [b] Perform interleaved optimization/density control of the 3D Gaussians, notably optimizing anisotropic covariance to achieve an accurate representation of the scene.
- [b] Develop a fast visibility-aware rendering algorithm that supports anisotropic splatting and both accelerates training and allow real-time rendering.


## Introduction
<mark style="background: #ADCCFFA6;">NeRF</mark>
- Neural Radiance Field methods build on continuous scene representations, typically optimizing a Multi-Layer Perceptron using volumetric ray-marching for novel-view synthesis of captured scenes. 
- [p] The continuous nature of these methods helps optimization.
- [c] The stochastic sampling required for rendering is costly and can result in noise. 
- Trade off speed and visual quality

<mark style="background: #BBFABBA6;">3D Gaussian representation </mark>
- a flexible and expressive scene representation.
- <mark style="background: #FFB86CA6;">Start with the same input as previous NeRF (cameras calibrated with Structure-from-Motion)</mark>
- Initialize the set of 3D Gaussians with the sparse point cloud produced for free as part of the SfM process. ref.[[Structure From Motion]]
	- [p] most point-based solutions that require Multi-View Stereo data, but we achieve high-quality results with only sfM points as input.
- <mark style="background: #FFB86CA6;">Optimization of the properties of the 3D Gaussians</mark> - 3D positions, opacity 𝛼, anisotropic covariance, and spherical harmonic coefficients - interleaved with adaptive density control steps
- <mark style="background: #FFB86CA6;">A fast, differentiable rendering approach for the GPU</mark>, which is visibility-aware, allows anisotropic splatting and fast back propagation to achieve high-quality novel view synthesis.


## Related Works
### Traditional Scene Reconstruction and Rendering
- [b] The advent of Structure-from-Motion enabled an entire new domain where a collection of photos could be used to synthesize novel views.
	- SfM estimates a sparse point cloud during camera calibration, that was initially used for simple visualization of 3D space.
- [b] Subsequent multi-view stereo produced impressive full 3D reconstruction algorithm.
	- These methods *re-project* and *blend* the input images into the novel view camera, and use the geometry to guide this re-projection.

### Neural Rendering and Radiance Fields
- [b] Volumetric representations for novel-view synthesis were initiated by Soft3D; deep-learning techniques coupled with volumetric ray marching were proposed building on a continuous differentiable density field to represent geometry.
	- [c] <mark style="background: #FFB86CA6;">Rendering using volumetric ray-marching has significant cost due to the large number of samples required to query the volume.</mark>
- [b] Neural Radiance Fields introduced importance sampling and positional encoding to improve quality
	- [c] but used a large Multi-Layer Perceptron negatively affecting speed.
	- [c] <mark style="background: #FFB86CA6;">While the rendering quality is outstanding, training and rendering times remain extremely high</mark>.


### Point-Based Rendering and Radiance Fields
- [p] Point-based methods efficiently render disconnected and unstructured geometry samples.
- [b] *differentiable* point based-rendering techniques have been augmented with neural features and rendered using a CNN resulting in fast or even real-time view synthesis
	- [c] still depend on MVS for the initial geometry 


## Overview
- [b] A set of images of a static scene, with the corresponding cameras calibrated by <mark style="background: #ADCCFFA6;">SfM which produces a sparse point</mark> cloud as a side effect
- [b] <mark style="background: #ADCCFFA6;">Create a set of 3D Gaussians</mark> defined by as position, covariance matrix and opacity $\alpha$
- [b] <mark style="background: #ADCCFFA6;">The directional appearance component (color) of the radiance field is represented via spherical harmonics</mark> ref. [[Spherical Harmonics]]
	- [i] Our Algorithm proceeds to create the radiance field representation via a sequence of optimization steps of 3D Gaussian parameters - position, covariance, $\alpha$, and SH coefficients interleaved with operations for adaptive control of the Gaussian density.

![](https://i.imgur.com/KZxIzQe.png)
*overall 3d gaussian splatting pipeline*


## Differentiable 3D Gaussian Splatting
- [b] Our Goal is to optimize a scene representation that allows high-quality novel view synthesis, starting from a sparse set of points without normals.
	- To do this, need a primitive that inherits the properties of differentiable volumetric representations, while at the same time being unstructured and explicit to allow very fast rendering.
- [b] Our representation has similarities to previous methods that use 2D points and assume each point is a small planar circle with a normal
	- [c] Given the extreme sparsity of SfM points it is very hard to estimate normals (very noise normals from such an estimation)
- [u] <mark style="background: #ADCCFFA6;">We model the geometry as a set of 3D Gaussians that do not require normals.</mark>
	- <mark style="background: #ADCCFFA6;">Our Gaussians are defined by a full 3D covariance matrix $\sum$ define in world space centered at point mean $𝜇$</mark> 
		- Gaussian Term $G(x) = e^{-\frac{1}{2} x^T \Sigma^{-1} x}$    
	- <mark style="background: #ADCCFFA6;">An obvious approach would be to optimize the covariance matrix $\sum$ to obtain 3D Gaussians that represent the radiance field</mark>
	- The covariance matrix $\sum$ of 3D Gaussian is analogous to describing the configuration of an ellipsoid
		- Given a scaling matrix $S$ , rotation matrix $R$ 
		- $\Sigma = R S S^T R^T$
		- 3D vector $s$ for scaling, quaternion $q$ to represent rotation
		

## Optimization with Adaptive Density Density Control of 3D Gaussians
- [b] optimization step, which creates a dense set of 3D Gaussians accurately representing the scene for free-view synthesis
	- position 𝑝, 𝛼, and covariance $\sum$, SH coefficients representing color 𝑐 of each Gaussians to capture the view-dependent appearance of the scene.

### Optimization
- [b] The optimization is based on successive iterations of rendering and comparing the resulting image to the training views
- [b] Use Stochastic Gradient Descent techniques for optimization
- [b] Use Sigmoid activation function, exponential activate function
- [b] Loss function is L1 combined with D-SSIM term
	- $\mathcal{L} = (1 - \lambda) \mathcal{L}_1 + \lambda \mathcal{L}_{D-SSIM}$ ref.[[Dissimilarity Structural Similarity Index]]

### Adaptive Control of Gaussians
1. Start with the initial set of sparse points from SfM
2. <mark style="background: #ADCCFFA6;">Apply our method to adaptively control the number of Gaussians and their density over unit volume</mark>
	- Allowing us to go from an initial sparse set of Gaussians to a denser set that better represents the scene, and with correct parameters.
- [b] Adaptive control of the Gaussians needs to populate empty areas
	- [u] focus on regions with missing geometric features (Under-Reconstruction)
	- [u] in regions where Gaussians over large areas in the scene (Over-Reconstruction)
	- tries to move the Gaussians to correct.

![](https://i.imgur.com/ZX3PIFc.png)
*adaptive control of the Gaussian pipeline*


## Fast Differentiable Rasterizer for Gaussians
- [b] Our goals are to have fast overall rendering and fast sorting to allow approximate $\alpha$-blending - including for anisotropic splats - and to avoid hard limits on the number of splats that can receive gradients
	- To do this, design a tile based rasterizer for Gaussian splats (software rasterization approaches) to pre-sort primitives
	- avoid the expense of sorting per pixel that hindered previous $\alpha$-blending solutions
<mark style="background: #BBFABBA6;">Culling Gaussians</mark>
- [u] Proceeds to cull 3D Gaussian against the view frustum and each tile.

<mark style="background: #BBFABBA6;">Screen Space Gaussians</mark>
- [u] Reject Gaussians at extreme positions (those with means close to the near plane and far outside) 
	- in game engine camera view: near plane & far plane

<mark style="background: #BBFABBA6;">Tiles</mark>
- [u] Splitting by splatting the screen into 16x16 tiles

<mark style="background: #BBFABBA6;">Duplicate with Keys</mark>
- [u] All are 64-bit
	- front of 32bit is View-space Depth of Gaussians
	- back of 32bit is Tile ID
	
<mark style="background: #BBFABBA6;">After Sorting Gaussian</mark>
- [u] Produce a list for each tile by identifying the first and last depth-sorted entry that splats to a given tile.
<mark style="background: #BBFABBA6;">Rasterization</mark>
- [u] Each block first loads packets of Gaussians into shared memory and then, for a given pixel, accumulates color and $\alpha$values by traversing the lists front-to-back, thus maximizing the gain in parallelism both for data loading/sharing and processing.
<mark style="background: #BBFABBA6;">During Rasterization</mark>
- [u] The saturation of $\alpha$is the only stopping criterion
- [u] No limit the number of blended primitives that receive gradient updates.