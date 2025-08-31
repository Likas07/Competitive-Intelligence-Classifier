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

## The Business Problem & Data Challenge

To maintain a competitive edge, the company's Business Intelligence (BI) team needed to analyze a massive database of all products imported by competitors in the agricultural sector. However, this was a significant challenge:

1.  **The Business Problem:** The manual analysis was so slow (taking up to 14 days) that by the time the report was ready, the competitive insights were already outdated.
2.  **The Data Challenge:** The database contained no clear product names. It was filled with **ambiguous keywords, internal codes, and loosely associated terms**, making it nearly impossible to accurately classify products without a domain expert's painstaking manual review.

## My Solution

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
