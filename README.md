# Nonlinear to Linear Separability

Transformation of non-linearly separable patterns or samples into linearly separable patterns.

This notebook accompanies the author's Scopus-indexed paper "Transforming Non-Linearly Separable Data".

## What the notebook does

All data is synthetic and generated in the notebook with NumPy and scikit-learn; no external dataset is needed.

1. **Two moons.** Generates 300 samples with `make_moons` (noise 0.2), standardizes them and makes a 70/30 train/test split. Kernel PCA with a polynomial kernel (degree 3, `coef0=1`, 2 components) is fitted to the training data, and a linear SVM is trained on the transformed features. The notebook plots the decision boundary and a confusion matrix. Saved output: accuracy 0.93.
2. **Mixed linear and non-linear features.** Builds synthetic two-class datasets (200 samples per class) that combine a linearly separable feature with non-linear features derived from it (sine, cosine, polynomial and exponential terms, plus noise). The features are standardized and split 70/30, and plotted in 2D and 3D.
3. **Kernel PCA on the non-linear features only.** The linear feature(s) are kept as they are, Kernel PCA (polynomial kernel, degree 3) is applied to the non-linear feature(s), the results are concatenated and a linear SVM is trained on them. Two variants are included, with decision-boundary and confusion-matrix plots. Saved outputs: accuracy 0.92 (two linear features plus one KPCA component) and 0.93 (one linear feature plus two KPCA components).
4. **RBF SVM baseline.** For comparison, an SVM with an RBF kernel is trained directly on the standardized features, without the Kernel PCA step. Saved output: accuracy 0.92.

Accuracy figures are the values printed in the notebook's saved outputs, on the 30% test split.

## Files

- `nonlinear_to_linear_separability.ipynb`: the notebook with the code, plots and saved outputs.
- `presentation.pptx`: slides presenting the work.

## How to run

```bash
pip install numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook nonlinear_to_linear_separability.ipynb
```

Run the cells from top to bottom; later cells reuse variables defined by earlier ones.
