# Per-chip oracle

Each view is allowed to fit its own selected centers; the arm is an oracle upper
bound for the shared-layout results, not a deployable protocol. Cells are
accuracy (%) / number of chips. R18, EffB0, and ViT denote ResNet-18,
EfficientNet-B0, and ViT-B/16.

## Azimuth bins

| Azimuth | K=10 R18 | K=10 EffB0 | K=10 ViT | K=20 R18 | K=20 EffB0 | K=20 ViT |
|---|---:|---:|---:|---:|---:|---:|
| 10°–19° | 87/38 | 97/38 | 100/38 | 100/38 | 100/38 | 100/38 |
| 20°–29° | 94/35 | 94/35 | 100/35 | 100/35 | 97/35 | 100/35 |
| 30°–39° | 100/38 | 100/38 | 100/38 | 100/38 | 100/38 | 100/38 |
| 40°–49° | 100/25 | 100/25 | 100/25 | 100/25 | 100/25 | 100/25 |
| 50°–59° | 97/29 | 100/29 | 100/29 | 100/29 | 100/29 | 100/29 |
| 60°–69° | 100/24 | 92/24 | 92/24 | 100/24 | 100/24 | 100/24 |
| 70°–79° | 95/21 | 95/21 | 100/21 | 100/21 | 100/21 | 100/21 |

## Elevation bins

| Elevation | K=10 R18 | K=10 EffB0 | K=10 ViT | K=20 R18 | K=20 EffB0 | K=20 ViT |
|---|---:|---:|---:|---:|---:|---:|
| 14° | 100/10 | 90/10 | 100/10 | 100/10 | 100/10 | 100/10 |
| 15° | 100/36 | 100/36 | 100/36 | 100/36 | 100/36 | 100/36 |
| 16° | 95/85 | 99/85 | 99/85 | 100/85 | 100/85 | 100/85 |
| 17° | 94/79 | 95/79 | 99/79 | 100/79 | 99/79 | 100/79 |

At K = 20 the azimuth curve is flat at 97%–100% in every bin for all three
judges, and the elevation rows are near-perfect; the 14° bin contains only 10
chips. The representation itself is therefore not the view-limited component in
the tested range.
