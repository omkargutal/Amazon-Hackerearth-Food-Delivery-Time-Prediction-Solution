# Food Delivery Time Prediction — Amazon Business Research

## Project Summary
This project focuses on predicting the total time taken for food delivery using a variety of factors including delivery person details, weather conditions, traffic density, and geographical distance. The objective is to provide a reliable predictive model that helps optimize delivery operations and manage stakeholder expectations.

A **Stacking Regressor** (utilizing XGBoost, LightGBM, and CatBoost) was implemented to achieve high predictive accuracy, capturing complex non-linear relationships between environmental factors and travel time.

---

## Dataset Information
The dataset used in this project is sourced from the **Amazon Business Research Analyst** challenge (Predict time taken by delivery person - Hackerearth hiring challenges).

*   **Source:** [Kaggle Dataset - Amazon Business Research Analyst](https://www.kaggle.com/datasets/syednusrath/amazon-business-research-analyst/data)
*   **Data Format:** The raw data consisted of over **45,000 individual text files** for training and **11,000+ text files** for testing.

---

## Data Creation & Processing
### Unstructured Data Extraction
One of the primary challenges of this project was the initial data format. Unlike standard CSV datasets, the raw data was provided in thousands of separate `.txt` files. 

**How we created the structured dataset:**
1.  **Iterative Ingestion:** We implemented a Python-based extraction engine using `glob` and `tqdm` to walk through the directory structures.
2.  **Parsing Logic:** Each file was read line-by-line. We developed custom string parsing rules to identify relevant fields (e.g., `Delivery_person_Age`, `Weather conditions`, etc.) and their associated values.
3.  **DataFrame Construction:** The extracted key-value pairs were aggregated into a centralized Pandas DataFrame, converting a massive collection of unstructured text into a clean, queryable format for machine learning.

---

## Feature Engineering & Cleaning
To squeeze the best performance out of the models, we engineered several high-impact features:
*   **Haversine Distance:** Calculated the direct geographical distance between the restaurant and the delivery location using latitude/longitude.
*   **Preparation Time (`prep_time`):** Derived the duration taken for the order to be picked up after it was ordered, capturing restaurant-side delays.
*   **Temporal Splits:** Extracted `day_of_week`, `hour`, and `month` to capture peak traffic and order volume variations.
*   **Robust Cleaning:** Handled missing values using median imputation for numeric fields and mode for categorical fields, ensuring zero data loss during prediction.

---

## Summary & Recommendations
### Key Findings
1.  **Traffic Density:** Categorized as 'High' or 'Jam', traffic remains the single largest bottleneck for delivery efficiency.
2.  **Preparation Efficiency:** A significant portion of 'Delivery Time' is actually spent waiting at the restaurant.

### Recommendations for Deployment
*   **Incentivize Prep-Efficiency:** Restaurants with low `prep_time` should be prioritized or featured.
*   **Dynamic Radius:** During 'High' traffic periods, adjust the visible delivery radius to customers to minimize extreme delays.
*   **Vehicle Optimization:** Encourage the usage of scooters in high-density urban areas as they show better resilience to 'Jam' traffic conditions compared to motorcycles.

---

## How to Run
1.  Install dependencies: `pip install pandas numpy scikit-learn xgboost lightgbm catboost matplotlib seaborn tqdm`
2.  Run the `Delivery_Time_Prediction.ipynb` notebook to extract data and train the model.
3.  The trained model will be saved as `delivery_model.pkl` for use in the production environment.

---

## Author
Developed with ❤️ by [**Omkar Gutal**](https://www.linkedin.com/in/omkar-gutal-a25935249/) 🔗

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/omkar-gutal-a25935249/)

