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

