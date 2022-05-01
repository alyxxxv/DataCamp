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




