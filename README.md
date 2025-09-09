# Breast Cancer Classification  

## Abstract  
This project investigates the application of supervised machine learning techniques for the classification of breast cancer tumors using the **Wisconsin Diagnostic Breast Cancer (WDBC)** dataset. The primary objective is **prediction**: to build models that distinguish malignant from benign cases based on cytological features extracted from fine-needle aspirates (FNA). The analysis compares models of varying complexity and interpretability, with an emphasis on minimizing false negatives to support clinical decision-making.  

---

## Introduction  
Early and accurate detection of breast cancer is critical to improving patient outcomes. Machine learning methods provide an opportunity to complement diagnostic practices by identifying tumor characteristics that are strongly associated with malignancy. This project evaluates three classifiers — Logistic Regression, Random Forest, and Support Vector Machine (SVM) — and identifies the most suitable model for predictive reliability and clinical relevance.  

---

## Dataset  
- **Source:** Wisconsin Diagnostic Breast Cancer (WDBC) dataset  
- **Records:** 569 patient samples  
- **Attributes:** 30 numerical features describing size, shape, and texture of nuclei  
- **Target variable:** Diagnosis (`M` = malignant, `B` = benign)  
- **Characteristics:**  
  - No missing values  
  - Moderately imbalanced distribution (37% malignant, 63% benign)  
  - Features standardized using z-scores  

---

## Methodology  
1. **Data Exploration**  
   - Distribution analysis revealed right-skewed features with significant outliers.  
   - Outliers were retained as they may represent clinically important cases.  
   - Features were standardized to improve comparability.  

2. **Model Training**  
   - **Logistic Regression**: Baseline linear model with interpretable coefficients.  
   - **Random Forest**: Ensemble of decision trees capable of capturing nonlinear interactions.  
   - **Support Vector Machine (RBF kernel)**: Nonlinear classifier suitable for complex boundaries.  
   - All models trained using stratified cross-validation to preserve class proportions.
   - All models were subjected to hyperparameters tuning process.

3. **Evaluation Metrics**  
   - Accuracy  
   - Precision, Recall, and F1-score (per class)  
   - Area Under the ROC Curve (AUC)  

---

## Results  
| Metric                | Logistic Regression | Random Forest | SVM     |  
|------------------------|---------------------|---------------|---------|  
| Overall Accuracy       | 0.9708              | **0.9766**    | 0.9708  |  
| Precision (Benign)     | 0.9636              | 0.9640        | 0.9636  |  
| Recall (Benign)        | 0.9907              | **1.0000**    | 0.9907  |  
| F1-Score (Benign)      | 0.9770              | **0.9817**    | 0.9770  |  
| Precision (Malignant)  | 0.9836              | **1.0000**    | **1.0000** |  
| Recall (Malignant)     | 0.9375              | 0.9375        | 0.9375  |  
| F1-Score (Malignant)   | 0.9600              | **0.9677**    | 0.9600  |  
| AUC                    | **0.9975**          | 0.9955        | 0.9955  |  

- All models achieved accuracy above 97%.  
- Random Forest achieved **perfect precision for malignant tumors** and **perfect recall for benign tumors**, making it the most balanced model.  
- Logistic Regression achieved the highest AUC, indicating strong threshold-independent discrimination, though with slightly lower malignant precision.  

---

## Conclusion  
Random Forest was selected as the final model, as it provided the best trade-off between sensitivity and specificity while maintaining strong overall accuracy. This model minimizes both false positives and false negatives, aligning with clinical priorities. Logistic Regression, while slightly superior in AUC, did not match Random Forest’s balanced performance across class-specific metrics.  

---

## Limitations and Future Work  
- The dataset is relatively small and drawn from a single institution, which may limit generalizability.  
- Additional clinical or demographic features could further enhance predictive performance.  
- External validation on independent datasets is required.  
- Future work may include exploring calibrated probabilities, cost-sensitive learning, and advanced ensemble methods (e.g., Gradient Boosting, XGBoost).  

---
Author: Himmler Benitez

License: MIT
