# 🚆 Train Dwell Time Prediction

## 📍 Context & Motivation
India’s public transport system is vast, vital, and… deeply flawed. From overcrowded stations to unpredictable delays, the railways suffer from poor infrastructure, inconsistent management, and a lack of real-time planning tools. Train delays are not just an inconvenience — they are part of daily life, often leading to missed connections, lost goods, and collective frustration.

In this context, improving the **prediction of dwell time** (the time a train spends at a station) becomes a powerful lever to enhance efficiency and reduce chaos. This project was initiated in collaboration with an Indian railway company aiming to **predict train dwell times more accurately using AI models**.

---

## 🎯 Objective
We focus on a particular set of trains and aim to model their **dwell time at the station "MINOT"**, which we define as the **last true change point** for all trains in the dataset.

> 🔎 **Dwell Time** = `Departure Time at MINOT` – `Arrival Time at MINOT`

---

## 📚 Notebooks Overview

This project is structured in 4 main notebooks:

---

### `01_EDA_Dwell_Time_Data.ipynb`
We explore the raw dwell time dataset using a classic EDA workflow:
- Distribution plots
- Categorical feature exploration
- Missing value handling
- Basic cleaning and formatting

---

### `02_Outlier_Detection_and_Removal.ipynb`
Outlier detection is essential to avoid skewed predictions.

- **First attempt**: IQR-based filtering → ❌ Ineffective due to skewed distribution.  
- **Second attempt**: Custom binning strategy → ✔️ More robust.

**Steps:**
1. Train/test split based on arrival date (training = before Jan 1, 2024)  
2. Binning dwell times and keeping only bins with ≥ 5% of trains  
3. Computing lower/upper bounds and adding `IS_OUTLIER` flag

---

### `03_Preprocessing_Supplementary_Tables.ipynb`
Preparation of the **Events** (planned movements) and **Schedule** (actual movements) tables:
- Cleaned both datasets
- Found common `TRAIN_ID`s and arrival times
- Merged into one dataset
- Extracted relevant structured columns
- Produced a feature-ready table

---

### `04_Feature_Engineering_and_Correlation.ipynb`
In this notebook we:
- Created **14 features**
- Plotted distribution graphs for each
- Studied feature correlation
- Performed a linear regression as a first modeling attempt

---

## 📊 Feature-by-Feature Insights (with Figures)

**Inspection Requirement**  
![Inspection Requirement](figs/Inspection_Requirement.png)  
Dwell time is higher when inspection is required.

**Is Holiday**  
![Is Holiday](figs/IS_HOLIDAY.png)  
Dwell time is lower on holidays.

**Train Priority**  
![Train Priority](figs/Train_Priority.png)  
Dwell time varies with priority; H and M behave similarly.

**Train Type**  
![Train Type](figs/Train_Type.png)

**Mainline**  
![Mainline Trains](figs/MainlineTrains.png)  
No significant variation.

**Day of Week**  
![Day of Week](figs/Day_of_Week.png)  
Increase from mid-week to weekend — lowest Wednesday, highest Saturday.

**Day Type**  
![Day Type](figs/Day_Type.png)  
No significant variation.

**Month**  
![Month](figs/Month.png)  
Higher in June, February, December; lower in May and September.

**Hour of Day**  
![Hour of Day](figs/Hour_of_Day.png)  
Peak at 1 pm.

**All Trains**  
![All Trains](figs/AllTrains.png)  
Some variation as the number increases.

**Yard Trains**  
![Yard Trains](figs/YardTrains.png)

**Mainline Trains**  
![Mainline Trains](figs/MainlineTrains.png)  
More mainline trains → higher dwell time.

**Priority Trains**  
![Priority Trains](figs/PriorityTrains.png)

**Priority Yard**  
![Priority Yard](figs/PriorityYard.png)

**Priority Mainline**  
![Priority Mainline](figs/PriorityMainline.png)

---

## 👩‍💻 Author
**Rita Berrada El Azizi**  
Data Scientist & Global Engineering Student  
_Infosys InStep 2025 — Indian Railways ML Project_

---

## 📄 License
This project is under the MIT License. See `LICENSE` for details.
