# Competitive Intelligence Classifier for Import Data

A machine learning system that deciphers ambiguous import data to reveal competitor products, automating a 14-day manual analysis workflow down to 5 minutes.

---

## 🎥 Live Demonstration

A full demonstration of the Streamlit application is available below. Watch to see how a user can upload a raw, ambiguous data file and receive categorized, actionable intelligence in minutes.

[![Watch the video](https://img.youtube.com/vi/RhID7f1pNOQ/maxresdefault.jpg)](https://youtu.be/RhID7f1pNOQ)

---

## 🏆 Key Results & Impact

* **⏱️ Drastic Efficiency Gain:** Reduced the time required for competitive analysis from **over 2 weeks to just 5 minutes**.
* **🎯 High Accuracy:** The machine learning system achieves **95% precision**, matching the performance of a human domain expert.
* **💼 Significant Business Value:** Saved the company over **80 hours of skilled labor per month**, enabling the BI team to focus on strategic analysis instead of manual data processing.

---

## Motivation

The company's Business Intelligence (BI) team needed to analyze a massive database of all products imported by competitors in the agricultural sector. However, this was a significant challenge:

1.  **The Business Problem:** The manual analysis was so slow (taking up to 14 days) that by the time the report was ready, the competitive insights were already outdated.
2.  **The Data Challenge:** The database contained no clear product names. It was filled with **ambiguous keywords, internal codes, and loosely associated terms**, making it nearly impossible to accurately classify products without a domain expert's painstaking manual review.

## Solution

I designed and built an end-to-end machine learning system that automates this entire intelligence-gathering process.

1.  **Data Processing & Cleaning:** I created robust Python scripts using the `fireducks` Pandas implementation to ingest and pre-process the raw, messy data, preparing it for the machine learning models.
2.  **Dual-Model ML System:** Recognizing the complexity, I developed two specialized classification models using the **AutoGluon** (AutoML) framework to decipher the ambiguous text:
    * **Model A:** An expert model trained to identify raw chemical ingredients.
    * **Model B:** An expert model trained to identify finished, branded goods.
3.  **Interactive Intelligence Platform:** I built a simple and intuitive user interface with **Streamlit**. This allows the BI team—regardless of technical skill—to upload an Excel file, run the analysis with a single click, and download the categorized competitive intelligence report. The system also intelligently flags low-confidence predictions for an optional human review.

## 🛠️ Tech Stack

* **Language:** Python
* **Machine Learning:** AutoGluon, Pandas (`fireducks`)
* **Web UI:** Streamlit
* **Core Tools:** Git & GitHub

---

## Data Schema

### Input (Excel)

The system expects an Excel file with a worksheet named **'TRADEMARK'**. The following columns are required:

* **`DataSourceName`**: The name of the data source.
* **`Dimension Value`**: The raw, ambiguous product description.
* **`Owner`**: The name of the company that owns the product.
* **`NCM`**: The Mercosur Common Nomenclature code for the product.
* **`Year`**: The year of the import record.
* **`Month`**: The month of the import record.

### Output (Excel)

The system generates several Excel files as output, separating high and low-confidence predictions for both trademark and ingredient models. The primary output files include:

* **`predictions_high_confidence_trademark.xlsx`** / **`predictions_high_confidence_ingredient.xlsx`**:
    * **`Predicted_Trademark`** / **`Predicted_Ingredient`**: The predicted product name.
    * **`Confidence`**: The model's confidence in the prediction (a float between 0 and 1).
    * **`Top_3_Predictions`**: The top three most likely product names.
    * **`Top_3_Probabilities`**: The probabilities associated with the top three predictions.
* **`predictions_for_review_trademark.xlsx`** / **`predictions_for_review_ingredient.xlsx`**: These files have the same structure as the high-confidence files but contain predictions with a confidence score below 0.90, which are flagged for human review.

---

## Metrics and Validation

* **Metric Definitions**:
    * **Precision**: A measure of the accuracy of the positive predictions, calculated as `TP / (TP + FP)`.
    * **Accuracy**: The proportion of true results among the total number of cases examined. This is the primary evaluation metric used during model training.
* **Reported Results**: The system achieves **95% precision**, which is comparable to the performance of a human domain expert.
* **Labeling**: The models are trained on data labeled by domain experts to ensure high-quality predictions.
* **Thresholding**: Predictions with a confidence score below **0.90** are automatically flagged for manual review.

---

## System Architecture

### Flow

The system follows this general workflow:

1.  **Ingest & Pre-process**: An Excel file is uploaded via the Streamlit UI. The `data_preprocess.py` script validates the columns, filters the data, and prepares it for the models.
2.  **Dual-Model Inference**: The pre-processed data is passed to two separate AutoGluon models:
    * **Model A (`autogluon_predictor_ingredient.py`)**: Predicts the raw chemical ingredients.
    * **Model B (`autogluon_predictor_trademark.py`)**: Predicts the finished, branded goods.
3.  **Threshold & Flag**: Each model's predictions are evaluated against a **0.90 confidence threshold**. Predictions below this threshold are separated for human review.
4.  **Export & UI**: The results are saved as separate Excel files, and a download link is provided in the Streamlit UI.

### Components

* **Training**: `database_processing/autogluon_model_trainer.py`
* **Inference**: `database_processing/autogluon_predictor_ingredient.py`, `database_processing/autogluon_predictor_trademark.py`
* **App**: `database_processing/streamlit.py`
* **Data Pre-processing**: `database_processing/data_preprocess.py`, `database_processing/convert_encoding.py`

---

## Human-in-the-Loop Review

* **Auto-flag Rules**:
    * Predictions with a confidence score of less than **0.90** are automatically flagged for review.
* **Reviewer Workflow**:
    1.  The system generates `predictions_for_review_ingredient.xlsx` and `predictions_for_review_trademark.xlsx` files.
    2.  A domain expert can review these files to correct any misclassifications.
    3.  The corrected data can then be used to retrain and improve the models.

---

## Limitations and Known Issues

* **Domain Drift**: New brands, products, or formulations not present in the training data may not be classified correctly. Periodic retraining with new data is recommended.
* **Ambiguous Text**: Highly ambiguous or abbreviated descriptions may be difficult for the models to classify with high confidence.

---
## ⚙️ Reproducibility


* **Conda Environment**: The project includes an `environment.yml` file. To create and activate the environment, clone the repository and run the following command in your terminal:
    ```bash
    conda env create -f environment.yml
    ```

* **Code & Data Separation**: The `.gitignore` file is configured to exclude data files (`*.csv`, `*.xlsx`), trained models (`AutogluonModels/`), and logs from the repository. This practice keeps the codebase clean, prevents large files from bloating the repository, and separates the logic from the data it processes.
---

## Citations and Attributions

* **AutoGluon**: [https://auto.gluon.ai](https://auto.gluon.ai)
* **Streamlit**: [https://streamlit.io](https://streamlit.io)
* **fireducks**: [https://github.com/dask-contrib/dask-fireducks](https://github.com/dask-contrib/dask-fireducks)
