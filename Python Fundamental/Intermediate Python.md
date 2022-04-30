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

