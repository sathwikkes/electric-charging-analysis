# EV Charging Station Analysis and Uptime Prediction

## Overview
This project explores and predicts the uptime of electric vehicle (EV) charging stations using machine learning models. With the rise in EV adoption, ensuring reliable charging infrastructure is critical for both customer satisfaction and operational efficiency. This analysis provides insights into the patterns of uptime, explores key factors influencing it, and builds predictive models to estimate future uptime.

The project contains two key Jupyter Notebook files:
- **`first-run.ipynb`**: Initial testing ground for running machine learning models with a broader set of features. Results from this exploratory attempt were used to refine the workflow.
- **`ev-analysis.ipynb`**: Comprehensive analysis, including exploratory data analysis (EDA), feature engineering, and final predictive models for station uptime.

---

## Dataset
The dataset used in this project contains information about electric charging stations, including:
- **Station Information**: ID, name, type, category, and access type.
- **Uptime Data**: Hourly uptime status for each station over multiple days.
- **Temporal Information**: Date, day of the week, and time-related trends.

### Key Features
1. **Hourly Data**:
   - `hour0`, `hour1`, ..., `hour23`: Uptime status for each hour of the day.
2. **Categorical Data**:
   - `Station_Type`, `Station_Category`, `Station_Access`
3. **Temporal Data**:
   - `Ping_Date`, `DayOfWeek`
4. **Target Variable**:
   - `Daily_Average_Uptime`: Average uptime for a station across all hours in a day.

---

## Why Is This Analysis Helpful?
1. **Operational Efficiency**: 
   - Proactively predict downtime to optimize maintenance schedules.
   - Allocate resources effectively based on station performance.
   
2. **Customer Satisfaction**:
   - Ensure consistent uptime for better user experiences at EV stations.

3. **Infrastructure Planning**:
   - Identify underperforming stations and optimize locations for new stations.

---

## Key Concepts and Techniques Used

### 1. **Preprocessing**
   - Dropped rows with missing values to ensure data quality.
   - Encoded categorical variables using one-hot encoding and label encoding.
   - Scaled numerical features (e.g., uptime statistics) using Min-Max Scaling for better model performance.

### 2. **Feature Engineering**
   - **Daily Average Uptime**: Mean uptime across all 24 hours of a day.
   - **Peak Hour**: Hour of the day with the highest uptime.
   - **Hourly Variability**: Standard deviation of uptime for each station.
   - **Lag Features**: Added `Lag_1`, `Lag_2`, and `Lag_3` (previous days' uptimes) to capture temporal dependencies.
   - **Rolling Averages**: Computed 3-day and 7-day rolling averages to capture trends.

### 3. **Exploratory Data Analysis (EDA)**
   - Visualized hourly and daily uptime patterns.
   - Examined how uptime varies across station categories, access types, and days of the week.
   - Used correlation analysis to identify features with strong relationships to uptime.

### 4. **Machine Learning Models**
   - **Initial Models (`first-run.ipynb`)**:
     - Tested Random Forest, XGBoost, LightGBM, CatBoost, and SVR using a broader set of features.
     - Results highlighted the need for refined feature selection and engineering.
   - **Final Models (`ev-analysis.ipynb`)**:
     - Focused on predicting uptime for a specific station.
     - Incorporated lag features and rolling averages.
     - Evaluated model performance using RMSE.

### 5. **Hyperparameter Tuning**
   - Conducted grid search to optimize Random Forest hyperparameters:
     - `n_estimators`, `max_depth`, `min_samples_split`, and `min_samples_leaf`.
   - Adjusted learning rates and tree depths for XGBoost, LightGBM, and CatBoost.

---

## Results
1. **Exploratory Insights**:
   - Station uptime shows clear temporal trends, with certain hours and days exhibiting higher uptime.
   - Stations categorized as "Public Access" tend to have higher uptime compared to "Private Access".

2. **Model Performance**:
   - The best-performing model achieved an RMSE of `X.XX` (adjust this after results).
   - XGBoost and LightGBM demonstrated strong performance, particularly after tuning.

3. **Next Day Uptime Predictions**:
   - Final predictions were constrained to valid ranges (0 to 1) to reflect realistic uptime values.

---


---

## Next Steps
1. **Expand Data Sources**:
   - Incorporate additional variables like traffic data, weather conditions, or maintenance logs.
2. **Deploy Predictive Models**:
   - Build a dashboard for real-time uptime predictions using Flask or FastAPI.
3. **Refine Models**:
   - Experiment with deep learning models like LSTMs for better temporal predictions.

---

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/username/ev-uptime-prediction.git
   cd ev-uptime-prediction