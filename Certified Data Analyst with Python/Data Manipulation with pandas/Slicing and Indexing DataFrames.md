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

