
## Research Question

How do classifiers built on hand-crafted audio features (MFCCs, spectral features, etc.) compare with pretrained deep audio models for music genre classification, specifically rock, folk, pop, and electronic, in terms of accuracy, per-genre errors, robustness, and interpretability?

## Data Source

A subset of **The Free Music Archive (FMA)** dataset, containing only rock, folk, pop, and electronic songs (Defferrard et al., 2017; [FMA GitHub Repository](https://github.com/mdeff/fma)).

## Planned Methods

First, build a feature-engineering baseline, extracting audio features and summarizing each over time (mean and variance), and fitting logistic regression, random forest, and gradient-boosted models. Permutation importance and SHAP will show which features drive predictions.

We will then fine-tune a pretrained audio model from Hugging Face (e.g., the Audio Spectrogram Transformer) and compare it with the feature-based classifiers.

All models will be trained and tested using the dataset's provided train/validation/test split and evaluated using:

- **Accuracy**
- **Macro-F1**
- **Robustness checks:** Shorter clips or added noise

We will discuss which approach performs best, where each fails, and what the interpretable features reveal about how genres differ.
