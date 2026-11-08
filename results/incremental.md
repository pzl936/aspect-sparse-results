# Incremental calibration and ablations

Protocol: offline 10°–36° (20 views), four new views at 60°–66°, held-out test
of 10 old-range views and 12 new-range views at 70°–80°. Accuracy is the mean
over the ten classes for each judge; cost is counted in view-steps.

## Method comparison

| Method | R18 old | R18 new | EffB0 old | EffB0 new | ViT old | ViT new | Cost |
|---|---:|---:|---:|---:|---:|---:|---:|
| One sample, fixed | 78.0 | 66.7 | 88.0 | 81.7 | 96.0 | 91.4 | 0 |
| One sample, rotated | 85.0 | 78.6 | 85.0 | 88.3 | 97.0 | 87.5 | 0 |
| ACDM offline | 95.0 | 81.9 | 87.0 | 87.5 | 98.0 | 89.7 | 2000 |
| Incremental, new only | 91.0 | 90.8 | 88.0 | 89.7 | 95.0 | 91.7 | 240 |
| Incremental, replay only | 93.0 | 88.3 | 86.0 | 88.1 | 95.0 | 93.1 | 480 |
| Incremental, replay + anchor | 93.0 | 89.2 | 84.0 | 89.2 | 94.0 | 91.9 | 480 |
| Full retrain, old + new | 92.0 | 81.4 | 82.0 | 89.2 | 98.0 | 91.1 | 2400 |

Judge means: offline 93.3 old / 86.4 new; replay + anchor 90.3 old / 90.1 new;
full retrain 90.7 old / 87.2 new. The four-view update closes most of the
new-band gap at 480 view-steps, whereas the full retrain spends 2,400 and is
lower on the new band.

## Anchor weight

Four new views, replay = 4.

| λ | Old | New |
|---:|---:|---:|
| 0 | 91.3 | 89.8 |
| 0.001 | 92.0 | 90.4 |
| 0.003 | 90.0 | 89.8 |
| 0.01 | 90.3 | 90.1 |
| 0.1 | 91.7 | 90.0 |

## Replay buffer

λ = 0.01, four new views.

| Replay size | Old | New |
|---:|---:|---:|
| 0 | 93.0 | 88.8 |
| 2 | 90.3 | 89.4 |
| 4 | 90.3 | 90.1 |
| 8 | 92.0 | 90.3 |

## Number of new views

λ = 0.01, replay = 4.

| New views | Old | New |
|---:|---:|---:|
| 1 | 92.0 | 89.4 |
| 2 | 91.7 | 90.0 |
| 3 | 91.3 | 90.5 |
| 4 | 90.3 | 90.1 |
| 6 | 90.3 | 90.5 |
| 8 | 92.0 | 92.0 |

One new view already gives 89.4% on the new band and 92.0% on the old band;
three to eight views move the new-band mean between 90.1% and 92.0% without a
monotone trend, so the first view carries most of the information and the rest
stabilizes the estimate.
