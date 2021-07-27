![](assets/images/teaser.png)

## Abstract

Recent learning approaches that implicitly represent surface geometry using coordinate-based neural representations have shown impressive results in the problem of multi-view 3D reconstruction. The effectiveness of these techniques is, however, subject to the availability of a large number (several tens) of input views of the scene, and computationally demanding optimizations. In this paper, we tackle these limitations for the specific problem of few-shot full 3D head reconstruction, by endowing coordinate-based representations with a probabilistic shape prior that enables faster convergence and better generalization when using few input images (down to three). First, we learn a shape model of 3D heads from thousands of incomplete raw scans using implicit representations. At test time, we jointly overfit two coordinate-based neural networks to the scene, one modeling the geometry and another estimating the surface radiance, using implicit differentiable rendering. We devise a two-stage optimization strategy in which the learned prior is used to initialize and constrain the geometry during an initial optimization phase. Then, the prior is unfrozen and fine-tuned to the scene. By doing this, we achieve high-fidelity head reconstructions, including hair and shoulders, and with a high level of detail that consistently outperforms both state-of-the-art 3D Morphable Models methods in the few-shot scenario, and non-parametric methods when large sets of views are available.

### Method

H3D-Net is a neural architecture that reconstructs high-quality 3D human heads from a few input images (down to 3) with associated masks and camera poses. At training time, a DeepSDF-like model is trained to capture the distribution of human heads from raw 3D data. Then, this model is connected with a coordinate-based rendering network, similarly to IDR, that estimates the emited radiance for each 3D surface point, enabling direct supervision in the image domain. During the 3D reconstruction process, the prior model keeps the 3D models within the space of plausible solutions and it is eventually unfrozen to capture finer details.

![](assets/images/method.png)

### Results

3D Head Reconstruction results with only 3 input images. In this examples, camera poses are regressed with and the masks are annotated estimated with U2Net and manually refined.

### Releted work

* [DeepSDF: Learning Continuous Signed Distance Functions for Shape Representation (2019)](https://arxiv.org/abs/1901.05103)
* [Implicit Geometric Regularization for Learning Shapes (2020)](https://arxiv.org/abs/2002.10099)
* [Multiview Neural Surface Reconstruction with Implicit Lighting and Material (2020)](https://arxiv.org/abs/2003.09852)

### BibTEX

```
@article{ramon2021h3dnet
  author    = {Ramon, Eduard and Triginer, Gil and Escur, Janna and Pumarola, Albert and Garcia, Jaime and Giro-i-Nieto, Xavier and Moreno-Noguer, Francesc},
  title     = {H3D-Net: Few-Shot High-Fidelity 3D Head Reconstruction},
  journal   = {arXiv preprint arXiv:3856181},
  year      = {2021},
}
```

