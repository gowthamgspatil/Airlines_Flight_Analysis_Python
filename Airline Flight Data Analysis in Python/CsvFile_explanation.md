##  airlines_flights_data.csv — Dataset Overview

This dataset contains records of airline flights, capturing various attributes related to flight operations, schedule details, and potential factors affecting flight pricing or delays.

###  Total Rows: *1338*

###  Total Columns: *10*

---

##  Column-Wise Description

| Column Name           | Description                                                                                                                                   |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Airline**           | Name of the airline operating the flight (e.g., IndiGo, Air India, SpiceJet). Useful for airline-wise analysis of trends, pricing, or delays. |
| **Date\_of\_Journey** | The departure date of the flight in `DD/MM/YYYY` format. Important for extracting features like month, day, weekday, or seasonality.          |
| **Source**            | The city from where the flight takes off (e.g., Delhi, Kolkata).                                                                              |
| **Destination**       | The city where the flight lands (e.g., Cochin, Delhi).                                                                                        |
| **Route**             | Flight route taken, represented as a string of stopovers (e.g., "DEL → BOM → COK"). Useful for understanding layovers and travel paths.       |
| **Dep\_Time**         | Scheduled departure time in `HH:MM` format. Can be used to derive time-of-day segments (morning, evening, etc.).                              |
| **Arrival\_Time**     | Scheduled arrival time. Sometimes includes the next day (e.g., "01:10 22 Mar") for overnight flights.                                         |
| **Duration**          | Total duration of the flight (e.g., "2h 50m"). Useful for calculating efficiency and comparing direct vs. connecting flights.                 |
| **Total\_Stops**      | Number of stops between source and destination (e.g., "non-stop", "1 stop"). Influences price and total duration.                             |
| **Price**             | Final flight price in INR (Indian Rupees). This is the **target variable** for prediction models.                                             |

---

##  Use Case Ideas

* **Flight Price Prediction**
  Use features like airline, duration, stops, and journey date to train a regression model for price forecasting.

* **Time Series Analysis**
  Analyze pricing trends over months or seasons.

* **Delay or Route Optimization**
  Study duration vs. route to identify efficient travel paths.

* **EDA & Dashboarding**
  Visualize average price by airline, stops, source-destination, or time of day using tools like Plotly, Power BI, or Tableau.

---

##  Data Cleaning Notes

* `Duration`, `Dep_Time`, and `Arrival_Time` may need to be converted to proper time formats.
* Missing or inconsistent values in `Route` or `Total_Stops` should be handled.
* `Price` is a continuous variable — often needs scaling for ML models.

