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







