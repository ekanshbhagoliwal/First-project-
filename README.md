# First-project-
My first project 
import pandas as pd import numpy as np import matplotlib.pyplot as plt import seaborn as sns

Load dataset (can be replaced with real sales data)

data = pd.read_csv("sales_data.csv")

Data Cleaning

data.dropna(inplace=True) data['Date'] = pd.to_datetime(data['Date'])

Feature Engineering

data['Month'] = data['Date'].dt.month data['Year'] = data['Date'].dt.year

KPI 1: Total Sales by Year

sales_by_year = data.groupby('Year')['Sales'].sum() print("Total Sales by Year:\n", sales_by_year)

KPI 2: Top 5 Products by Sales

top_products = data.groupby('Product')['Sales'].sum().nlargest(5) print("Top 5 Products by Sales:\n", top_products)

Visualization 1: Sales Trend Over Time

plt.figure(figsize=(10,5)) sns.lineplot(data=data, x='Date', y='Sales', color='blue') plt.title("Sales Trend Over Time") plt.xlabel("Date") plt.ylabel("Sales") plt.show()

Visualization 2: Sales by Category

plt.figure(figsize=(8,5)) sns.barplot(x='Category', y='Sales', data=data, estimator=sum, ci=None) plt.title("Sales by Category") plt.xticks(rotation=45) plt.show()

KPI 3: Monthly Average Sales

monthly_avg = data.groupby('Month')['Sales'].mean() print("Monthly Average Sales:\n", monthly_avg)

