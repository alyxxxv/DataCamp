# Slicing and Indexing DataFrames

**Explisit Indexes**
Setting a column as index
```python 
dogs_ind = dogs.set_index("name")
print(dogs_ind)
```
Removing Index 
```python 
dogs_ind.reset_index(drop=True)
```
indexes make subsetting simpler. 
```python
dogs[dogs["name"].isin(["Bella", "Stella"])]
#atau 
dogs_ind.loc[["Bella", "Stella"]]
```
multiple column in indexes
```python 
dogs1= dogs.set_index(["Breed", "color"])
print(dogs1)
```
Subset inner levels with a list of tuples
```python 
dogs_ind3.loc[[("Labrador", "Brown"), ("Chihuahua", "Tan")]]
```
<img width="422" alt="2022-07-28_20h39_23" src="https://user-images.githubusercontent.com/87213160/181519356-ed24a4eb-b51e-46e1-bf2c-d9a995704ef4.png">

Sorting by index values 
```python 
dogs_ind3.sort_index()
```
Controlling sort_index
```python 
dogs_ind3.sort_index(level=["color", "breed"], ascending=[True, False])
```
<img width="259" alt="2022-07-28_20h41_37" src="https://user-images.githubusercontent.com/87213160/181519839-8bc47720-a9ab-4b40-99f4-59b47d4cc80d.png">

EXERCISE 1
```python 
# Look at temperatures
print(temperatures)

# Index temperatures by city
temperatures_ind = temperatures.set_index("city")

# Look at temperatures_ind
print(temperatures_ind)

# Reset the index, keeping its contents
print(temperatures_ind.reset_index())

# Reset the index, dropping its contents
print(temperatures_ind.reset_index(drop=True))
```

EXERCISE 2 

Create a list called cities that contains "Moscow" and "Saint Petersburg".
Use [] subsetting to filter temperatures for rows where the city column takes a value in the cities list.
Use .loc[] subsetting to filter temperatures_ind for rows where the city is in the cities list.
```python 
# Make a list of cities to subset on
cities = ["Moscow", "Saint Petersburg"]

# Subset temperatures using square brackets
print(temperatures[temperatures["city"].isin(cities)])

# Subset temperatures_ind using .loc[]
print(temperatures_ind.loc[cities])
```

EXERCISE 3

Set the index of temperatures to the "country" and "city" columns, and assign this to temperatures_ind.
Specify two country/city pairs to keep: "Brazil"/"Rio De Janeiro" and "Pakistan"/"Lahore", assigning to rows_to_keep.
Print and subset temperatures_ind for rows_to_keep using .loc[].

```python 
# Index temperatures by country & city
temperatures_ind = temperatures.set_index(["country", "city"])

# List of tuples: Brazil, Rio De Janeiro & Pakistan, Lahore
rows_to_keep = [("Brazil", "Rio De Janeiro"), ("Pakistan", "Lahore")]

# Subset for rows to keep
print(temperatures_ind.loc[rows_to_keep])
```

EXERCISE 4

Sort temperatures_ind by the index values.
Sort temperatures_ind by the index values at the "city" level.
Sort temperatures_ind by ascending country then descending city.

```python
# Sort temperatures_ind by index values
print(temperatures_ind.sort_index())

# Sort temperatures_ind by index values at the city level
print(temperatures_ind.sort_index(level="city"))

# Sort temperatures_ind by country then descending city
print(temperatures_ind.sort_index(level=["country", "city"], ascending=[True, False]))
```

**Slicing and subsetting with .loc and .iloc**

Slicing adalah teknik untuk memilih sebuah elemen yang berurutan. 

<img width="433" alt="2022-07-29_08h22_04" src="https://user-images.githubusercontent.com/87213160/181663275-b779c58a-9b29-45ae-9146-34641e6b449a.png">

Set Index lalu di sorting atau diurutkan. 

```python 
dogs_srt = dogs.set_index(["breed", "color"]).sort_index()
print(dogs_srt)
```

jika menggunakan loc dan iloc, loc untuk string, dan iloc untuk urutan. 

<img width="439" alt="2022-07-29_08h27_22" src="https://user-images.githubusercontent.com/87213160/181663831-e818c9e9-823a-499f-a1cf-d086c66d76a0.png">
<img width="437" alt="2022-07-29_08h28_04" src="https://user-images.githubusercontent.com/87213160/181663897-7d20a41e-63b7-4275-98f6-7383cae9b32a.png">

Slicing Columns

<img width="440" alt="2022-07-29_08h29_08" src="https://user-images.githubusercontent.com/87213160/181663996-aa0ffcf4-80ea-450d-9a1c-160d9ae84bae.png">
<img width="440" alt="2022-07-29_08h29_43" src="https://user-images.githubusercontent.com/87213160/181664042-95b11917-115e-4818-96fa-e00f22a20f96.png">

Jika menggunakan .iloc maka : 
```python 
print(dogs.iloc[2:5, 1:4])
```
<img width="439" alt="2022-07-29_08h32_07" src="https://user-images.githubusercontent.com/87213160/181664291-9d4246e3-9aeb-45b0-8cb2-0622fe2a20b5.png">

prinsipnya adalah [baris, kolom] 

EXERCISE 1 

Sort the index of temperatures_ind.
Use slicing with .loc[] to get these subsets:
from Pakistan to Russia.
from Lahore to Moscow. (This will return nonsense.)
from Pakistan, Lahore to Russia, Moscow.

```python 
# Sort the index of temperatures_ind
temperatures_srt = temperatures_ind.sort_index()

# Subset rows from Pakistan to Russia
print(temperatures_srt.loc["Pakistan":"Russia"])

# Try to subset rows from Lahore to Moscow
print(temperatures_srt.loc["Lahore":"Moscow"])

# Subset rows from Pakistan, Lahore to Russia, Moscow
print(temperatures_srt.loc[("Pakistan", "Lahore"):("Russia", "Moscow")])
```

EXERCISE 2

Use .loc[] slicing to subset rows from India, Hyderabad to Iraq, Baghdad.
Use .loc[] slicing to subset columns from date to avg_temp_c.
Slice in both directions at once from Hyderabad to Baghdad, and date to avg_temp_c.

```python 
# Subset rows from India, Hyderabad to Iraq, Baghdad
print(temperatures_srt.loc[("India", "Hyderabad"):("Iraq", "Baghdad")])

# Subset columns from date to avg_temp_c
print(temperatures_srt.loc[:, "date":"avg_temp_c"])

# Subset in both directions at once
print(temperatures_srt.loc[("India", "Hyderabad"):("Iraq", "Baghdad"), "date":"avg_temp_c"])
```

EXERCISE 3 

Use Boolean conditions, not .isin() or .loc[], and the full date "yyyy-mm-dd", to subset temperatures for rows in 2010 and 2011 and print the results.
Set the index of temperatures to the date column and sort it.
Use .loc[] to subset temperatures_ind for rows in 2010 and 2011.
Use .loc[] to subset temperatures_ind for rows from Aug 2010 to Feb 2011.

```python 
# Use Boolean conditions to subset temperatures for rows in 2010 and 2011
temperatures_bool = temperatures[(temperatures["date"] >= "2010-01-1") & (temperatures["date"] <= "2011-12-31")]
print(temperatures_bool)

# Set date as the index and sort the index
temperatures_ind = temperatures.set_index("date").sort_index()

# Use .loc[] to subset temperatures_ind for rows in 2010 and 2011
print(temperatures_ind.loc["2010":"2011"])

# Use .loc[] to subset temperatures_ind for rows from Aug 2010 to Feb 2011
print(temperatures_ind.loc["2010-08":"2011-02"])
```

EXERCISE 4

Use .iloc[] on temperatures to take subsets.

Get the 23rd row, 2nd column (index positions 22 and 1).
Get the first 5 rows (index positions 0 to 5).
Get all rows, columns 3 and 4 (index positions 2 to 4).
Get the first 5 rows, columns 3 and 4.

```python 
# Get 23rd row, 2nd column (index 22, 1)
print(temperatures.iloc[22,1])

# Use slicing to get the first 5 rows
print(temperatures.iloc[0:5, :])

# Use slicing to get columns 3 to 4
print(temperatures.iloc[:, 2:4])

# Use slicing in both directions at once
print(temperatures.iloc[0:5, 2:4])
```

**Working With Pivot Tables**

```python 
dogs_height_by_breed_vs_color = dogs_pack.pivot_table("height_cm", index="breed", columns="color")
print(dogs_height_by_breed_vs_color)
```

<img width="432" alt="2022-07-29_09h12_42" src="https://user-images.githubusercontent.com/87213160/181668454-663410ab-5155-450d-9b03-56bc28450e59.png">

The Axis Argument
```python 
dogs_height_by_breed_vs_colo.mean(axis="index")
```
<img width="185" alt="2022-07-29_09h14_56" src="https://user-images.githubusercontent.com/87213160/181668694-713aa10d-7e3a-44b1-b65e-5d4ce2c78dae.png">

calcultaing summary stats accros columns
```python 
dogs_height_by_breed_vs_colo.mean(axis="columns")
```
<img width="198" alt="2022-07-29_09h15_13" src="https://user-images.githubusercontent.com/87213160/181668728-8183a9fe-9fcc-48c4-958d-5ee10abf9304.png">


EXERCISE 1

Add a year column to temperatures, from the year component of the date column.
Make a pivot table of the avg_temp_c column, with country and city as rows, and year as columns. Assign to temp_by_country_city_vs_year, and look at the result.

```python 
# Add a year column to temperatures
temperatures['year'] = temperatures['date'].dt.year

# Pivot avg_temp_c by country and city vs year
temp_by_country_city_vs_year = temperatures.pivot_table("avg_temp_c", index=['country', 'city'], columns ="year")

# See the result
print(temp_by_country_city_vs_year)
```

EXERCISE 2

Use .loc[] on temp_by_country_city_vs_year to take subsets.

From Egypt to India.
From Egypt, Cairo to India, Delhi.
From Egypt, Cairo to India, Delhi, and 2005 to 2010.

```python 
# Subset for Egypt to India
print(temp_by_country_city_vs_year.loc["Egypt":"India"])

# Subset for Egypt, Cairo to India, Delhi
print(temp_by_country_city_vs_year.loc[("Egypt", "Cairo"):("India", "Delhi")])

# Subset for Egypt, Cairo to India, Delhi, and 2005 to 2010
print(temp_by_country_city_vs_year.loc[("Egypt", "Cairo"):("India", "Delhi"), "2005":"2010"])
```

EXERCISE 3

Calculate the mean temperature for each year, assigning to mean_temp_by_year.
Filter mean_temp_by_year for the year that had the highest mean temperature.
Calculate the mean temperature for each city (across columns), assigning to mean_temp_by_city.
Filter mean_temp_by_city for the city that had the lowest mean temperature.

```python
# Get the worldwide mean temp by year
mean_temp_by_year = temp_by_country_city_vs_year.mean()

# Filter for the year that had the highest mean temp
print(mean_temp_by_year[mean_temp_by_year==mean_temp_by_year.max()])

# Get the mean temp by city
mean_temp_by_city = temp_by_country_city_vs_year.mean(axis="columns")

# Filter for the city that had the lowest mean temp
print(mean_temp_by_city[mean_temp_by_city==mean_temp_by_city.min()])
```

