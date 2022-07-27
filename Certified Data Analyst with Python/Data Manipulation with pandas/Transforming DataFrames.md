# Transforming DataFrames

**Introduction to Dataframe**

Pandas merupakan salah satu package library dari Python yang digunakan untuk memanipulasi data. 

When you get a new DataFrame to work with, the first thing you need to do is explore it and see what it contains. There are several useful methods and attributes for this.

**.head()** returns the first few rows (the “head” of the DataFrame).

**.info()** shows information on each of the columns, such as the data type and number of missing values.

**.shape** returns the number of rows and columns of the DataFrame.

**.describe()** calculates a few summary statistics for each column.

**.values**: A two-dimensional NumPy array of values.

**.columns**: An index of columns: the column names.

**.index**: An index for the rows: either row numbers or row names.

```python 
# Import pandas using the alias pd
import pandas as pd

# Print the values of homelessness
print(homelessness.values)

# Print the column index of homelessness
print(homelessness.columns)

# Print the row index of homelessness
print(homelessness.index)
```

**Sorting and subsetting**

kita dapat melakukan sorting untuk nilai numerik tertentu yang kita inginkan. misalnya, kita ingin melakukan sorting pada kolom berat 

```python 
dogs.sort_values("weight_kg")
```

untuk mensettel secara descending atau sebaliknya, maka: 
```python 
dogs.sort_values("weight_kg", ascending=False)
```
**Sorting by Multiple Variables**
```python 
dogs.sort_values(["weight_kg", "height_cm"], ascending = [True, False])
```
**Subsetting Columns**
```python 
dogs["name"]
```
**Subsetting Multiple Columns**
```python 
dogs[["name", "height_cm"]]
```

**Subsetting Rows**

misalkan kita ingin mengetahui manakah yang tingginya melebihi 50, sehingga. 
```python 
dogs["height_cm"]>50
```
Jika kita ingin mengetahui semua kolomnya, maka dapat menggunakan: 

```python
dogs[dogs["height_cm"]>50]
```
<img width="428" alt="2022-07-27_18h53_19" src="https://user-images.githubusercontent.com/87213160/181240436-52bf1d90-dbaf-4e70-8c81-f9b3fd19fb37.png">

**Subsetting based on text data**
```python
dogs[dogs["breed"] == "Labrador"]
```
<img width="426" alt="2022-07-27_18h54_40" src="https://user-images.githubusercontent.com/87213160/181240657-5afa97f9-b293-47c4-95b9-20c6466c50be.png">

**Subsettng based on dates**

```python
dogs[dogs["date_of_birth"] < "2015-01-01"]
```
<img width="425" alt="2022-07-27_18h56_11" src="https://user-images.githubusercontent.com/87213160/181240938-b996d41b-669d-4b96-9b66-d2cc80178887.png">

**Subsetting based on multiple conditions**

bisa menggunakan logical operator 
```python 
is_lab = dogs["breed"] == "Labbrador"
is_brown = dogs["color"] == "Brown"
dogs[is_lab & is_brown]
```
atau
```python 
dogs[ (dogs["breed"] == "Labrador") & (dogs["color"] == "Brown") ]
```
<img width="431" alt="2022-07-27_18h59_27" src="https://user-images.githubusercontent.com/87213160/181241780-8a0e3a0b-fd26-4f94-a922-cfc0d961ac27.png">

**Subsetting using .isin()**

Jika ingin memfilter beberapa nilai dari variabel kategori, maka bisa menggunakan metode isin
```python 
is_black_or_brown = dogs["color"].isin(["Black", "Brown"])
dogs[is_black_or_brown]
```
<img width="427" alt="2022-07-27_19h02_30" src="https://user-images.githubusercontent.com/87213160/181242134-5c6a4781-0f57-4ae4-abcb-f2c40cd98937.png">

Exercise : 
Filter homelessness for cases where the USA census state is in the list of Mojave states, canu, assigning to mojave_homelessness. View the printed result.
```python 
# The Mojave Desert states
canu = ["California", "Arizona", "Nevada", "Utah"]

# Filter for rows in the Mojave Desert states
mojave_homelessness = homelessness[homelessness["state"].isin(canu)]

# See the result
print(mojave_homelessness)
```

**Adding New Column**

```python 
dogs["height_m"]=dogs["height_cm"]/100
print(dogs)
```
Doggy Mass Index 
```python 
dogs["bmi"] = dogs["weight_kg"]/dogs["height_m"]**2
print(dogs.head())
```
<img width="430" alt="2022-07-27_21h14_26" src="https://user-images.githubusercontent.com/87213160/181269668-f9e2401a-f3e7-4c50-8d1d-bd41c148bec7.png">

**Multiple Manipulaions**
```python 
bmi_lt_100 = dogs[dogs["bmi"]<100]
bmi_lt_100_height = bmi_lt_100.sort_values("height_cm", ascending = False)
bmi_lt_100_height[["name", "height_cm", "bmi"]]
```

EXERCISE 1

Add a new column to homelessness, named total, containing the sum of the individuals and family_members columns.
Add another column to homelessness, named p_individuals, containing the proportion of homeless people in each state who are individuals.

```python 
# Add total col as sum of individuals and family_members
homelessness["total"] = homelessness["individuals"] + homelessness["family_members"]
# Add p_individuals col as proportion of total that are individuals
homelessness["p_individuals"] = homelessness["individuals"]/homelessness["total"]

# See the result
print(homelessness)
```

EXERCISE 2

Add a column to homelessness, indiv_per_10k, containing the number of homeless individuals per ten thousand people in each state.
Subset rows where indiv_per_10k is higher than 20, assigning to high_homelessness.
Sort high_homelessness by descending indiv_per_10k, assigning to high_homelessness_srt.
Select only the state and indiv_per_10k columns of high_homelessness_srt and save as result. Look at the result.

```python
# Create indiv_per_10k col as homeless individuals per 10k state pop
homelessness["indiv_per_10k"] = 10000 *homelessness["individuals"]/ homelessness["state_pop"]

# Subset rows for indiv_per_10k greater than 20
high_homelessness = homelessness[homelessness["indiv_per_10k"] > 20]

# Sort high_homelessness by descending indiv_per_10k
high_homelessness_srt = high_homelessness.sort_values("indiv_per_10k", ascending = False)

# From high_homelessness_srt, select the state and indiv_per_10k cols
result = high_homelessness_srt[["state", "indiv_per_10k"]]

# See the result
print(result)
```





