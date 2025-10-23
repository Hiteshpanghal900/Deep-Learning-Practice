# Ancient Text Classification

This repository documents my solution for the NPPE-1 Kaggle competition, a challenge focused on computational history. The goal was to build a robust deep learning model capable of classifying ancient, anonymized inscription texts by their geographical origin based solely on subtle linguistic, dialectal, and stylistic patterns embedded within the text.

## 🎯 The Challenge & Goal
| Feature | Description |
| :--- | :--- |
| **Objective** | Predict the correct anonymized geographical **`label`** for each inscription in the test set. |
| **Data** | A large collection of cleaned, anonymized inscription texts (`train.csv` and `test.csv`). |
| **Evaluation** | **Macro F1 Score** (A robust metric for multi-class classification, critical for potentially imbalanced historical data). |
| **Constraint** | Solution must be entirely reproducible within a self-contained environment (Kaggle Notebook). |

## 🛠️ Solution Approach: Fine-Tuning DistilBERT with Class Weighting
The core of the solution lies in fine-tuning a powerful, efficient Transformer model, DistilBERT, and implementing a critical technique to handle the expected class imbalance common in historical datasets.

**1. Data Processing and Tokenization**
* **Model:** The pre-trained distilbert-base-uncased model was selected for its balance of performance and efficiency.

* **Tokenization:** The corresponding DistilBERT tokenizer was used to preprocess the ancient inscription texts, converting them into the numerical input format required by the model.

**2. Model Fine-Tuning and Imbalance Mitigation**
* **Base Model:** A standard DistilBertForSequenceClassification model was loaded and fine-tuned for the multi-class classification task.

* **Class Imbalance Handling:** To optimize the Macro F1 Score (which penalizes poor performance on minority classes), weight balancing was introduced:

* **Application:** These weights were applied during the model training process to penalize errors on under-represented geographical regions more heavily, forcing the model to pay equal attention to all classes.

* **Training Strategy:** Implemented stratified cross-validation and tuned hyperparameters (learning rate, epochs) to ensure robust generalization.

**3. Prediction & Submission**
* The fine-tuned DistilBERT model was used to generate predictions for the test.csv texts.

* Predictions were mapped back to the numerical label format for submission.