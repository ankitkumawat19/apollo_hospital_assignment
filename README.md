# apollo_hospital_assignment
Exploratory Data Analysis (EDA) in Python on 75,000+ Apollo Hospitals records to identify appointment no-show drivers, quantify revenue loss, evaluate reminder efficacy, and optimize doctor utilization across 15 cities.
# 🏥 Apollo Hospitals - Appointment No-Show and Patient Engagement Analysis

An end-to-end Exploratory Data Analysis (EDA) project in Python exploring booking behavior, patient retention, doctor utilization, and financial losses caused by appointment no-shows across 15 cities in India.

This project was created as part of my practical application and learning in **Healthcare Data Analytics** and **Business Analytics**.

---

## 📌 Project Overview

Apollo Hospitals operates across 15 cities in India through a mix of in-clinic consultations, video consults, and home visits across multiple booking channels (Apollo App, Website, Call Centre, Walk-in, and Partner Apps). 

A significant share of booked appointments results in **no-shows**, which directly impacts doctor utilization, operational revenue, and patient health outcomes. 

As a Data Analyst at Apollo Hospitals, the objective of this project is to perform comprehensive Exploratory Data Analysis (EDA) in Python across **75,000 appointment records** and **320 doctors** from **2022 to 2024** to uncover actionable patterns across:
- Overall booking behavior and outcome breakdowns
- Specialty-wise and geographic no-show risk factors
- Reminder and patient engagement effectiveness
- Demographic segmentation and chronic disease impacts
- Financial leakage and lost revenue estimation
- Doctor utilization and consultation service quality

The project is implemented in **Jupyter Notebook (`.ipynb`)** format with clean, production-grade analytical code.

---

## ✨ Features & Analysis Modules

- **Business Volume & Trend Tracking:** Monthly and quarterly volume tracking across 2022–2024.
- **Outcome Classification:** Detailed distribution across `Completed`, `No-Show`, `Cancelled`, and `Scheduled`.
- **Channel Mix Optimization:** High-volume booking channels vs. channels with severe dropouts.
- **Lead-Time Impact Analysis:** Quantitative assessment of lead time on cancellation and no-show probabilities.
- **Reminder Channel Efficacy:** Direct comparison of SMS, WhatsApp, and Call reminders against unreminded bookings.
- **Membership & Repeat Cohort Analysis:** Behavior patterns of Apollo Members vs. non-members and first-time vs. repeat patients.
- **Financial Leakage Modeling:** Calculation of realized revenue vs. revenue lost to no-shows and cancellations.
- **Service Quality & Doctor Utilization:** Waiting times, consult duration vs. patient satisfaction, and doctor experience-fee relationships.

---

## 📊 Analytical Rules & Domain Logic

The analysis strictly adheres to critical business and healthcare metrics guidelines:

1. **No-Show Rate Calculation:**
   $$\text{No-Show Rate} = \frac{\text{No-Show Count}}{\text{Completed} + \text{No-Show} + \text{Cancelled}}$$
   *(Appointments marked as `Scheduled` are strictly excluded from the denominator as their visit outcome is still pending).*

2. **Quality & Operational Metrics:**
   - Metrics such as `wait_time`, `patient_satisfaction`, `consultation_duration`, and `doctor_utilisation` are populated **only for `Completed` visits**.
   - These analyses are strictly filtered on `appointment_status == 'Completed'`.

3. **Revenue Realization:**
   - Non-completed rows carry zero realized revenue.
   - All realized revenue, city-level collections, and out-of-pocket analyses are scoped strictly to completed appointments, while no-show rows are used to calculate opportunity losses.

4. **Categorical Handling:**
   - The value `'None'` in fields like `chronic_condition`, `membership_type`, `insurance_provider`, and `cancellation_reason` represents a valid non-applicable status rather than missing data.

---

## 📂 Dataset Information

The analysis leverages two relational files linked by `doctor_id`:

| Dataset File | Dimensions | Granularity | Key Attributes |
| :--- | :--- | :--- | :--- |
| **`apollo_appointments_fact.csv`** | 75,000 rows × 52 columns | 1 row per appointment | Booking channel, appointment status, dates, lead time, reminder types, patient demographics, wait times, fees, insurance coverage |
| **`apollo_doctors_dim.csv`** | 320 rows × 15 columns | 1 row per doctor | `doctor_id`, doctor experience, department/specialty, consultation charges, doctor ratings |

---

## 💻 Python Concepts & Libraries Used

This project applies core data science and analytical techniques in Python:

- **Data Manipulation & Cleaning:** `pandas` and `numpy` (relational merges, categorical standardizations, conditional aggregations).
- **Date-Time Processing:** Parsing timestamps, calculating booking lead windows, monthly/quarterly period resampling.
- **Statistical Aggregations:** GroupBy operations, weighted averages, multi-variable pivot tables.
- **Data Visualization:** `matplotlib` and `seaborn` (time series, stacked bar charts, box plots, correlation heatmaps).
- **Business Logic Modeling:** Custom Python functions for no-show rates, lost revenue calculations, and cohort grouping.

---

## 🔍 Key Business Questions Answered

### 1. Business Overview
- How is appointment volume trending across months and quarters from 2022 to 2024?
- What is the split of outcomes across completed, no-show, cancelled, and scheduled appointments?
- Which booking channels drive the highest volume and how does the channel mix look?

### 2. No-Show Analysis
- Which specialties and cities have the highest and lowest no-show rates?
- How does booking lead time affect the probability of a no-show?
- Do evening slots, weekends, and longer-lead bookings see higher dropout?
- Which appointment types (in-clinic, video, home visit) and booking channels carry the most no-show risk?

### 3. Reminder & Engagement Effectiveness
- How much does reminder type reduce no-show rates compared to unreminded patients?
- Does prior no-show history predict future no-show behavior?
- Do Apollo members and repeat patients show better attendance than non-members and first-time patients?

### 4. Patient & Demographic Segmentation
- How do age group, gender, and chronic condition status influence no-show likelihood?
- Which visit reasons are most common and are some associated with higher dropout?
- What does the patient age distribution look like within specialties like Paediatrics, Gynaecology, and Psychiatry?

### 5. Financial Performance
- How much revenue is being lost to no-shows?
- How does average revenue vary across specialties and appointment types?
- Which cities generate the most revenue and what is the payment mode mix?
- How does insurance coverage affect what patients pay out of pocket?

### 6. Doctor Utilisation & Service Quality
- Which specialties have the highest and lowest doctor utilisation rates?
- How long are patients waiting and does it vary by specialty or time of day?
- Is there a relationship between consultation duration and patient satisfaction?
- How does doctor experience relate to the fee charged?

---

## 📸 Output Preview

### Monthly Appointment Volume Trend
![Appointment Volume Trend](appointment_volume_trend.png)

### No-Show Rate by Lead Time & Reminder Type
![No Show Analysis](no_show_analysis.png)

### Financial Loss & Specialty Revenue Breakdown
![Revenue Analysis](revenue_analysis.png)

---

## 🚀 How to Run

### Prerequisites
Make sure Python 3.8+ and Jupyter are installed on your computer.

### Step 1: Clone the Repository
```bash
git clone [https://github.com/](https://github.com/)<your-username>/apollo-hospitals-no-show-analysis.git
cd apollo-hospitals-no-show-analysis
