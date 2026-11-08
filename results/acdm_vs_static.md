# ACDM versus static prototype

Per-class held-out accuracy (%), K = 20, 25 views per class and judge. Mean
rows average the ten classes for each judge; the judge-averaged means are 92.5%
for the ACDM and 91.2% for the static prototype.

| Class | ACDM R18 | ACDM EffB0 | ACDM ViT | Static R18 | Static EffB0 | Static ViT |
|---|---:|---:|---:|---:|---:|---:|
| 2S1 | 100 | 100 | 96 | 100 | 100 | 100 |
| BMP2 | 92 | 92 | 96 | 100 | 80 | 100 |
| BTR70 | 96 | 100 | 88 | 92 | 100 | 48 |
| M1 | 72 | 100 | 100 | 80 | 92 | 100 |
| M2 | 96 | 20 | 100 | 88 | 40 | 100 |
| M35 | 80 | 100 | 100 | 100 | 100 | 100 |
| M548 | 92 | 92 | 100 | 56 | 92 | 100 |
| M60 | 92 | 92 | 100 | 88 | 88 | 100 |
| T72 | 92 | 88 | 100 | 100 | 96 | 96 |
| ZSU23-4 | 100 | 100 | 100 | 100 | 100 | 100 |
| **Mean** | **91.2** | **88.4** | **98.0** | **90.4** | **88.8** | **94.4** |

The ACDM changes the error profile rather than uniformly raising accuracy. It
recovers BTR70 on ViT (88% versus 48%) and M548 on ResNet-18 (92% versus 56%),
while M2 on EfficientNet-B0 falls from 40% to 20% and M35 on ResNet-18 from 100%
to 80%. The static layout behaves as a class texture that happens to work on the
easy classes; once the model is required to change with azimuth, part of the
easy-class margin is spent on classes whose discriminative returns migrate.
