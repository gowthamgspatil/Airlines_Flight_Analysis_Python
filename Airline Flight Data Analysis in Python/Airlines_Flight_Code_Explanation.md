###  **Detailed Code Explanation**

#### **1. Importing Libraries**

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
```

* `pandas` → For data loading and manipulation.
* `numpy` → For numerical operations.
* `seaborn` and `matplotlib` → For data visualization.

#### **2. Loading the Dataset**

```python
df = pd.read_csv('Airline Dataset.csv')
```

* Loads the flight dataset into a DataFrame named `df`.
* `Airline Dataset.csv` is expected to have flight-related records like date, price, airline, source, destination, etc.

---

#### **3. Basic Data Exploration**

```python
df.head()
df.info()
df.describe()
```

* `.head()` → Displays the first 5 rows.
* `.info()` → Displays column names, data types, and missing values.
* `.describe()` → Gives statistical summary of numerical columns (mean, std, min, max).

---

#### **4. Checking Missing Values**

```python
df.isnull().sum()
```

* Identifies how many missing values exist per column.

---

#### **5. Unique Values and Data Cleaning**

```python
df['Airline'].unique()
df['Source'].unique()
df['Destination'].unique()
```

* Displays the unique values in specific categorical columns to understand possible categories.

---

#### **6. Data Preprocessing**

* Columns like **Date\_of\_Journey**, **Dep\_Time**, and **Arrival\_Time** are converted from string to datetime format:

```python
df['Date_of_Journey'] = pd.to_datetime(df['Date_of_Journey'])
```

* Then new columns like **Journey\_day**, **Journey\_month**, etc., are extracted:

```python
df["Journey_day"] = df["Date_of_Journey"].dt.day
df["Journey_month"] = df["Date_of_Journey"].dt.month
```

#### **7. Feature Engineering**

* Departure and arrival hours/minutes are extracted:

```python
df['Dep_hour'] = pd.to_datetime(df['Dep_Time']).dt.hour
df['Dep_min'] = pd.to_datetime(df['Dep_Time']).dt.minute
```

* Duration is split into hours and minutes.

---

#### **8. Data Cleaning – Categorical Columns**

* Columns such as `Airline`, `Source`, and `Destination` are converted using `pd.get_dummies()` for machine learning readiness (one-hot encoding).

---

#### **9. Dropping Unnecessary Columns**

```python
df.drop(['Route', 'Additional_Info', 'Date_of_Journey', 'Dep_Time', 'Arrival_Time'], axis=1, inplace=True)
```

* These columns are dropped either due to redundancy or because they’ve been broken into more useful components.

---

#### **10. Correlation Analysis**

```python
plt.figure(figsize=(18,10))
sns.heatmap(df.corr(), annot=True, cmap="RdYlGn")
```

* Heatmap of correlation between features and target (likely 'Price') to understand relationships between variables.

---

#### **11. Feature Importance using ExtraTreesRegressor**

```python
from sklearn.ensemble import ExtraTreesRegressor

model = ExtraTreesRegressor()
model.fit(X, y)
```

* Trains a tree-based model to identify which features are most important in predicting price.

---

#### **12. Train-Test Split and Model Training**

```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

rf = RandomForestRegressor()
rf.fit(X_train, y_train)
```

* The dataset is split into training and testing sets.
* A **Random Forest Regressor** model is trained to predict flight prices.

---

#### **13. Predictions and Metrics**

```python
y_pred = rf.predict(X_test)

from sklearn import metrics
metrics.r2_score(y_test, y_pred)
metrics.mean_absolute_error(y_test, y_pred)
```

* Model predictions are evaluated using R² and MAE (Mean Absolute Error).

---

#### **14. Visual Comparison of Actual vs Predicted**

```python
sns.distplot(y_test - y_pred)
plt.scatter(y_test, y_pred)
```

* Helps visually compare predicted flight prices with actual ones.

---

#### **15. Model Serialization with Pickle**

```python
import pickle
file = open('flight_rf.pkl', 'wb')
pickle.dump(rf, file)
```

* Saves the trained model for future use without retraining.

---

###  **Key Insights This Notebook Provides**

* Airline, Source, Destination, Duration, and Total Stops significantly affect the price.
* Time of day (departure/arrival time) also influences flight cost.
* Random Forest performs well as a predictive model.
* Data cleaning and feature engineering are essential before modeling.
