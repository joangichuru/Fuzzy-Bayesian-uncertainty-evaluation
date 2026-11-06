# Local clean-execution verification — 6 November 2026

The packaged notebook was executed end-to-end using `nbclient` in the package directory without Python errors (26 notebook cells). The output audit notebook was not distributed.

- Dataset: 4,020 observations; Late Blight 1,954; Early Blight 2,066.
- Stratified 5-fold hybrid: accuracy 0.925124; pooled AUC 0.977653; Brier 0.060438; log-loss 0.212817; ECE 0.069021.
- Paired model comparison after tie audit: 60 BN-only errors corrected; nine new errors; net 51.
- Grouped historical folds: 788, 767, 830, 781, 854 observations; identical environmental configurations kept within a single fold.
- Grouped 5-fold mean accuracy: fuzzy-only 0.943710, BN-only 0.912012, hybrid 0.931457.
- Grouped 5-fold hybrid: mean AUC 0.980016; mean log-loss 0.208060; mean Brier 0.058887.

The historical grouped-fold assignments are retained **solely to reproduce the manuscript's original analysis**. Newer scikit-learn versions select different folds due to a resolved shuffle bug. The README and grouped validation note explain this distinction. 