# Angle and scene audit

## Field dependence

The fixed layout renders the same body field at every azimuth, while the
rotated and ACDM fields change with aspect.

| Quantity | Fixed | Rotated | ACDM |
|---|---:|---:|---:|
| NCC to design view | 1.000 at every azimuth | minimum 0.183 | minimum 0.269 |
| Consecutive-view MSE | 0 | follows rigid motion | follows learned deformation |

## Geometric check on ASC point sets

For 1,119 view pairs drawn from all ten classes, the full ASC point set of a
reference view was rotated by the azimuth difference and compared with the
target view by symmetric Chamfer distance (ASC pixels). The fraction of pairs
improved by rotation, and the mean distance before/after rotation, are:

| Separation | Pairs | Fixed | Rotated | Improved |
|---|---:|---:|---:|---:|
| 3°–10° | 289 | 1.68 | 1.63 | 67.1% |
| 10°–20° | 304 | 1.81 | 1.69 | 74.0% |
| 20°–30° | 151 | 1.96 | 1.67 | 80.1% |
| 30°–45° | 227 | 2.32 | 1.78 | 77.1% |
| 45°–60° | 148 | 2.83 | 2.17 | 74.3% |

Rotation is therefore a data-supported geometric prior for the visible-center
set, but not a complete model of the view change; this is why the ACDM adds the
low-order Fourier deformation.

## Scene variation

Across within-class view pairs, the measured scene also changes with aspect.

| Separation | Body IoU | Shadow IoU | Background NCC |
|---|---:|---:|---:|
| 10°–20° | 0.42 | 0.12 | 0.08 |
| 20°–30° | 0.33 | 0.12 | 0.07 |
| 30°–45° | 0.27 | 0.12 | 0.06 |
| 45°–60° | 0.21 | 0.11 | 0.05 |

A fixed background and shadow suppress real scene variation. The full-chip
simulation therefore retrieves the background, shadow, and body support of the
nearest measured view for the requested azimuth.
