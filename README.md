# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 03-11-2026


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 1: Load dataset
data = pd.read_csv('airline.csv')

# Convert passenger column to numeric
data['Airline passengers carried'] = (
    data['Airline passengers carried']
    .astype(str)
    .str.replace(',', '', regex=False)
    .astype(float)
)

# Step 2: Perform seasonal decomposition
decomposition = seasonal_decompose(
    data['Airline passengers carried'],
    model='additive',
    period=12
)

# Step 3: Plot decomposition
plt.figure(figsize=(10, 12))

# Original Data
plt.subplot(411)
plt.plot(
    data['Airline passengers carried'],
    label='Airline Passengers'
)
plt.legend(loc='upper left')
plt.title('Original Airline Passenger Data')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```
















### OUTPUT:



PLOTTING THE DATA:
<img width="1215" height="346" alt="image" src="https://github.com/user-attachments/assets/fcf50430-68ee-4a34-b1c2-27bfc8701e8d" />


SEASONAL PLOT REPRESENTATION :
<img width="1287" height="332" alt="image" src="https://github.com/user-attachments/assets/224c0a58-d562-4cd1-a835-bca69151c854" />



TREND PLOT REPRESENTATION :
<img width="1223" height="341" alt="image" src="https://github.com/user-attachments/assets/59f9d158-8b29-4c89-b9c5-bb9033d562b1" />

RESIDUAL REPRESENTATION :
<img width="1247" height="326" alt="image" src="https://github.com/user-attachments/assets/16f5a790-dcd3-41be-9492-9f21128fb45d" />




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
