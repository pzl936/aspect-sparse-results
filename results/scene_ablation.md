# Scene ablation

The ACDM is evaluated with the angle-matched measured scene and with a fixed
design-view scene. Values are held-out accuracy (%) on ResNet-18 /
EfficientNet-B0 / ViT-B/16.

| Scene | R18 | EffB0 | ViT | Mean |
|---|---:|---:|---:|---:|
| Angle-matched measured scene | 91.2 | 88.4 | 98.0 | 92.5 |
| Fixed design-view scene | 92.4 | 90.4 | 89.6 | 90.8 |

The fixed scene is slightly better on ResNet-18 and EfficientNet-B0 but
collapses on ViT and on class M60 (24/64/12 versus 92/92/100). A body-only
simulation on a frozen background is therefore not a neutral approximation: it
changes the decision and its cross-network stability. Background and shadow
must follow the query angle for consistent cross-network behavior.
