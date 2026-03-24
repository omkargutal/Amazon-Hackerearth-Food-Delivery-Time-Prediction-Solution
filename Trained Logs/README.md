## 📦 Model Artifacts

### 1. `delivery_model.pkl`

**Description:**
This file contains the trained Machine Learning model.

**What it is:**
A `.pkl` (pickle) file is a serialized version of a Python object. In this project, it stores the trained **Stacking Regressor model**, which combines models like XGBoost, LightGBM, and CatBoost.

**Why it exists:**

```python
joblib.dump(model, "delivery_model.pkl")
```

---

### 2. `encoders.pkl`

**Description:**
This file contains the preprocessing objects used for categorical data.

**What it is:**
A serialized dictionary (`le_dict`) that stores multiple `LabelEncoder` objects.

**Why it exists:**
Machine learning models require numerical input. During training, categorical values like:

* `Weather conditions`
* `Road_traffic_density`

were converted into numbers.
---

## Important Note

Both files must be used together during inference:

* `delivery_model.pkl` → for predictions
* `encoders.pkl` → for preprocessing input data

---