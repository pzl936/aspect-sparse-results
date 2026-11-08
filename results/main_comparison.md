# Main comparison

Main split: train on 20 views at 10°–44°, test on 25 disjoint views at
45°–84°. Accuracy is held-out true-class accuracy (%), and the mean is over the
ten classes for each judge. The final column is the mean over the three judges.

| Method | ResNet-18 | EfficientNet-B0 | ViT-B/16 | Mean |
|---|---:|---:|---:|---:|
| ACDM (one-sample init + offline calibration) | 91.2 | 88.4 | 98.0 | **92.5** |
| Static class-shared prototype | 90.4 | 88.8 | 94.4 | 91.2 |
| One-sample rigid rotation (no offline calibration) | 75.6 | 80.4 | 89.6 | 81.9 |
| View-specific top-20 amplitude sparse reference | 94.4 | 94.0 | 97.6 | 95.3 |

## Interpretation

- Offline calibration is essential: a one-sample rigid rotation reaches 81.9%
  in the judge mean, whereas the calibrated ACDM reaches 92.5%.
- The view-specific top-20 sparse reference is 95.3%. It requires a measured
  sample and its own 20 strongest centers at every view, so it is a reference,
  not a deployable layout. The ACDM is 2.8 points below it in the judge mean;
  this is the cost of one aspect-conditioned layout.
- The gain over the static class-shared prototype is a reallocation rather than
  a uniform increase. Classes whose discriminative returns migrate with aspect,
  such as BTR70 and M548, improve on at least one judge, while some easy-class
  margins decrease.

## Deformation order

| Deformation order | ResNet-18 | EfficientNet-B0 | ViT-B/16 |
|---|---:|---:|---:|
| M = 0 (rigid rotation) | 92 | 89 | 98 |
| M = 1 (first-order Fourier) | 91 | 88 | 98 |
| M = 2 | 93 | 89 | 99 |

On the main split the three orders are within the per-class intervals. The
first-order model is selected on the extrapolation protocol, where it gives a
mean new-range accuracy of 86.4% versus 85.0% for M = 0 and 84.8% for M = 2.
