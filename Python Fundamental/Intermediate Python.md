# Basic Plots with Matplotlib 

**Visualisasi Data** 

Visualisasi data merupakan bagian yang sangat penting dari analisis data. Biasanya, dalam menggunakan visualisasi data menggunakan Matplotli. 

``` python 
import matplotlib.pyplot as plt 
year = [1950, 1970, 2010]
pop = [2.519, 3.692, 5.263] 
plt.plot(year, pop)
plt.show()
```

untuk membuatnya menjadi scatter plot, maka menggunakan **plt.scatter**

``` python 
import matplotlib.pyplot as plt 
year = [1950, 1970, 2010]
pop = [2.519, 3.692, 5.263] 
plt.scatter(year, pop)
plt.show()
```

untuk mengubah nilai sumbu x menjadi skala logaritmik 
``` python 
# Change the line plot below to a scatter plot
plt.scatter(gdp_cap, life_exp)

# Put the x-axis on a logarithmic scale
plt.xscale('log')

# Show plot
plt.show()
```
<img width="270" alt="2022-04-30_19h10_06" src="https://user-images.githubusercontent.com/87213160/166104972-60e8184c-1eba-4d86-965d-ffda4ad39279.png">

**HISTOGRAM**

merupakan salah satu tools visualisasi data yang dapat membuat gambaran tentang distribusi variabel. 

contohnya 
``` python 
values = [0, 0.6, 1.4, 1.6, 2.2, 2.5, 2.6, 3.2, 3.5, 3.9, 4.2, 6]
plt.hist(values, bins=3)
plt.show()
```

``` python 
# Histogram of life_exp, 15 bins
plt.hist(life_exp, bins=15)

# Show and clear plot
plt.show()
plt.clf()

# Histogram of life_exp1950, 15 bins
plt.hist(life_exp1950, bins=15)

# Show and clear plot again
plt.show()
plt.clf()
```

<img width="265" alt="2022-04-30_19h22_09" src="https://user-images.githubusercontent.com/87213160/166105368-35165425-da9d-48ab-805b-abd94f0c589b.png">


**CUSTOMIZATION**

anda dapat mengubah plot, warna, tipe data, dan lainnya. 

``` python 
import matplotlib.pyplot as plt 
year = [1950, 1970, 2010]
pop = [2.519, 3.692, 5.263] 
plt.plot(year, pop)

plt.xlabel('Year')
plt.ylabel('Population')
plt.title('World Population Projections') #memberi judul pada grafik
plt.yticks([0, 2, 4, 6, 8, 10], ['0', '2B', '4B', '6B', '8B', '10B']) #memberi interval pada ylabel. 
plt.show()
```

``` python
# Import numpy as np
import numpy as np

# Store pop as a numpy array: np_pop
np_pop = np.array(pop)

# Double np_pop
np_pop=np_pop*2

# Update: set s argument to np_pop
plt.scatter(gdp_cap, life_exp, s = np_pop)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000, 10000, 100000],['1k', '10k', '100k'])

# Display the plot
plt.show()
```
<img width="284" alt="2022-04-30_19h47_07" src="https://user-images.githubusercontent.com/87213160/166106205-d2a4f51d-6991-4d30-bc56-d1e1c7aad46b.png">

Case : membuat data yang seperti tadi lalu terbuat list dictionary bahwa setiap benua memiliki warna. 

dict = {
    'Asia':'red',
    'Europe':'green',
    'Africa':'blue',
    'Americas':'yellow',
    'Oceania':'black'
}

dictionary tersebut disimpan dalam bentuk c=col. Lalu, untuk visualisasi datanya adalah sebagai berikut: 

``` python 
# Specify c and alpha inside plt.scatter()
plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c=col, alpha=0.8) 

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000,10000,100000], ['1k','10k','100k'])

# Show the plot
plt.show()
```
<img width="273" alt="2022-04-30_19h52_08" src="https://user-images.githubusercontent.com/87213160/166106372-a9a25e51-a96e-4b60-a9c4-5847cc1acad1.png">

Cara membuat grid 

```python 
# Scatter plot
plt.scatter(x = gdp_cap, y = life_exp, s = np.array(pop) * 2, c = col, alpha = 0.8)

# Previous customizations
plt.xscale('log') 
plt.xlabel('GDP per Capita [in USD]')
plt.ylabel('Life Expectancy [in years]')
plt.title('World Development in 2007')
plt.xticks([1000,10000,100000], ['1k','10k','100k'])

# Additional customizations
plt.text(1550, 71, 'India')
plt.text(5700, 80, 'China')

# Add grid() call
plt.grid(True)

# Show the plot
plt.show()
```

<img width="276" alt="2022-04-30_19h54_16" src="https://user-images.githubusercontent.com/87213160/166106434-a1619ccd-c9dc-48c3-ba41-ffb6c2bbc875.png">

# Dictionary & Pandas

**Dictionary**

kita dapat membuat list. Misalkan terdapat list suatu negara. Kita ingin menentukan jumlah populasi dari Albania. Maka:

```python 
pop =[30.55, 2.77, 39.21]
countries = ["afghanistan", "albania", "algeria"]
ind_alb=countries.index("albania")
ind_alb
pop(ind_alb)
```
atau

```python 
pop =[30.55, 2.77, 39.21]
countries = ["afghanistan", "albania", "algeria"]
world = {"afghanistan":38.55, "albania":2.77, "algeria":39.21}
world["albania"]
```
```python
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo' }

# Print out the keys in europe
print(europe.keys())

# Print out value that belongs to key 'norway'
print(europe['norway'])
```

immutable object : yang tidak bisa diganti 

<img width="318" alt="2022-04-30_21h36_49" src="https://user-images.githubusercontent.com/87213160/166109949-8833f280-ffc6-49d2-9880-2a7e22463a19.png">

```python 
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin', 'norway':'oslo' }

# Add italy to europe
europe['italy'] = 'rome'

# Print out italy in europe
print('italy' in europe)

# Add poland to europe
europe['poland'] = 'warsaw'

# Print europe
print(europe)
```

del and update
```python 
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'bonn',
          'norway':'oslo', 'italy':'rome', 'poland':'warsaw',
          'australia':'vienna' }

# Update capital of germany
europe['germany'] = 'berlin'

# Remove australia
del(europe['australia'])

# Print europe
print(europe)
```

``` python 
# Dictionary of dictionaries
europe = { 'spain': { 'capital':'madrid', 'population':46.77 },
           'france': { 'capital':'paris', 'population':66.03 },
           'germany': { 'capital':'berlin', 'population':80.62 },
           'norway': { 'capital':'oslo', 'population':5.084 } }


# Print out the capital of France
print(europe['france']['capital'])

# Create sub-dictionary data
data = { 'capital':'rome', 'population':59.83 }

# Add data to europe under key 'italy'
europe['italy'] = data

# Print europe
print(europe)
```

# Pandas 

merupakan package data manipulasi. 

``` python 
import pandas as pd 
brics = pd.DataFrame(dict)
```

untuk membaca file csv 
``` python 
brics = pd.read_csv('path/to/brics.csv')
```

EXERCISE
``` python 
# Pre-defined lists
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]

# Import pandas as pd
import pandas as pd 

# Create dictionary my_dict with three key:value pairs: my_dict
my_dict = {'country':names, 'drives_right': dr, 'cars_per_cap':cpc}

# Build a DataFrame cars from my_dict: cars
cars=pd.DataFrame(my_dict)

# Print cars
print(cars)
```

EXERCISE 2

specify the row labels by setting cars.index equal to row_labels. 
``` python 
# Pre-defined lists
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]

# Import pandas as pd
import pandas as pd 

# Create dictionary my_dict with three key:value pairs: my_dict
my_dict = {'country':names, 'drives_right': dr, 'cars_per_cap':cpc}

# Build a DataFrame cars from my_dict: cars
cars=pd.DataFrame(my_dict)

# Print cars
print(cars)
```

**Select and Index**

misalkan ingin mengambil salah satu kolom pada tabel. Bagaimana cara melakukannya dengan tanda kurung siku. maka : 
```python 
brics['country']
atau 

brics[['country']] #untuk menyimpan datanya
```
atau bisa juga menngambil lebih dari 1 kolom 
``` python 
brics[['country', 'capital']]
atau juga 
brics[1:4] #mengambil kolom mulai dari 1 ke 4
```
Pandas terdiri dari 2 komponen 
1. Loc (label based)

2. iLoc (integer position-based)

contoh penggunaan 
``` python 
brics.loc['RU']
```
untuk memilih lebih dari 1 baris, maka contohnya adalah sebagai berikut: 
``` python 
brics.loc[['RU', 'IN', 'CH']]
```

anda juga dapat menggunakan loc untuk memilih semua baris tetapi hanya sejumlah kolom tertentu. contohnya: 
``` python 
brics.loc[['RU', 'IN', 'CH'], ['country', 'capital']]
```
memilih semua baris tetapi hanya kolom tertentu, maka : 
```python 
brics.loc[:, ['country', 'capital']] #tanda titik dua menandakan semua baris
```
sama seperti loc, penggunaan iloc hampir mirip namun lebih ke index yang berupa integer. 
``` python 
brics.iloc[[1,2,3], [0,1]] #ingat kalau index berawal dari 0. 
```
exercise 
``` python 
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out first 3 observations
print(cars.iloc[:3])

# Print out fourth, fifth and sixth observation
print(cars.iloc[3:6])
```

Exercise using Loc and Iloc
``` python 
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out drives_right value of Morocco
print(cars.loc[['MOR'], ['drives_right']])

# Print sub-DataFrame
print(cars.loc[['RU', 'MOR'], ['country', 'drives_right']])
```

# Logic, Control Flow, and Filtering

``` python 
# Comparison of booleans
True == False

# Comparison of integers
-5*15 != 75

# Comparison of strings
"pyscript" == "PyScript"

# Compare a boolean with an integer
True == 1
```

``` 
# Comparison of integers
x = -3 * 6
print(x>= -10)

# Comparison of strings
y = "test"
print("test"<=y)

# Comparison of booleans
print(True>False)
```

``` 
# Create arrays
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])

# my_house greater than or equal to 18
print(my_house>=18)

# my_house less than your_house
print(my_house<your_house)
```

**Boolean Operators **

```
# Define variables
my_kitchen = 18.0
your_kitchen = 14.0

# my_kitchen bigger than 10 and smaller than 18?
print(my_kitchen> 10 and my_kitchen <18)

# my_kitchen smaller than 14 or bigger than 17?
print(my_kitchen<14 or my_kitchen>17)

# Double my_kitchen smaller than triple your_kitchen?
print(my_kitchen*2 < your_kitchen*3)
```

np.logical 
```
# Create arrays
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])

# my_house greater than 18.5 or smaller than 10
print(np.logical_or(my_house > 18.5, your_house<10))

# Both my_house and your_house smaller than 11
print(np.logical_and(my_house < 11, your_house<11))
```

**If, Elif, and Else**

```
# Define variables
room = "kit"
area = 14.0

# if-else construct for room
if room == "kit" :
    print("looking around in the kitchen.")
else :
    print("looking around elsewhere.")

# if-else construct for area
if area > 15 :
    print("big place!")
else : 
    print("pretty small.")
```

```
# Define variables
room = "bed"
area = 14.0

# if-elif-else construct for room
if room == "kit" :
    print("looking around in the kitchen.")
elif room == "bed":
    print("looking around in the bedroom.")
else :
    print("looking around elsewhere.")

# if-elif-else construct for area
if area > 15 :
    print("big place!")
elif area>10 : 
    print("medium size, nice!")
else :
    print("pretty small.")
```

**Filtering Pandas DataFrame**

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Extract drives_right column as Series: dr
dr = cars['drives_right']

# Use dr to subset cars: sel
sel = cars[dr]

# Print sel
print(sel)
```

to be a one liner 
``` 
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Convert code to a one-liner

sel = cars[cars['drives_right']]

# Print sel
print(sel)
```
**Exercise**
```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Create car_maniac: observations that have a cars_per_cap over 500
cpc = cars['cars_per_cap']
many_cars = cpc>500
car_maniac = cars[many_cars]

# Print car_maniac
print(car_maniac)
```

**Exercise 2**
```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Import numpy, you'll need this
import numpy as np

# Create medium: observations with cars_per_cap between 100 and 500
cpc = cars['cars_per_cap']
between = np.logical_and(cpc>100, cpc<500)
medium = cars[between]
# Print medium
print(medium)
```

# Loops

**While Loops**

```python 
error = 50
while error > 1:
    error = error / 4
    print(error)
```

Exercise : ada di link --> https://colab.research.google.com/drive/1EuaVg8bcIccS1nbUdsdLGWu1FXny9c1c?usp=sharing

**For Loop**

```python 
fam = [1.73, 1.68, 1.71, 1.89]
for height in fam: 
    print(height)
```
<img width="378" alt="2022-07-23_19h57_27" src="https://user-images.githubusercontent.com/87213160/180605922-5362ca6b-6f10-4bc6-9c15-e04c029d226b.png">

<img width="370" alt="2022-07-23_20h01_13" src="https://user-images.githubusercontent.com/87213160/180606055-9bdc8991-1290-4aa9-b0ef-3d96cede3094.png">

```python 
# areas list
areas = [11.25, 18.0, 20.0, 10.75, 9.50]

# Change for loop to use enumerate() and update print()
for index, a in enumerate(areas) :
    print("room " + str(index) + ": " + str(a) )
```

**Loop Data Structure Part 1**

melakukan perulangan untuk dictionary 

```python 
world = { "afghanistan":30.55, "albania":2.77, "algeria":39.21}

for key, value in world.items() : 
    print(key + "---" + str(value))
```
atau bisa menggunakan berikut: 
```python 
world = { "afghanistan":30.55, "albania":2.77, "algeria":39.21}

for k, v in world.items() : 
    print(key + "---" + str(value))
```
Untuk penggunaannya pada numpy array. 
```python 
import numpy as np
np_height = np.array([1.73, 1.68, 1.71, 1.89, 1.79])
np_weight = np.array([65.4, 59.2, 63.6, 88.4, 68.7])
bmi = np_weight/np_height

for val in bmi : 
    print(val)
```
Untuk 2D Numpy Array 
```python 
import numpy as np
np_height = np.array([1.73, 1.68, 1.71, 1.89, 1.79])
np_weight = np.array([65.4, 59.2, 63.6, 88.4, 68.7])
meas = np.array([np_height, np_weight])

for val in meas :
    print(val)
```
Numpy array nditer
```python 
import numpy as np
np_height = np.array([1.73, 1.68, 1.71, 1.89, 1.79])
np_weight = np.array([65.4, 59.2, 63.6, 88.4, 68.7])
meas = np.array([np_height, np_weight])

for val in np.nditer(meas) :
    print(val)
```
<img width="210" alt="2022-07-27_09h35_24" src="https://user-images.githubusercontent.com/87213160/181148430-1ea05a7c-a162-459b-9212-f2535028996e.png">

EXERCISE 1 
```python 
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin',
          'norway':'oslo', 'italy':'rome', 'poland':'warsaw', 'austria':'vienna' }
          
# Iterate over europe
for key, value in europe.items(): 
    print("the capital of " + key + " is " + str(value) )
```
Output : 

<img width="171" alt="2022-07-27_09h40_05" src="https://user-images.githubusercontent.com/87213160/181148928-96695cad-d279-4011-a7b2-a06910a50f22.png">

EXERCISE 2: 

Import the numpy package under the local alias np.

Write a for loop that iterates over all elements in np_height and prints out "x inches" for each element, where x is the value in the array.

Write a for loop that visits every element of the np_baseball array and prints it out.

```python 
# Import numpy as np
import numpy as np

# For loop over np_height
for x in np_height: 
    print(str(x) + " inches")

# For loop over np_baseball
for x in np.nditer(np_baseball): 
    print(x)
```

**Loop Data Structures Part 2**

```python 
import pandas as pd 
brics = pd.read_csv('brics.csv', index_col = 0 )

for val in brics : 
    print(val)
```
iterrows
```python 
import pandas as pd 
brics = pd.read_csv('brics.csv', index_col = 0 )

for lab, row in brics.iterrows() : 
    print(lab)
    print(row)
```
Selective Print 
```python 
import pandas as pd 
brics = pd.read_csv("brics.csv", index_col = 0) 
for lab, row in brics.iterrow(): 
    print(lab + ": " +row["capital"])
```
Add column 
 ``` python 
 import pandas as pd 
 brics = pd.read_csv("brics.csv", index_col = 0)
 for lab, row in brics.iterrows() : 
    #Creating series on every iteration 
    brics.loc[lab, "name_lenght"] = len(row["country"])
print(brics)
```
<img width="293" alt="2022-07-27_10h05_04" src="https://user-images.githubusercontent.com/87213160/181151847-ed73fd8e-e469-4e3d-a2d6-14fa263d7601.png">

apply a function in particular columns. 
```python 
import pandas as pd 
brics = pd.read_csv("brics.csv", index_col = 0)
brics["name_length"] = brics["country"].apply(len)
print(brics)
```
EXERCISE 1 : 
Use a for loop to add a new column, named COUNTRY, that contains a uppercase version of the country names in the "country" column. You can use the string method upper() for this.
To see if your code worked, print out cars. Don't indent this code, so that it's not part of the for loop.

```python 
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Code for loop that adds COUNTRY column
for lab, row in cars.iterrows(): 
    cars.loc[lab, "COUNTRY"] = row["country"].upper()

# Print cars
print(cars)
```


