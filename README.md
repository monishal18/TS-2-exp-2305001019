# EXPERIMENT 2: TIME SERIES ANALYSIS AND DECOMPOSITION
# NAME : MONISHA 
# REG NO :2305001019

## Aim
To perform time series analysis and decomposition on the monthly average temperature of a city using Python.

## Software Required
- Python 3
- Google Colab or Jupyter Notebook
- Pandas
- Matplotlib
- Statsmodels

## Procedure
1. Import the required libraries.
2. Create monthly temperature data.
3. Convert the month column into a time index.
4. Plot the original time series.
5. Decompose the time series into trend, seasonal, and residual components.
6. Plot and display each component.
7. Observe the results.

## Observation
The monthly temperature increases until May and then gradually decreases towards December. The decomposition separates the observed data into trend, seasonal, and residual components.


## Program
```

import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Create monthly temperature data
months = [
    "Jan", "Feb", "Mar", "Apr", "May", "Jun",
    "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"
]

temperature = [
    25, 27, 29, 32, 34, 33,
    32, 31, 30, 29, 27, 25
]

# Create DataFrame
data = pd.DataFrame({
    "Month": months,
    "Temperature": temperature
})

print("Monthly Temperature:")
print(data)

# Convert month into a time index
data["Month"] = pd.date_range(
    start="2025-01-01",
    periods=12,
    freq="ME"
)

data.set_index("Month", inplace=True)

print("\nTime Series Data:")
print(data)

# Plot the original time series
plt.figure(figsize=(10, 5))

plt.plot(
    data.index,
    data["Temperature"],
    marker="o"
)

plt.title("Monthly Average Temperature")
plt.xlabel("Month")
plt.ylabel("Temperature (°C)")
plt.grid()
plt.show()

# Perform time series decomposition
result = seasonal_decompose(
    data["Temperature"],
    model="additive",
    period=12
)

# Plot all decomposition components
result.plot()
plt.show()

# Display individual components
plt.figure()
plt.plot(result.observed)
plt.title("Observed Temperature")
plt.show()

plt.figure()
plt.plot(result.trend)
plt.title("Trend Component")
plt.show()

plt.figure()
plt.plot(result.seasonal)
plt.title("Seasonal Component")
plt.show()

plt.figure()
plt.plot(result.resid)
plt.title("Residual Component")
plt.show()

# Print decomposition components
print("\nTrend:")
print(result.trend)

print("\nSeasonal:")
print(result.seasonal)

print("\nResidual:")
print(result.resid)
```

## Expected Output
- Monthly average temperature graph
<img width="667" height="357" alt="image" src="https://github.com/user-attachments/assets/5d40861e-84b6-4902-ad74-ee96dd64f5bf" />

- Observed temperature component


<img width="662" height="113" alt="image" src="https://github.com/user-attachments/assets/ade45e2c-ebe7-4cc6-996e-7ea404deb9a8" />

- Trend component

<img width="650" height="132" alt="image" src="https://github.com/user-attachments/assets/1de9d19f-f641-47d2-b032-a938879a12ad" />

- Seasonal component

<img width="672" height="130" alt="image" src="https://github.com/user-attachments/assets/997fbf14-e91b-4eaf-b116-2b3fbdf11425" />

- Residual component

<img width="652" height="150" alt="image" src="https://github.com/user-attachments/assets/e59d3d92-f961-4e8d-af19-bab770a6d048" />


## Result
Thus, the monthly temperature time series was successfully plotted and decomposed into observed, trend, seasonal, and residual components using Python.
