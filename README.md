# Automated Product Classification with an Interactive UI

This project uses Python, AutoML, and Streamlit to create a complete solution for automating product classification. It transforms a tedious, 2-week manual data entry task into a 5-minute, interactive process.



---

## 🏆 Key Results & Impact

* **⏱️ Drastic Efficiency Gain:** Reduced the time required for product classification from **over 2 weeks to just 5 minutes**.
* **🎯 High Accuracy:** The machine learning system achieves **95% precision**, matching the performance of a human expert.
* **💼 Significant Business Value:** Saved the company over **80 hours of skilled labor per month**, freeing employees to focus on high-value analysis instead of manual data entry.

---

## The Challenge

An agricultural company was manually classifying thousands of imported products each month from a large, unstructured database. The process was not only incredibly time-consuming but also prone to human error. They needed an automated system to accurately distinguish between two key import types:
1.  **Raw Active Ingredients** for local formulation.
2.  **Finished, Formulated Products** ready for sale.

## My Solution

I designed and built an end-to-end machine learning system with a user-friendly web interface to solve this problem.

1.  **Data Processing & Cleaning:** I created robust Python scripts using the fireducks **Pandas** implementation to ingest, clean, and pre-process the raw database dumps, making the data suitable for modeling.
2.  **Dual-Model ML System:** Recognizing the complexity, I developed two specialized classification models using the **AutoGluon** (AutoML) framework:
    * **Model A (Ingredients):** An expert model trained to identify raw chemical components.
    * **Model B (Products):** An expert model trained to identify finished, branded goods.
3.  **Interactive Web Application:** I built a simple and intuitive user interface with **Streamlit**. This allows any team member—regardless of technical skill—to upload an Excel file, run the models with a single click, and download the categorized results. The system also intelligently separates predictions by confidence level, flagging low-confidence entries for a quick human review.

## 🛠️ Tech Stack

* **Language:** Python
* **Machine Learning:** AutoGluon, Scikit-learn, Pandas
* **Web UI:** Streamlit
* **Core Tools:** Jupyter Notebook, Git & GitHub

https://github.com/user-attachments/assets/7a9d6149-a27f-4c6e-b983-163cad08e07c
