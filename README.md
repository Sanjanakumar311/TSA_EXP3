# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 02-05-2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load dataset
file_path = "/content/Teen_Mental_Health_Dataset.csv"
df = pd.read_csv(file_path)

# ---- STEP 1: Identify time column ----
print(df.columns)

# ---- STEP 2: Select a numeric time series column ----
# Example: 'Stress_Level' or any numeric column
data = df['age'].dropna().values   # Using 'age' as a default numeric column for autocorrelation

# ---- STEP 3: Autocorrelation ----
N = len(data)
lags = range(35)

mean_data = np.mean(data)
variance_data = np.var(data)

autocorr_values = []

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# ---- STEP 4: Plot ----
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation (Time Series)')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```

### OUTPUT:
<img width="790" height="623" alt="image" src="https://github.com/user-attachments/assets/ed7942a7-2350-4624-ad4b-feef79072ae9" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
