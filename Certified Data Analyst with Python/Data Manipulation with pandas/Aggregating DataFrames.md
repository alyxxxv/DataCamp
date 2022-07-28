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

Cara menghapus nama yang duplikat 
```python 
vet_visits.drop_duplicates(subset="name")
```
atau drop multiple column 
```python 
unique_dogs = vet_visits.drop_duplicates(subset=["name", "breed"])
print(unique_dogs)
```

Untuk menghitung jumlah unique value pada dogs, maka: 
```python 
unique_dogs["breed"].value_counts()
#atau
unique_dogs["breed"].value_counts(sort=True) #menggunakan sort argumen
```

menghitung proportion 
```python 
unique_dogs["breed"].value_counts(normalize=True)
```

EXERCISE 1

Remove rows of sales with duplicate pairs of store and type and save as store_types and print the head.
Remove rows of sales with duplicate pairs of store and department and save as store_depts and print the head.
Subset the rows that are holiday weeks using the is_holiday column, and drop the duplicate dates, saving as holiday_dates.
Select the date column of holiday_dates, and print.

```python
# Drop duplicate store/type combinations
store_types = sales.drop_duplicates(subset=["store", "type"])
print(store_types.head())

# Drop duplicate store/department combinations
store_depts = sales.drop_duplicates(subset=["store", "department"])
print(store_depts.head())

# Subset the rows where is_holiday is True and drop duplicate dates
holiday_dates = sales[sales["is_holiday"] == True ].drop_duplicates(subset="date")

# Print date col of holiday_dates
print(holiday_dates["date"])
```

**Counting Categorical Variables**

Counting is a great way to get an overview of your data and to spot curiosities that you might not notice otherwise. In this exercise, you'll count the number of each type of store and the number of each department number using the DataFrames you created in the previous exercise:
```python
# Drop duplicate store/type combinations
store_types = sales.drop_duplicates(subset=["store", "type"])

# Drop duplicate store/department combinations
store_depts = sales.drop_duplicates(subset=["store", "department"])
```
EXERCISE 2 : 

Count the number of stores of each store type in store_types.
Count the proportion of stores of each store type in store_types.
Count the number of different departments in store_depts, sorting the counts in descending order.
Count the proportion of different departments in store_depts, sorting the proportions in descending order

```python
# Count the number of stores of each type
store_counts = store_types["type"].value_counts()
print(store_counts)

# Get the proportion of stores of each type
store_props = store_types["type"].value_counts(normalize=True)
print(store_props)

# Count the number of each department number and sort
dept_counts_sorted = store_depts["department"].value_counts(sort=True)
print(dept_counts_sorted)

# Get the proportion of departments of each number and sort
dept_props_sorted = store_depts["department"].value_counts(sort=True, normalize=True)
print(dept_props_sorted)
```

**Grouped summary statistics**

Grouped Summaries 
``` python 
dogs.groupby("color").["weight_kg"].mean()
```

<img width="427" alt="2022-07-28_09h59_38" src="https://user-images.githubusercontent.com/87213160/181410790-ddd0733c-191d-4abc-b1a1-514a674a451d.png">

Multipled Grouped Summaries
``` python 
dogs.groupby("color").["weight_kg"].agg([min, max, sum])
```
<img width="432" alt="2022-07-28_10h00_38" src="https://user-images.githubusercontent.com/87213160/181410934-58f29b9c-dc77-4edc-82af-55ec0ef1f7da.png">

Grouping by multiple variables
```python 
dogs.groupby(["color", "breed"])["weight"].mean()
```
<img width="241" alt="2022-07-28_10h01_58" src="https://user-images.githubusercontent.com/87213160/181411090-1c053d53-239d-4e33-af18-91ea73777c00.png">

Many Groups, many summaries
``` python 
dogs.groupby(["color", "breed"])[["Weight_kg", "height_cm"]].mean()
```
<img width="244" alt="2022-07-28_10h03_21" src="https://user-images.githubusercontent.com/87213160/181411256-384064c8-e6f8-4061-99bf-1aa0465e4915.png">

EXERCISE 1

Calculate the total weekly_sales over the whole dataset.
Subset for type "A" stores, and calculate their total weekly sales.
Do the same for type "B" and type "C" stores.
Combine the A/B/C results into a list, and divide by sales_all to get the proportion of sales by type.

```python
# Calc total weekly sales
sales_all = sales["weekly_sales"].sum()

# Subset for type A stores, calc total weekly sales
sales_A = sales[sales["type"] == "A"]["weekly_sales"].sum()

# Subset for type B stores, calc total weekly sales
sales_B = sales[sales["type"] == "B"]["weekly_sales"].sum()

# Subset for type C stores, calc total weekly sales
sales_C = sales[sales["type"] == "C"]["weekly_sales"].sum()

# Get proportion for each type
sales_propn_by_type = [sales_A, sales_B, sales_C] / sales_all
print(sales_propn_by_type)
```

EXERCISE 2 

Group sales by "type", take the sum of "weekly_sales", and store as sales_by_type.
Calculate the proportion of sales at each store type by dividing by the sum of sales_by_type. Assign to sales_propn_by_type.

```python
# Group by type; calc total weekly sales
sales_by_type = sales.groupby("type")["weekly_sales"].sum()

# Get proportion for each type
sales_propn_by_type = sales_by_type / sum(sales_by_type)
print(sales_propn_by_type)
```

Group sales by "type" and "is_holiday", take the sum of weekly_sales, and store as sales_by_type_is_holiday.
```python
# From previous step
sales_by_type = sales.groupby("type")["weekly_sales"].sum()

# Group by type and is_holiday; calc total weekly sales
sales_by_type_is_holiday = sales.groupby(["type", "is_holiday"])["weekly_sales"].sum()
print(sales_by_type_is_holiday)
```

EXERCISE 2

Import numpy with the alias np.
Get the min, max, mean, and median of weekly_sales for each store type using .groupby() and .agg(). Store this as sales_stats. Make sure to use numpy functions!
Get the min, max, mean, and median of unemployment and fuel_price_usd_per_l for each store type. Store this as unemp_fuel_stats.

```python
# Import numpy with the alias np
import numpy as np

# For each store type, aggregate weekly_sales: get min, max, mean, and median
sales_stats = sales.groupby("type")["weekly_sales"].agg([min, max, np.mean, np.median])

# Print sales_stats
print(sales_stats)

# For each store type, aggregate unemployment and fuel_price_usd_per_l: get min, max, mean, and median
unemp_fuel_stats = sales.groupby("type")[["unemployment", "fuel_price_usd_per_l"]].agg([min, max, np.mean, np.median])

# Print unemp_fuel_stats
print(unemp_fuel_stats)
```
**Pivot Tables*

untuk mengetahui summary statistic dari sebuah data. 
```python 
dogs.pivot_table(values="weight_kg", index="color")
```
<img width="219" alt="2022-07-28_11h44_41" src="https://user-images.githubusercontent.com/87213160/181422460-392c09a5-f796-4350-b4eb-de1e2d079870.png">

secara default, pivot table melakukan operasi nilai mean. Untuk mengubahnya, maka kita bisa menggunakan syntax aggfunc=...
``` python 
import numpy as n 
dogs.pivot_table(values="weight_kg", index="color", aggfunc=np.median)
```
multiple function
``` python 
import numpy as n 
dogs.pivot_table(values="weight_kg", index="color", aggfunc=[np.mean, np.median)]
```
<img width="168" alt="2022-07-28_11h50_04" src="https://user-images.githubusercontent.com/87213160/181423062-c1f1827f-cd53-4da6-9830-931dc488e67e.png">

Pivot on two variables. 
 ```python 
 dogs.pivot_table(values="weight_kg", index="color", columns="breed")
 ```
 <img width="316" alt="2022-07-28_11h51_53" src="https://user-images.githubusercontent.com/87213160/181423240-8584f692-7c8a-4501-ad67-176bed810213.png">
 
nilai Nan itu merupakan missing value. Untuk mengisi missing value, maka kita bisa menggunakan dengan syntax fill_value = 0 
```python 
 dogs.pivot_table(values="weight_kg", index="color", columns="breed", fill_value=0)
 ```
 <img width="427" alt="2022-07-28_11h53_20" src="https://user-images.githubusercontent.com/87213160/181423408-420bce87-9d2a-4670-9a70-d9d9370829e0.png">

Jika kita mensetting marginnya, maka terdapat rata-rata dari keseluruhan baris dan kolom. seperti berikut: 
```python
dogs.pivot_table(values="weight_kg", index="color", columns="breed", fill_value=0, margins=True)
```
<img width="430" alt="2022-07-28_11h55_09" src="https://user-images.githubusercontent.com/87213160/181423621-c515e847-fc9a-47ad-9eee-c711a5c60d18.png">
