# 🛡️ Membership Inference Attack (MIA)

This project, as a part of the Trustworthy Machine Learning Course in SoSe'25 aims to extract information from a protected target model by progressively improving a membership inference attack pipeline. This was built on top of the [`yonsei-sslab/MIA`](https://github.com/yonsei-sslab/MIA) framework for efficient experimentation.

**🔍 Final Results:**
- **TPR@FPR=0.05**: `0.144`
- **AUC**: `0.655`

---

## 🔁 Approach Overview

### 🧪 Initial Setup
- Trained 5 shadow models.
- Attack model initially used only the confidence score (max softmax value).
- Then extended to the full 44-dimensional softmax output from the target model, leading to modest improvement.

### 🛠️ Feature Engineering
- Replaced confidence-only input with richer features:
  - Full softmax probability vector
  - Entropy
  - Margin
  - Loss
  - True label
- These enhancements significantly boosted performance.

### 📈 Scaling Up
- Increased shadow models from 5 → 20 → 30.
- Adopted variable training set sizes (300 to 3000 per model) to simulate more diverse behaviors.
- Combined outputs from both shadow and target models, leading to best results.

### 🧩 Data Splitting
- Disjoint train/eval/test splits per shadow model.
- Eval/test sizes fixed at 500/1000 samples respectively.
- Varied training size to capture learning behavior under different data regimes.

### 🔬 Additional Experiments
- Data augmentation didn’t improve performance.
- Future work may include class-specific attack models for better granularity in high-class-count settings (44 classes here).

---

