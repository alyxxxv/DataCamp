# Aggregating DataFrames

**Summarizing Numerical Data**

```python 
dogs["height_cm"].mean() #calculate mean
dogs["height_cm"].median() #calculate median 
dogs["height_cm"].mode() #calculate modus
dogs["height_cm"].min() #calculate minimum value
dogs["height_cm"].max() #calculate maximum value
dogs["height_cm"].var() #calculate variance
dogs["height_cm"].std() #calculate standart deviation
```

Metode Agregat (.agg() --> digunakan untuk menghitung statistik khusus
```python 
def pct30(column): #persentil ke 30
  return column.quantile(0.3)

dogs["weight_kg"].agg(pct30) #summaries on single columns
dogs[["weight_kg", "height_cm"]].agg(pct30) #summaries on multiple column
```

Multiple summaries
```python 
def pct40(column): #persentil ke 40
  return column.quantile(0.4)

dogs["weight_kg"].agg([pct30, pct40]) #summaries on single columns
```
<img width="433" alt="2022-07-27_21h46_38" src="https://user-images.githubusercontent.com/87213160/181277563-61250be3-5182-4913-bb43-638cef714f06.png">

Cumulative Sum 
```python 
dogs["weight_kg"].cumsum()
```
Cumulative sum 

.cummax() = kumulatif maximum

.cummin() = kumulatif minimum

.cumprod() = kumulatif product

EXERCISE 1 

```python
# Print the head of the sales DataFrame
print(sales.head())

# Print the info about the sales DataFrame
print(sales.info())

# Print the mean of weekly_sales
print(sales["weekly_sales"].mean())

# Print the median of weekly_sales
print(sales["weekly_sales"].median())
```
EXERCISE 2
```python
# Print the maximum of the date column
print(sales["date"].max())
# Print the minimum of the date column
print(sales["date"].min())
```

**Efficient summaries**

The .agg() method allows you to apply your own custom functions to a DataFrame, as well as apply functions to more than one column of a DataFrame at once, making your aggregations super-efficient. For example,
```python 
df['column'].agg(function)
```

In the custom function for this exercise, "IQR" is short for inter-quartile range, which is the 75th percentile minus the 25th percentile. It's an alternative to standard deviation that is helpful if your data contains outliers.

EXERCISE 1
```python
# Import NumPy and create custom IQR function
import numpy as np
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

# Update to print IQR and median of temperature_c, fuel_price_usd_per_l, & unemployment
print(sales[["temperature_c", "fuel_price_usd_per_l", "unemployment"]].agg([iqr, np.median]))
```

EXERCISE 2

Sort the rows of sales_1_1 by the date column in ascending order.
Get the cumulative sum of weekly_sales and add it as a new column of sales_1_1 called cum_weekly_sales.
Get the cumulative maximum of weekly_sales, and add it as a column called cum_max_sales.
Print the date, weekly_sales, cum_weekly_sales, and cum_max_sales columns.

```python
# Sort sales_1_1 by date
sales_1_1 = sales_1_1.sort_values("date", ascending = True)

# Get the cumulative sum of weekly_sales, add as cum_weekly_sales col
sales_1_1["cum_weekly_sales"] = sales_1_1["weekly_sales"].cumsum()

# Get the cumulative max of weekly_sales, add as cum_max_sales col
sales_1_1["cum_max_sales"] = sales_1_1["weekly_sales"].cummax()

# See the columns you calculated
print(sales_1_1[["date", "weekly_sales", "cum_weekly_sales", "cum_max_sales"]])
```

**Counting**


