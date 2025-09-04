Analysis Questions — Answers & Observations

Explained Variance:

The explained variance per principal component declines as you take more components. The cumulative explained variance plot shows how many components are needed for a threshold (e.g., in our run, n_95 printed above shows how many PCA components explain 95% of variance). For Wine (13 features), typically 6–8 components suffice to reach ~95% depending on dataset split.

PCA vs LDA:

PCA finds directions of maximum variance without regard to labels , good for compression and visualization.

LDA finds directions that maximize class separability (using class labels) and often yields better preprocessing for classification (higher accuracy with fewer components) because it focuses on discriminative information rather than overall variance.

KPCA γ parameter:

Small γ (e.g., 0.01): kernel becomes broad (close to linear), the kernel matrix entries are high (points look similar) and KPCA may fail to separate non-linear structures.

Very large γ (e.g., 100): kernel becomes very localized; only near-identical points have significant kernel values → noisy eigenvectors; overfitting-like behavior; small clusters in transformed space.

There is a sweet spot (dataset-dependent) that yields good separation (e.g., γ between 5 and 30 in our half-moons example).

Classifier performance & timing:

Typically LDA (2 components) gives competitive or better accuracy than PCA(2) when used for classification because it optimizes class separability.

Using reduced dimensions (2) reduces training time for many classifiers, but the original (standardized) dataset may give slightly higher accuracy if many informative components are ignored. Check the printed times/accuracies for your run.

Limitations:

PCA fails when the principal directions of variance are not informative for the target labels or when data is nonlinear (e.g., concentric circles).


KPCA uses kernels to implicitly map data into a higher-dimensional space where linear separation may be possible; it addresses nonlinearity by using kernel functions (RBF, polynomial, etc.) to compute similarities and perform PCA in feature space.
