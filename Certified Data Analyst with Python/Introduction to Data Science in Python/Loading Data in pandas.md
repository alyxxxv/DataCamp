# Loading Data in pandas

digunakan untuk memproses data. bisa dalam bentuk tabular, spreadsheet, dll.

<img width="356" alt="2022-07-22_19h37_06" src="https://user-images.githubusercontent.com/87213160/180440645-1bd86962-18cf-49e9-9856-aa93ecd43424.png">

<img width="389" alt="2022-07-22_19h39_59" src="https://user-images.githubusercontent.com/87213160/180441090-7008375f-fe55-4159-8481-a5ceec287d93.png">

```python 
# Import pandas under the alias pd
import pandas as pd

# Load the CSV "credit_records.csv"
credit_records = pd.read_csv('credit_records.csv')

# Display the first five rows of credit_records using the .head() method
print(credit_records.head())

# Use .info() to inspect the DataFrame credit_records
print(credit_records.info())
```

**Selecting Columns**

Untuk menghitung jumlah kolom dari 'price'
```python 
credit_records.price.sum()
```
to plot data 
```python 
plt.plot(ransom['letter'], ransom['frequency'])
```

Selecting String with Bracket 

```python 
suspect = credit_records['suspect']

Selecting with dot
```python
price = credit_records.price
```

catatan : Jika nama kolomnya terdapat spaces dan special character, maka harus menggunakan bracket ['  ']

using bracket

```python
# Select the column item from credit_records
# Use brackets and string notation
items = credit_records['item']

# Display the results
print(items)
```

using dot
```python
# Select the column item from credit_records
# Use dot notation
items = credit_records.item

# Display the results
print(items)
```
```python 
# One or more lines of code contain errors.
# Fix the errors so that the code runs.

# Select the location column in credit_records
location = credit_records['location']

# Select the item column in credit_records
items = credit_records.item

# Display results
print(location)
```

**Select Row with Logic**

using logic with dataframe 
```python 
credit_records.price > 20.00
```

or 

```python 
credit_records[credit_records.price > 20.00]
```
<img width="403" alt="2022-07-22_20h56_24" src="https://user-images.githubusercontent.com/87213160/180454536-59321f64-7d08-4ac7-a950-8951fe194ee5.png">




