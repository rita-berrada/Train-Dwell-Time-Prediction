# 🚆 Train Dwell Time Prediction

### 📍 Context & Motivation

India’s public transport system is vast, vital, and deeply flawed. From overcrowded stations to unpredictable delays, the railways suffer from poor infrastructure, inconsistent management, and a lack of real-time planning tools. Train delays are not just an inconvenience, they are part of daily life, often leading to missed connections, lost goods, and collective frustration.

In this context, improving the **prediction of dwell time** (the time a train spends at a station) becomes a powerful lever to enhance efficiency and reduce chaos. This project was initiated in collaboration with an Indian railway company aiming to **predict their trains dwell times more accurately using ML models**.

---

### 🎯 Objective

We focus on a particular set of trains and aim to model their **dwell time at the station "MINOT"**, which we define as the **last crue change point** for all trains in the dataset.

> 🔎 **Dwell Time** = `Departure Time at MINOT` – `Arrival Time at MINOT`

---

## 📚 Notebooks Overview

This project is structured in 4 main notebooks:

---

### `01_EDA_Dwell_Time_Data.ipynb`

We explore the raw dwell time dataset using a classic EDA workflow, with techniques commonly used in data science:

- **Distribution plots** of dwell times
- **Categorical feature exploration**
- **Missing value handling**
- **Initial insights** into station and time-based patterns
- **Basic cleaning** and formatting

---

### `02_Outlier_Detection_and_Removal.ipynb`

Outlier detection is essential to avoid skewed predictions. Here's how we tackled it:

- **First attempt**: IQR-based filtering  
  → ❌ Ineffective due to **strongly skewed distribution** of dwell times.

- **Second attempt**: Custom binning strategy  
  ✔️ More robust and domain-specific.

**Steps followed:**

1. **Train/test split**: based on `arrival_date`.  
   - Training = all trains with arrival **before Jan 1, 2024**

2. **Binning dwell time**:
   - Each train was assigned a bin according to its dwell time.
   - We **kept only bins** containing **at least 5%** of total trains.
   - We found **lower and upper bounds** 

3. **Outlier flagging**:
   - An `IS_OUTLIER` flag was added to the entire dataset.

---

_(next: I'll add feature creation + event preprocessing when you’re ready)_


