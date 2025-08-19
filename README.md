# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 19-08-2025

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
DEVELOPED BY: NARRA RAMYA
REG NO: 212223040128
```

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv("/content/9. Sales-Data-Analysis.csv")

df['Date'] = pd.to_datetime(df['Date'], format='%d-%m-%Y')
df.set_index('Date', inplace=True)

df['Sales'] = df['Price'] * df['Quantity']

# Step 3: Plot original data
plt.figure(figsize=(10,5))
plt.plot(df['Sales'], label='Original Data')
plt.title("Sales Data - Original")
plt.legend()
plt.show()

# Step 4: Regular Differencing
df['Sales_diff'] = df['Sales'].diff()

plt.figure(figsize=(10,5))
plt.plot(df['Sales_diff'], label='Regular Differencing')
plt.title("Sales Data - Regular Differencing")
plt.legend()
plt.show()


# Step 5: Seasonal Differencing (Assuming 12-month seasonality)
df['Sales_seasonal_diff'] = df['Sales'].diff(12)

plt.figure(figsize=(10,5))
plt.plot(df['Sales_seasonal_diff'], label='Seasonal Differencing')
plt.title("Sales Data - Seasonal Differencing")
plt.legend()
plt.show()

# Step 6: Log Transformation
df['Sales_log'] = np.log(df['Sales'])

plt.figure(figsize=(10,5))
plt.plot(df['Sales_log'], label='Log Transformation')
plt.title("Sales Data - Log Transformation")
plt.legend()
plt.show()

df['Sales_log_diff'] = df['Sales_log'].diff()
plt.figure(figsize=(10,5))
plt.plot(df['Sales_log_diff'], label="Log + Regular Differencing")
plt.legend()
plt.show()
check_stationarity(df['Sales_log_diff'], "After Log + Regular Differencing")


df['Sales_log_seasonal_diff'] = df['Sales_log'].diff(12).diff()
plt.figure(figsize=(10,5))
plt.plot(df['Sales_log_seasonal_diff'], label="Log + Regular + Seasonal Differencing")
plt.legend()
plt.show()
check_stationarity(df['Sales_log_seasonal_diff'], "After Log + Regular + Seasonal Differencing")


 plt.tight_layout()
 plt.show()


df.plot(kind='line')
```


### OUTPUT:

# ORIGINAL :

<img width="1060" height="561" alt="image" src="https://github.com/user-attachments/assets/c77cbd49-f217-492e-b098-4a1c408eb0a9" />


# REGULAR DIFFERENCING:

<img width="1074" height="557" alt="image" src="https://github.com/user-attachments/assets/e233e237-800f-4b93-96a9-18183f3be90a" />


# SEASONAL ADJUSTMENT:

<img width="1075" height="559" alt="image" src="https://github.com/user-attachments/assets/ee784c1e-bf7d-4236-80d0-4fae441dfba2" />

# LOG TRANSFORMATION:

<img width="1030" height="561" alt="image" src="https://github.com/user-attachments/assets/9eac07ec-7a80-4fd0-a549-95e5b325383c" />

# LOG AND REGULAR DIFFERENCING:


<img width="1045" height="534" alt="image" src="https://github.com/user-attachments/assets/74a6cbf8-4257-4857-a435-de56123f4884" />

# LOG AND REGUALR AND SEASONAL DIFFERENCING :

<img width="1021" height="520" alt="image" src="https://github.com/user-attachments/assets/c2985f76-c927-4c0c-8995-7baa20419d2e" />


# OVERALL VIEW:

<img width="722" height="547" alt="image" src="https://github.com/user-attachments/assets/e550ea63-7033-4246-ac27-8a67024c01b5" />

### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
