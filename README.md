# ✈️ Airlines Flight Analysis - Python Project

This project focuses on analyzing flight data using Python. It includes comprehensive data preprocessing, exploratory data analysis (EDA), and visualization to gain insights into airline flight performance.

##  Project Structure

```
Airlines_Flight_Analysis_Python/
│
├── Airlines+Data.csv                # Main dataset used for analysis
├── Airlines_EDA.ipynb              # Jupyter notebook with full EDA and visualizations
└── README.md                       # Project overview and instructions
```

---

##  Objective

The goal of this project is to analyze various factors affecting airline performance and customer satisfaction. This includes delay patterns, flight routes, customer reviews, and service quality.

---

##  Dataset Overview

* **File Name**: `Airlines+Data.csv`
* **Size**: \~34,000+ rows
* **Columns Include**:

  * `Date_of_Journey`, `Dep_Time`, `Arrival_Time`
  * `Airline`, `Source`, `Destination`
  * `Route`, `Duration`, `Total_Stops`
  * `Additional_Info`, `Price`

This dataset contains records of flight bookings, prices, travel duration, and other related attributes.


##  Tools & Technologies Used

* **Python** 
* **Jupyter Notebook**
* **Pandas** – for data manipulation
* **Matplotlib & Seaborn** – for data visualization
* **NumPy** – numerical operations


##  Exploratory Data Analysis (EDA)

Key steps and insights from the `Airlines_EDA.ipynb` notebook:

### 1.  Data Cleaning

* Handled missing values in `Route`, `Total_Stops`, etc.
* Extracted day, month, and year from `Date_of_Journey`.
* Converted `Duration`, `Dep_Time`, and `Arrival_Time` to proper formats.

### 2.  Feature Engineering

* Extracted features like `Journey_Day`, `Journey_Month`, `Dep_Hour`, etc.
* Converted categorical variables (e.g., `Airline`, `Source`) using **Label Encoding** or **One-Hot Encoding**.

### 3.  Visualizations

* Count plots for airlines, sources, destinations
* Boxplots showing price variations across different features
* Line plots and heatmaps for trend analysis

### 4.  Key Insights

* Flights with 1 stop are the most common.
* Jet Airways had the highest number of flights but also showed higher prices.
* Non-stop flights are typically cheaper.
* Flight price correlates with duration and number of stops.


##  Summary

This project showcases:

* Real-world data cleaning challenges
* Feature extraction from date-time fields
* Data visualization for airline business intelligence
* Deriving insights for improving flight pricing and scheduling

##  Future Enhancements

* Integrate machine learning to **predict flight prices**
* Use **interactive dashboards** with Plotly or Power BI
* Add **time-series analysis** for price trends

## Author

**Gowtham GS Patil**
📧 [LinkedIn](https://www.linkedin.com/in/gowthamgshivamuthy) | 🌐 [GitHub](https://github.com/gowthamgspatil)
