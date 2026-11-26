# Synthetic Dataset: Disaster Resilience Planning

**Domain:** Government & Public Services (Philippines Context)  
**Target Audience:** Resilience Planners, Infrastructure Risk Analysts, and Data Science Learners  
**Author:** Akkhileus Viktor Zara Vargas

## Overview
This repository contains a mathematically rigorous, synthetic dataset generator and analytical environment focused on disaster resilience. It models infrastructure service disruption and recovery times following severe weather events (typhoons and floods) in the Philippines.

The data generation process utilizes standard civil engineering approaches (e.g., Logistic Fragility Curves) to estimate damage probabilities based on environmental stress, while simulating real-world operational bottlenecks in recovery.

## Realism Injections & Hidden Challenges
This dataset is specifically designed for intermediate-to-advanced data learners. It contains intentional "messiness" to simulate real-world municipal data:
1. **The Omitted Variable ("Hidden Decay"):** True maintenance deficit heavily influences both damage probability and repair times, but the variable is *dropped* before final export. Learners must discover this bias through exploratory data analysis (EDA) when they realize official vulnerability scores don't perfectly predict failure.
2. **Reporting Artifacts:** Repair times are mathematically rounded to simulate tired field crews logging hours in 12-hour or 24-hour shifts.
3. **Missingness:** Missing records in LGU registries are simulated for `year_built` and `official_vulnerability_score`.
4. **Queueing Bottlenecks:** Recovery times are modeled with a heavy right-tail (Lognormal distribution) and dynamic delay times representing crew shortages.

## File Structure

```text
📁 DisasterResilience_Dataset/
 ├── 📄 1_Data_Generator.ipynb             # Python script that generates the data
 ├── 📄 2_EDA_and_Analysis.ipynb           # Sample analytical notebook and target insights
 ├── 📄 Synthetic_Dataset_Specification_Disaster_Resilience.docx # Mathematical formulas and literature citations
 ├── 📄 README.md                          # Project documentation
 └── 📁 data/                              # The generated CSV files
      ├── Assets.csv
      ├── HazardEvents.csv
      ├── DamageReports.csv
      └── ServiceRestoration.csv
```

## Quick Start
1. **To Generate Fresh Data:** Open `1_Data_Generator.ipynb` and click `Restart & Run All`. This will build the base tables, apply the math, drop the latent variables, and export new CSVs to the `data/` folder.
2. **To Analyze the Data:** Open `2_EDA_and_Analysis.ipynb` to see baseline descriptive statistics, visualize reporting artifacts, and attempt the "detective work" stretch goal.
3. **To Review the Math:** Open the Word document to view the $\beta$ coefficients, hazard normalization logic, and APA-formatted literature references justifying the model design.

## Analytical Use Cases for Learners
Learners can use this dataset to practice:
* **Predictive Modeling:** Train a classification model (e.g., Random Forest, XGBoost) to predict `is_service_disrupted` or `damage_state` based on hazard intensity and asset features.
* **Survival Analysis / Queueing Theory:** Analyze `time_to_restore_hours` to predict how long a specific municipality will be without critical services.
* **Causal Inference & Bias Detection:** Prove that `official_vulnerability_score` is an incomplete metric by analyzing unexplained variance in severe damage reports.