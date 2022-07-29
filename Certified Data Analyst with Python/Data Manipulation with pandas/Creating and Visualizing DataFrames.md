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



