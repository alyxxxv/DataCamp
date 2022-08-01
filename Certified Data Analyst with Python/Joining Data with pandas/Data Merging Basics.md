# Data Merging Basics

**Inner Join**

```python 
wards_census=  wards.merge(census, on='ward')
```
Inner join merupakan menggabungkan dari data yang sama dari kedua tabel. 

**Suffixes**

Untuk menghindari pernamaan kolom yang sama, maka bisa menggunakan suffixes. 
```python 
wards_census=  wards.merge(census, on='ward', suffixes=('_ward', '_cen'))
print(wards_census.head())
print(wards_census.shape)
```
EXERCISE 1 
```python 
# Merge the taxi_owners and taxi_veh tables setting a suffix
taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid', suffixes=('_own','_veh'))

# Print the value_counts to find the most popular fuel_type
print(taxi_own_veh['fuel_type'].value_counts())
```
EXERCISE 2 
```python 
# Print the first few rows of the census_altered table to view the change 
print(census_altered[['ward']].head())

# Merge the wards and census_altered tables on the ward column
wards_census_altered = wards.merge(census_altered, on='ward')

# Print the shape of wards_census_altered
print('wards_census_altered table shape:', wards_census_altered.shape)
```

**One to Many Relationship**

One to One : Every row in the left table is related to only one row in the right table. 

<img width="253" alt="2022-07-30_18h01_19" src="https://user-images.githubusercontent.com/87213160/181907966-f9952fc3-6c31-47f7-8f7e-cac55115e632.png">


