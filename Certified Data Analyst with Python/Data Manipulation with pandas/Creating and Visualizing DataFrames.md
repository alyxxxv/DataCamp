# Creating and Visualizing DataFrames

**Visualizing your data**

Untuk membuat histogram 
```python 
import matplotlib.pyplot as plt
dog_pack["height_cm"].hist(bins=5)
plt.show()
```
Bar Plot 
```python 
df.plot(kind="bar", title="kasih judul apa yaaa")
plt.show()
```
Line plot 
```python 
sully.plot(x="date, y="weight_kg", kind="line", rot=45)
plt.show()
```
Scatter plot 
```python 
df.plot(x="nama", y="nama", kind"scatter")
plt.show()
```

Layering. 
```python 
dog_pack[dog_pack["sex"]=="F"]["height_cm"].hist()
dog_pack[dog_pack["sex"]=="M"]["height_cm"].hist()
plt.legend(["F", "M"])
plt.show()
```
<img width="146" alt="2022-07-29_09h39_34" src="https://user-images.githubusercontent.com/87213160/181671457-e42a296e-c30a-47e9-b4d6-53fc74f708dd.png">

untuk membuat sedikit transparan, maka bisa diatur nilai alpha. 

EXERCISE 1

Print the head of the avocados dataset. What columns are available?
For each avocado size group, calculate the total number sold, storing as nb_sold_by_size.
Create a bar plot of the number of avocados sold by size.
Show the plot.

```python 
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Look at the first few rows of data
print(avocados.head())

# Get the total number of avocados sold of each size
nb_sold_by_size = avocados.groupby("size")["nb_sold"].sum()
print(nb_sold_by_size)
# Create a bar plot of the number of avocados sold by size
nb_sold_by_size.plot(kind="bar")

# Show the plot
plt.show()
```
<img width="732" alt="2022-07-29_09h46_34" src="https://user-images.githubusercontent.com/87213160/181672248-d6f5cf1a-83b6-4bde-9b1d-22911b9541db.png">

EXERCISE 2

Get the total number of avocados sold on each date. The DataFrame has two rows for each date—one for organic, and one for conventional. Save this as nb_sold_by_date.
Create a line plot of the number of avocados sold.
Show the plot.

```python 
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Get the total number of avocados sold on each date
nb_sold_by_date = avocados.groupby("date")["nb_sold"].sum()

# Create a line plot of the number of avocados sold by date
nb_sold_by_date.plot(kind="line")

# Show the plot
plt.show()
```
<img width="724" alt="2022-07-29_09h49_24" src="https://user-images.githubusercontent.com/87213160/181672583-6c1d5ea2-92eb-4bab-9915-53b901b6bbe9.png">

EXERCISE 3

Create a scatter plot with nb_sold on the x-axis and avg_price on the y-axis. Title it "Number of avocados sold vs. average price".
Show the plot.

```python 
# Scatter plot of avg_price vs. nb_sold with title
avocados.plot(x='nb_sold', y='avg_price', kind='scatter',title="Number of avocados sold vs. average price")

# Show the plot
plt.show()
```
<img width="718" alt="2022-07-29_09h52_53" src="https://user-images.githubusercontent.com/87213160/181672976-87624303-1342-489a-a166-e1d69ddbdeb6.png">

EXERCISE 4

```python 
# Modify bins to 20
avocados[avocados["type"] == "conventional"]["avg_price"].hist(bins=20, alpha=0.5)

# Modify bins to 20
avocados[avocados["type"] == "organic"]["avg_price"].hist(bins=20, alpha=0.5)

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```

<img width="454" alt="2022-07-29_09h58_21" src="https://user-images.githubusercontent.com/87213160/181673615-5d954f6a-6ab3-4d1b-817d-667b63a941dc.png">

**Handling Missing Values**

detect missing value. 
```python 
dogs.isna()
```
detect any missing value in variable 
```python 
dogs.isna().any()
```
Counting missing value 
```python 
dogs.isna().sum()
```
Plotting Missing Value
```python 
dogs.isna().sum().plot(kind="bar")
plt.show()
```
<img width="198" alt="2022-07-29_10h10_04" src="https://user-images.githubusercontent.com/87213160/181674930-67014414-8c1a-4f84-97f8-c7f061b68e27.png">

Removing Missing Value
```python 
dogs.dropna()
```
atau bisa mengisi missing value dengan 0

```python 
dogs.fillna(0)
```

EXERCISE 1 

```python 
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Check individual values for missing values
print(avocados_2016.isna())

# Check each column for missing values
print(avocados_2016.isna().any())

# Bar plot of missing values by variable
avocados_2016.isna().sum().plot(kind="bar")

# Show plot
plt.show()
```

<img width="714" alt="2022-07-29_10h14_49" src="https://user-images.githubusercontent.com/87213160/181675406-65843611-c61c-4893-8645-1c91822839b4.png">

EXERCISE 2

Replace the missing values of avocados_2016 with 0s and store the result as avocados_filled.
Create a histogram of the cols_with_missing columns of avocados_filled.

```python 
# From previous step
cols_with_missing = ["small_sold", "large_sold", "xl_sold"]
avocados_2016[cols_with_missing].hist()
plt.show()

# Fill in missing values with 0
avocados_filled = avocados_2016.fillna(0)

# Create histograms of the filled columns
avocados_filled[cols_with_missing].hist()

# Show the plot
plt.show()
```
<img width="455" alt="2022-07-29_10h23_51" src="https://user-images.githubusercontent.com/87213160/181676267-7c83bb6f-a0dc-4ecf-8cd4-1a4e27e51ca1.png">

**Creating DataFrames**

<img width="234" alt="2022-07-29_10h47_09" src="https://user-images.githubusercontent.com/87213160/181678774-62614e34-d64f-4feb-a93e-24e7976af2c8.png">

<img width="325" alt="2022-07-29_10h49_28" src="https://user-images.githubusercontent.com/87213160/181679012-3f7cdb0e-7be4-4a7a-bebb-8b1f78b76473.png">

```python 
new_dogs=pd.DataFrame(list_of_dicts)
print(new_dogs)
```
<img width="436" alt="2022-07-29_10h52_15" src="https://user-images.githubusercontent.com/87213160/181679256-25013a3c-cabd-4bc8-b14a-4bfc53010043.png">

EXERCISE 1

Create a list of dictionaries with the new data called avocados_list.
Convert the list into a DataFrame called avocados_2019.
Print your new DataFrame.

```python
# Create a list of dictionaries with new data
avocados_list = [
    {"date": "2019-11-03", "small_sold": 10376832, "large_sold": 7835071},
    {"date": "2019-11-10", "small_sold": 10717154, "large_sold": 8561348},
]

# Convert list into DataFrame
avocados_2019 = pd.DataFrame(avocados_list)

# Print the new DataFrame
print(avocados_2019)
```

EXERCISE 2

Create a dictionary of lists with the new data called avocados_dict.
Convert the dictionary to a DataFrame called avocados_2019.
Print your new DataFrame.

```python 
# Create a dictionary of lists with new data
avocados_dict = {
  "date": ["2019-11-17", "2019-12-01"],
  "small_sold": [10859987, 9291631],
  "large_sold": [7674135, 6238096]
}

# Convert dictionary into DataFrame
avocados_2019 = pd.DataFrame(avocados_dict)

# Print the new DataFrame
print(avocados_2019)
```

**Reading and writing CSVs**

```python 
import pandas as pd 
new_dogs=pd.read_csv('new_dogs.csv')
print(new_dogs)
```
Convert DataFrame to CSV 
```python 
new_dogs.to_csv("new_dogs_with_bmi.csv")
```

