# 🚆 Train Dwell Time Prediction

### 📍 Context & Motivation

India’s public transport system is vast, vital, and… deeply flawed. From overcrowded stations to unpredictable delays, the railways suffer from poor infrastructure, inconsistent management, and a lack of real-time planning tools. Train delays are not just an inconvenience — they are part of daily life, often leading to missed connections, lost goods, and collective frustration.

In this context, improving the **prediction of dwell time** (the time a train spends at a station) becomes a powerful lever to enhance efficiency and reduce chaos. This project was initiated in collaboration with an Indian railway company aiming to **predict train dwell times more accurately using AI models**.

---

### 🎯 Objective

We focus on a particular set of trains and aim to model their **dwell time at the station "MINOT"**, which we define as the **last true change point** for all trains in the dataset.

> 🔎 **Dwell Time** = `Departure Time at MINOT – `Arrival Time at MINOT`

---

## 📚 Notebooks Overview

This project is structured in 4 main notebooks:

---

### `01_EDA_Dwell_Time_Data.ipynb`

We explore the raw dwell time dataset using a classic EDA workflow:

- **Distribution plots**
- **Categorical feature exploration**
- **Missing value handling**
- **Basic cleaning** and formatting

---

### `02_Outlier_Detection_and_Removal.ipynb`

Outlier detection is essential to avoid skewed predictions.

- **First attempt**: IQR-based filtering → ❌ Ineffective due to skewed distribution.
- **Second attempt**: Custom binning strategy → ✔️ More robust.

**Steps:**
1. **Train/test split** based on arrival date (training = before Jan 1, 2024)
2. **Binning dwell times** and keeping only bins with ≥ 5% of trains
3. Computing **lower/upper bounds** and adding `IS_OUTLIER` flag

---

### `03_Preprocessing_Supplementary_Tables.ipynb`

Preparation of the **Events** (planned movements) and **Schedule** (actual movements) tables:

1. Cleaned both datasets
2. Found common `TRAIN_ID`s and arrival times
3. Merged into one dataset
4. Extracted relevant structured columns
5. Produced a feature-ready table

---

### `04_Feature_Engineering_and_Correlation.ipynb`

In this notebook we:
- Created **14 features**
- Plotted **distribution graphs** for each
- Studied **feature correlation**
- Performed a **linear regression** as a first modeling attempt

---

## 👩‍💻 Author

**Rita Berrada El Azizi**  
Data Scientist & Global Engineering Student  
_Infosys InStep 2025 — Indian Railways ML Project_

---

## 📄 License

This project is under the MIT License. See `LICENSE` for details.



