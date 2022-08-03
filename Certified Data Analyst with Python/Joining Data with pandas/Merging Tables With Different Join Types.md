# Merging Tables With Different Join Types

**Left Join**

menggabungkan data berdasarkan tabel disebelah kiri. Jika tabel kiri tidak ada di sebelah kanan, maka akan menghasilkan nilai null. 

<img width="434" alt="2022-08-03_18h47_53" src="https://user-images.githubusercontent.com/87213160/182600465-1070e958-cd0e-4e54-88a8-bf6d02215e8a.png">

Left Join 
```python
movie_taglines = movies.merge(taglines, on ='id', how='left')
```

EXERCISE 1 
```python 
# Merge the movies table with the financials table with a left join
movies_financials = movies.merge(financials, on='id', how='left')

# Count the number of rows in the budget column that are missing
number_of_missing_fin = movies_financials['budget'].isna().sum()

# Print the number of movies missing financials
print(number_of_missing_fin)
```

**Right Join**

mengembalikan data pada tabel sebelah kanan 

<img width="439" alt="2022-08-03_20h00_07" src="https://user-images.githubusercontent.com/87213160/182614014-5e0d4e1b-7798-4832-92fd-2f64124cda59.png">

Filtering the Data 
```python 
m = movie_to_genres['genres'] == 'TV Movie'
tv_genre = movie_to_genre[m]
print(tv_genre)
```
**Merge with right Join**

```python 
#kasusnya jika tabel yang ingin dijoin kan berbeda nama kolomnya
tv_movies = movies.merge(tv_genre, how='right', left_on='id', right_on='movie_id'
```

**Outer Join**

menggabungkan data yang sama, dan data yang tidak sama tetap dimunculkan sebagai nilai null 

<img width="449" alt="2022-08-03_20h07_43" src="https://user-images.githubusercontent.com/87213160/182615402-c1d5338b-a0e8-49e8-97a0-a8bbf3f350fd.png">

Dataset for Outer Join 
```python 
m = movie_to_genres['genre'] == 'Family'
family = movie_to_genres[m].head(3)
#and 
m = movie_to_genres['genre'] == 'Comedy'
comedy = movie_to_genres[m].head(3)
```

merge with outer join 
``` python 
family_comedy = family.merge(comedy, on = 'movie_id', how = 'outer', suffixes=('_fam', '_com'))
print(family_comedy)
```
