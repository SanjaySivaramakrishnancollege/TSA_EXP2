# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date: 02.05.2026

### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
A - LINEAR TREND ESTIMATION

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
file_path = r"C:\Users\admin\Desktop\Sem lab\TSA\FINAL_USO.csv"  # Replace with your actual file path
data = pd.read_csv(file_path)
data.head()
print(data.columns)
# Convert 'Date' column to datetime format and specify the correct format
data["Date"] = pd.to_datetime(data["Date"], format="%Y-%m-%d")

# Set the 'Date' column as the index
data.set_index("Date", inplace=True)

# Extract the time (x values) and 'Close' (y values)
data["Time"] = np.arange(len(data))
x = data["Time"].values
y = data["Close"].values

# Linear trend calculation (degree 1 polynomial)
linear_coefficients = np.polyfit(x, y, 1)
linear_trend = np.polyval(linear_coefficients, x)

# Polynomial trend calculation (degree 2 polynomial)
polynomial_coefficients = np.polyfit(x, y, 2)
polynomial_trend = np.polyval(polynomial_coefficients, x)

# Create subplots: one for the linear trend, one for the polynomial trend
plt.figure(figsize=(12, 10))

# Plot for linear trend
plt.subplot(2, 1, 1)
plt.plot(data.index, y, label="Gold Price (Close)", color="blue")
plt.plot(data.index, linear_trend, label="Linear Trend", color="red")
plt.title("Gold Price with Linear Trend")
plt.xlabel("Date")
plt.ylabel("Gold Price")
plt.legend()
plt.grid(True)

```
B- POLYNOMIAL TREND ESTIMATION

```
# Plot for polynomial trend
plt.subplot(2, 1, 2)
plt.plot(data.index, y, label="Gold Price (Close)", color="blue")
plt.plot(
    data.index, polynomial_trend, label="Polynomial Trend (Degree 2)", color="green"
)
plt.title("Gold Price with Polynomial Trend")
plt.xlabel("Date")
plt.ylabel("Gold Price")
plt.legend()
plt.grid(True)

# Adjust layout to avoid overlap
plt.tight_layout()

# Show the plots
plt.show()

```
### OUTPUT
A - LINEAR TREND ESTIMATION
<img width="1682" height="701" alt="image" src="https://github.com/user-attachments/assets/faf7957c-d1b6-4d6c-ab9e-6007be86ce45" />

B- POLYNOMIAL TREND ESTIMATION
<img width="1689" height="700" alt="image" src="https://github.com/user-attachments/assets/94516bd1-bed1-4676-831c-6429472a86f1" />

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
