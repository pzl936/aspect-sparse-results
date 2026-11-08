# Static class-shared prototype

One trihedral layout is shared by all training chips of a class and rendered
unchanged at every held-out view. Values are held-out accuracy (%) for
ResNet-18 / EfficientNet-B0 / ViT-B/16.

## Per-class accuracy

| Class | K=10 | K=20 |
|---|---|---|
| 2S1 | 32 / 100 / 96 | 100 / 100 / 100 |
| BMP2 | 96 / 80 / 100 | 100 / 80 / 100 |
| BTR70 | 88 / 100 / 44 | 92 / 100 / 48 |
| M1 | 0 / 100 / 56 | 80 / 92 / 100 |
| M2 | 24 / 48 / 100 | 88 / 40 / 100 |
| M35 | 100 / 100 / 100 | 100 / 100 / 100 |
| M548 | 44 / 100 / 100 | 56 / 92 / 100 |
| M60 | 40 / 76 / 92 | 88 / 88 / 100 |
| T72 | 56 / 76 / 96 | 100 / 96 / 96 |
| ZSU23-4 | 100 / 100 / 100 | 100 / 100 / 100 |

## View and budget ablation

| K | Training views | ResNet-18 | EfficientNet-B0 | ViT-B/16 | Mean |
|---:|---:|---:|---:|---:|---:|
| 20 | 5 | 81.2 | 84.8 | 95.6 | 87.2 |
| 20 | 10 | 88.4 | 84.8 | 92.8 | 88.7 |
| 20 | 20 | 90.4 | 88.8 | 94.4 | 91.2 |
| 20 | 30 | 86.4 | 85.6 | 93.2 | 88.4 |
| 10 | 30 | 62.8 | 83.6 | 90.8 | 79.1 |

At K = 20 the mean held-out accuracy is 90.4 / 88.8 / 94.4. The result is
class-dependent: most classes are above 80% on at least two networks, while
BTR70, M2, and M548 are difficult. At K = 10, ResNet-18 falls to a mean of
58.0% and several classes are near chance. K = 20 is the smallest broadly usable
budget in this study. Once the azimuth span is covered, adding views gives less
than adding points: 20 views with K = 20 reach 91.2%, whereas K = 10 with 30
views reaches 79.1%.
