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
data = pd.read_csv("/content/BMW_Car_Sales_Classification.csv")

yearly_sales = data.groupby("Year")["Sales_Volume"].sum().reset_index()
X = yearly_sales["Year"].values.reshape(-1, 1)
y = yearly_sales["Sales_Volume"].values
```
A - LINEAR TREND ESTIMATION
```
linear_model = LinearRegression()
linear_model.fit(X, y)
yearly_sales["Linear_Trend"] = linear_model.predict(X)

plt.figure(figsize=(10,6))
plt.plot(yearly_sales["Year"], y, label="Original Data", marker="o")
plt.plot(yearly_sales["Year"], yearly_sales["Linear_Trend"], color="orange", label="Linear Trend")
plt.title("Linear Trend Estimation - BMW Sales")
plt.xlabel("Year")
plt.ylabel("Sales Volume")
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
yearly_sales["Poly_Trend"] = poly_model.predict(X_poly)

plt.figure(figsize=(10,6))
plt.plot(yearly_sales["Year"], y, label="Original Data", marker="o", alpha=0.6)
plt.plot(yearly_sales["Year"], yearly_sales["Poly_Trend"], color="red", label="Polynomial Trend (Degree 2)")
plt.title("Polynomial Trend Estimation - BMW Sales")
plt.xlabel("Year")
plt.ylabel("Sales Volume")
plt.legend()
plt.grid(True)
plt.show()
```
### OUTPUT
A - LINEAR TREND ESTIMATION
<img width="1202" height="677" alt="Screenshot 2025-08-19 142907" src="https://github.com/user-attachments/assets/b93c648e-e546-4dec-bc3a-6ca00cd243a4" />

B- POLYNOMIAL TREND ESTIMATION
<img width="1174" height="687" alt="Screenshot 2025-08-19 142916" src="https://github.com/user-attachments/assets/5005c4a5-ac73-4be9-a2b9-54b7d8a3d1b3" />

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
