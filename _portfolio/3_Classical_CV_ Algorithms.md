---
title: "Classical Computer Vision Algorithms"
excerpt: "Four vision systems implemented from first principles in NumPy and SciPy, plus a document-parsing pipeline."
collection: portfolio
---

Four classical computer vision systems, implemented in NumPy and SciPy rather
than with high-level vision libraries.

**Boundary detection.** Multi-scale derivative-of-Gaussian gradients fused
across scales, gated by a local-variance texture penalty so that busy, textured
regions are suppressed in favour of genuine structural edges. Improved on a
Sobel baseline.

**Illuminant estimation.** Estimates the light source color using
variance-weighted Minkowski pooling, with an exponential saturation penalty
that steers the estimate toward neutral, textured surfaces and away from
blown-out highlights. Improved on the gray-world method.

**Cell counting under focus blur.** Splits touching cells by carving the
distance transform with an edge product taken across multiple scales, and
falls back to a median-area estimate when blur has merged cells into a single
connected component. Improved on Otsu thresholding with connected components.

**Single-image super-resolution.** Reconstructs missing detail by searching the
image itself for self-similar patches at different scales, using them to infer
plausible high-resolution content rather than just interpolating between
existing pixels.

## Capstone: document rectification and binarization

An end-to-end pipeline for photographed documents. A spatial prior locates the
page in the frame, a homography corrects the perspective distortion from an
off-angle shot, and the flattened page is then binarized, with text and
photographic regions detected and routed through different treatments rather
than one threshold applied to both. Benchmarked against a deep learning
segmentation pipeline.
