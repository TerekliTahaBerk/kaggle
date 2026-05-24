# Pit Stop Blend Inputs

Structured dataset for final submission blending.

## Layout

```text
blend_dataset/
├── public/
│   ├── super/          # strongest 0.95449 / 0.95437 / 0.95435 anchor files
│   ├── rank_diverse/   # rank-like submissions used through rank remapping
│   ├── top_external/   # previous 0.95409 candidates
│   ├── core/           # stable public-core files used before b10
│   ├── diverse/        # 0.95381 diverse signal
│   └── support/        # smaller public support candidates
├── ours/
│   ├── main/           # our base/two-seed submissions
│   └── variants/       # our CatBoost variant submissions
└── notes/
    ├── manifest.csv
    └── README.md
```

Every CSV must contain exactly:

```csv
id,PitNextLap
```

All files are validated to have the same row count and id order.

## Current Super Group

```text
public/super/
├── 0.95449.csv
├── 0.95437.csv
├── 0.95435.csv
├── 0.95431_a.csv
├── 0.95431_b.csv
├── 0.95419.csv
├── 0.95418.csv
├── 0.95411_a.csv
└── 0.95411_b.csv
```

`0.95449.csv` is the main anchor for the current blender. `0.95437.csv` and `0.95435.csv` are close high-scoring support signals, while the `0.95431` files provide a more diverse high-scoring support profile. `0.95419.csv`, `0.95418.csv`, and `0.95411` are kept as older support signals for diagnostics and controlled blends.

The `public/rank_diverse/0.95446.csv` file has a rank-like distribution with mean close to `0.50`, so it should not be used as a normal probability source. The blender uses it through rank-remapping methods only.
