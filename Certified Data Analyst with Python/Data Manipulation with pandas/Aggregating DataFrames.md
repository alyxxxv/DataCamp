# Aggregating DataFrames

**Summarizing Numerical Data**

```python 
dogs["height_cm"].mean() #calculate mean
dogs["height_cm"].median() #calculate median 
dogs["height_cm"].mode() #calculate modus
dogs["height_cm"].min() #calculate minimum value
dogs["height_cm"].max() #calculate maximum value
dogs["height_cm"].var() #calculate variance
dogs["height_cm"].std() #calculate standart deviation
```

Metode Agregat (.agg() --> digunakan untuk menghitung statistik khusus
```python 
def pct30(column): #persentil ke 30
  return column.quantile(0.3)

dogs["weight_kg"].agg(pct30) #summaries on single columns
dogs[["weight_kg", "height_cm"]].agg(pct30) #summaries on multiple column
```

Multiple summaries
```python 
def pct40(column): #persentil ke 40
  return column.quantile(0.4)

dogs["weight_kg"].agg([pct30, pct40]) #summaries on single columns
```
<img width="433" alt="2022-07-27_21h46_38" src="https://user-images.githubusercontent.com/87213160/181277563-61250be3-5182-4913-bb43-638cef714f06.png">

Cumulative Sum 
```python 
dogs["weight_kg"].cumsum()
```
Cumulative sum 

.cummax() = kumulatif maximum

.cummin() = kumulatif minimum

.cumprod() = kumulatif product

