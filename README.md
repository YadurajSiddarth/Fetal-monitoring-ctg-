# Improving Anomaly Detection in Fetal Monitoring Using Cardiotocography (CTG) Data: A Comparative Study of Original and Enhanced Detection Techniques


[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YadurajSiddarth/Fetal-monitoring-ctg/blob/main/Fetus_Monitoring_(CTG).ipynb)

This project applies anomaly detection to fetal monitoring data from Cardiotocography (CTG). It is developed for the **Data Mining and Predictive Analytics** coursework.

The project analyses CTG measurements to identify unusual fetal-monitoring records and compares an original anomaly-detection method with an improved approach.

## Files

| File | Description |
|---|---|
| `Fetus_Monitoring_(CTG).ipynb` | Google Colab / Jupyter Notebook containing preprocessing, anomaly detection, evaluation and visualisations |
| `uci_ctg_dataset.csv` | CTG dataset used in the experiment |
| `README.md` | Project documentation |

## Dataset
* **Source:** UCI Machine Learning Repository (Cardiotocography Dataset - ID 193)
* **Size:** 2,126 recordings, 21 physiological features
* **Target:** Binary Classification (Normal vs. Anomaly)

Cardiotocography records fetal heart rate and uterine contraction measurements. The data can be used to classify fetal health conditions and investigate potentially anomalous CTG records.

**Dataset file:** `uci_ctg_dataset.csv`

## Project Objective

The objective is to evaluate an existing anomaly-detection approach for fetal monitoring and propose an improvement.

The workflow is:

1. Load and inspect the CTG dataset.
2. Clean and preprocess the data.
3. Select relevant CTG features.
4. Implement the original anomaly-detection technique.
5. Implement an improved anomaly-detection technique.
6. Compare both approaches using evaluation metrics.
7. Visualise and discuss the results.


## Anomaly Detection Approaches

### Baseline Model: Salini et al. (2024)
* **Algorithm:** Random Forest Classifier (with balanced class weights)
* **Feature Selection:** Pearson Correlation-Based Selection
* **Preprocessing:** Z-Score Normalization + 77/23 Stratified Split

### Proposed Improvement: XGBoost + SMOTE
* **Limitation Addressed:** Standard parallel tree ensembles (Random Forest) struggle with the extreme class imbalance of medical data, leading to a high False Negative Rate.
* **Algorithm:** Extreme Gradient Boosting (XGBoost) for sequential error correction.
* **Data Balancing:** Synthetic Minority Over-sampling Technique (SMOTE) applied exclusively to the training set to synthesize anomaly data points and perfectly balance the feature space.

## Evaluation Metrics

The models are evaluated using appropriate metrics, including:

- Precision
- Recall
- F1-score
- Accuracy, where appropriate
- False positives
- False negatives
- Number of anomalies detected
- Computational time
- ROC-AUC or PR-AUC, where applicable

## Results

| Metric | Original Approach (RF) | Improved Approach (XGBoost + SMOTE) |
|---|---:|---:|
| Precision | 0.9091 | 0.8981 |
| Recall | 0.8411 | 0.9065 |
| F1-score | 0.8738 | 0.9023 |
| False Positives | 9 | 11 |
| False Negatives | 17 | 10 |
| Number of Anomalies Detected | 99 | 108 |
| Computational Time | 0.4985 seconds | 0.7593 seconds |

## Tools Used

- Python
- Google Colab
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Seaborn

## Limitations and Ethics

This project is for academic analysis only. It must not be used as a clinical diagnostic system. Any real-world fetal-monitoring system requires medical validation, expert oversight, patient-data protection and compliance with healthcare privacy requirements.

## Authors

Yaduraj Siddarth

