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

EXERCISE 1 
```python 
# Merge action_movies to the scifi_movies with right join
action_scifi = action_movies.merge(scifi_movies, on='movie_id', how='right',
                                   suffixes=('_act','_sci'))

# From action_scifi, select only the rows where the genre_act column is null
scifi_only = action_scifi[action_scifi['genre_act'].isnull()]

# Merge the movies and scifi_only tables with an inner join
movies_and_scifi_only = movies.merge(scifi_only, left_on = 'id', right_on = 'movie_id')

# Print the first few rows and shape of movies_and_scifi_only
print(movies_and_scifi_only.head())
print(movies_and_scifi_only.shape)
```
EXERCISE 2 

Merge movie_to_genres and pop_movies using a right join. Save the results as genres_movies.
Group genres_movies by genre and count the number of id values.

```python 
# Use right join to merge the movie_to_genres and pop_movies tables
genres_movies = movie_to_genres.merge(pop_movies, how='right', 
                                      left_on = 'movie_id', 
                                      right_on='id')
print(genres_movies)
# Count the number of genres (dikumpulkan berdasarkan genre dan dihitung berdasarkan id)
genre_count = genres_movies.groupby('genre').agg({'id':'count'})

# Plot a bar chart of the genre_count
genre_count.plot(kind='bar')
plt.show()
```
<img width="692" alt="2022-08-03_20h24_45" src="https://user-images.githubusercontent.com/87213160/182618981-9b9434dc-2b54-4a4d-a586-d749f6598775.png">

EXERCISE 3 

Using Outer Join to Select actors

<img width="230" alt="2022-08-03_20h30_15" src="https://user-images.githubusercontent.com/87213160/182620157-eea92bb5-dde7-4585-9e26-b45f7a635c72.png">

Save to iron_1_and_2 the merge of iron_1_actors (left) with iron_2_actors tables with an outer join on the id column, and set suffixes to ('_1','_2').
Create an index that returns True if name_1 or name_2 are null, and False otherwise.

```python
# Merge iron_1_actors to iron_2_actors on id with outer join using suffixes
iron_1_and_2 = iron_1_actors.merge(iron_2_actors,
                                     on = 'id',
                                     how = 'outer',
                                     suffixes=('_1', '_2'))

# Create an index that returns true if name_1 or name_2 are null
m = ((iron_1_and_2['name_1'].isnull()) | 
     (iron_1_and_2['name_2'].isnull()))

# Print the first few rows of iron_1_and_2
print(iron_1_and_2[m].head())
```

**Merging a table to itself**

<img width="441" alt="2022-08-03_21h01_39" src="https://user-images.githubusercontent.com/87213160/182627538-e5294c14-d0f8-49ab-aa39-56bd3770d855.png">




