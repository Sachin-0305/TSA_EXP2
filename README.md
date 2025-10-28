# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
### Date: 19/08/2025
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:

```

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures

data = pd.read_csv("/content/GoogleStockPrices.csv")


data['Date'] = pd.to_datetime(data['Date'])

data['Year'] = data['Date'].dt.year
yearly_data = data.groupby("Year")['Close'].mean().reset_index()

X = yearly_data["Year"].values.reshape(-1, 1)
y = yearly_data["Close"].values

```
A - LINEAR TREND ESTIMATION
```
linear_model = LinearRegression()
linear_model.fit(X, y)
yearly_data["Linear_Trend"] = linear_model.predict(X)

plt.figure(figsize=(10, 6))
plt.plot(yearly_data["Year"], y, label="Average Closing Price", marker="o")
plt.plot(yearly_data["Year"], yearly_data["Linear_Trend"], color="orange", label="Linear Trend")
plt.title("Linear Trend Estimation - Google Stock Prices")
plt.xlabel("Year")
plt.ylabel("Average Closing Price")
plt.legend()
plt.grid(True)
plt.show()
```
B- POLYNOMIAL TREND ESTIMATION
```
poly_features = PolynomialFeatures(degree=2)
X_poly = poly_features.fit_transform(X)

poly_model = LinearRegression()
poly_model.fit(X_poly, y)
yearly_data["Poly_Trend"] = poly_model.predict(X_poly)

# Step 7: Plot Polynomial Trend
plt.figure(figsize=(10, 6))
plt.plot(yearly_data["Year"], y, label="Average Closing Price", marker="o", alpha=0.7)
plt.plot(yearly_data["Year"], yearly_data["Poly_Trend"], color="red", label="Polynomial Trend (Degree 2)")
plt.title("Polynomial Trend Estimation - Google Stock Prices")
plt.xlabel("Year")
plt.ylabel("Average Closing Price")
plt.legend()
plt.grid(True)
plt.show()
```
### OUTPUT
A - LINEAR TREND ESTIMATION
<img width="1134" height="677" alt="Screenshot 2025-10-28 091641" src="https://github.com/user-attachments/assets/d0fd3f48-d617-41b3-9a5a-957c2342578d" />

B- POLYNOMIAL TREND ESTIMATION
<img width="1146" height="676" alt="Screenshot 2025-10-28 091659" src="https://github.com/user-attachments/assets/abc1b570-dd21-4aac-b826-fe13a62185f7" />

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
