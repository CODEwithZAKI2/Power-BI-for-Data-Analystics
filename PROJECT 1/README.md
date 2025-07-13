# 🏥 US Hospital Performance Analysis Dashboard
![US Hospital Performance Analysis Dashboard](../images/dashboard-preview.png)
## 📁 Dataset

- **Source:** [Medicare Hospital General Information](https://www.kaggle.com/datasets/cms/hospital-general-information)
- **File:** [`dataset/HospInfo.csv`](dataset/HospInfo.csv)
- **Power BI File:** `Hospital General Information.pbix`

---

## 🚀 Project Overview

This project analyzes US hospital performance using Power BI, focusing on overall ratings and key quality metrics. The dashboard provides actionable insights for healthcare stakeholders, showcasing advanced data cleaning, transformation, and visualization skills.

---

## 🛠️ Workflow Summary

1. **Dataset Selection:**  
   Chose the official Medicare Hospital General Information dataset for its relevance and richness.

2. **Data Cleaning (Power Query):**
   - Removed unnecessary footnote columns.
   - Standardized categorical columns (ownership, EHR status).
   - Converted IDs, ZIP codes, and phone numbers to text for data integrity.
   - Replaced "Not Available" in ratings with nulls for proper numeric analysis.
   - Created a new `Ownership Category` column for simplified analysis.
   - Formatted names and locations for readability.

3. **Analysis & Visualization (Power BI):**
   - Answered five challenging business questions using DAX measures and interactive visuals.
   - Extracted key insights and visualized them with appropriate chart types.

---

## ❓ Business Questions & Insights

### 1️⃣ **Which states have the highest and lowest average hospital overall ratings?**
- **Approach:**  
  DAX:  
  ```dax
  Average Rating = AVERAGE('HospInfo'[Hospital overall rating])
  ```
  Table visual with State and Average Rating.
- **Visualization:**  
  - Bar charts for Top 5 and Bottom 5 States.
  - **Titles:**  
    - Top 5 States by Average Hospital Overall Rating  
    - Bottom 5 States by Average Hospital Overall Rating
- **Insight:**  
  Significant variation exists; SD, DE, WI, MN, and ID lead, while NV, NY, PR, VI, and DC lag.

---

### 2️⃣ **How does average hospital rating differ by ownership category?**
- **Approach:**  
  Created `Ownership Category` in Power Query:
  ```powerquery
  if Text.Contains([Hospital Ownership], "Government") then "Government"
  else if Text.Contains([Hospital Ownership], "Volunteer non-profit") then "Voluntary non-profit"
  else [Hospital Ownership]
  ```
  DAX:  
  ```dax
  Average Rating = AVERAGE('HospInfo'[Hospital overall rating])
  ```
- **Visualization:**  
  Column chart  
  **Title:** Average Hospital Overall Rating by Ownership Category
- **Insight:**  
  Physician-owned hospitals have the highest ratings; tribal and proprietary hospitals rate lowest.

---

### 3️⃣ **Is there a difference in average rating by EHR meaningful use status?**
- **Approach:**  
  DAX for status grouping:
  ```dax
  EHRs Status = 
  SWITCH(
      TRUE(),
      ISBLANK('HospInfo'[Meets criteria for meaningful use of EHRs]), "Unknown",
      'HospInfo'[Meets criteria for meaningful use of EHRs] = TRUE(), "True",
      'HospInfo'[Meets criteria for meaningful use of EHRs] = FALSE(), "False"
  )
  ```
- **Visualization:**  
  Pie chart  
  **Title:** Average Hospital Overall Rating by EHR Meaningful Use Status
- **Insight:**  
  Hospitals with unknown EHR status have slightly higher average ratings than those marked as True.

---

### 4️⃣ **How do hospital types compare in terms of average rating?**
- **Approach:**  
  Table visual with Hospital Type and Average Rating.
- **Visualization:**  
  Column chart  
  **Title:** Average Hospital Overall Rating by Hospital Type
- **Insight:**  
  Critical Access Hospitals outperform Acute Care Hospitals; Children’s Hospitals lack rating data.

---

### 5️⃣ **Is there a relationship between hospital rating and mortality national comparison?**
- **Approach:**  
  Table visual with Mortality National Comparison and Average Rating.
- **Visualization:**  
  Column chart  
  **Title:** Average Hospital Overall Rating by Mortality National Comparison
- **Insight:**  
  Hospitals above the national average for mortality have higher ratings; those below have the lowest.

---

## 📊 Dashboard Preview

![US Hospital Performance Analysis Dashboard](../images/dashboard-preview.png)

---

## 🧮 Key DAX Measures

```dax
Average Rating = AVERAGE('HospInfo'[Hospital overall rating])

EHRs Status = 
SWITCH(
    TRUE(),
    ISBLANK('HospInfo'[Meets criteria for meaningful use of EHRs]), "Unknown",
    'HospInfo'[Meets criteria for meaningful use of EHRs] = TRUE(), "True",
    'HospInfo'[Meets criteria for meaningful use of EHRs] = FALSE(), "False"
)
```

---

## 🔄 Power Query Transformations

- Removed columns: `*footnote`
- Split and formatted address fields.
- Standardized categorical columns.
- Created `Ownership Category` for simplified analysis.

---

## 🏆 Portfolio Value

This project demonstrates:
- Advanced Power Query data cleaning.
- DAX measure creation and logic.
- Insightful healthcare analytics.
- Professional dashboard design and storytelling.

---

## 📬 Contact

For questions or collaboration, connect via [LinkedIn](https://www.linkedin.com/codewithzaki) or email.
