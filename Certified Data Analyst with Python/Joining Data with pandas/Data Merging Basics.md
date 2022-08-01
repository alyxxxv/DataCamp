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

```python 
wards_licenses=  wards.merge(licenses, on='ward', suffixes=('_ward', '_lic'))
```

EXERCISE 1

Starting with the licenses table on the left, merge it to the biz_owners table on the column account, and save the results to a variable named licenses_owners.
Group licenses_owners by title and count the number of accounts for each title. Save the result as counted_df
Sort counted_df by the number of accounts in descending order, and save this as a variable named sorted_df.
Use the .head() method to print the first few rows of the sorted_df.

```python 
# Merge the licenses and biz_owners table on account
licenses_owners = licenses.merge(biz_owners, on='account')

# Group the results by title then count the number of accounts
counted_df = licenses_owners.groupby('title').agg({'account':'count'})

# Sort the counted_df in desending order
sorted_df = counted_df.sort_values("account", ascending=False)

# Use .head() method to print the first few rows of sorted_df
print(sorted_df.head())
```
**Merging multiple DataFrames**

menggabungkan dua kolom 
```python 
grants.merge(licenses, on=['address', 'zip'])
```

**Merging multiple tables**
```python
grants_licenses_ward = grants.merge(licenses, on = ['address', 'zip']\.merge(wards, on='ward', suffixes=('_bus', '_ward'))

grants_licenses_ward.head()
```
<img width="440" alt="2022-08-01_17h51_37" src="https://user-images.githubusercontent.com/87213160/182132738-5689cd74-ee49-4102-aa73-cb412ac8ea31.png">

**Merging even more**

Three tables: 
```python 
df1.merge(df2, on='col')\
  .merge(df3, on='col')
```

Four tables: 
```python 
df1.merge(df2, on='col')\
  .merge(df3, on='col')\
  .merge(df4, on='col')
```

EXERCISE 1
```python 
# Merge the ridership, cal, and stations tables
ridership_cal_stations = ridership.merge(cal, on=['year','month','day']) \
							.merge(stations, on='station_id')

# Create a filter to filter ridership_cal_stations
filter_criteria = ((ridership_cal_stations['month'] == 7) 
                   & (ridership_cal_stations['day_type'] == 'Weekday') 
                   & (ridership_cal_stations['station_name'] == 'Wilson'))

# Use .loc and the filter to select for rides
print(ridership_cal_stations.loc[filter_criteria, 'rides'].sum())
```

EXERCISE 2
```python 
# Merge licenses and zip_demo, on zip; and merge the wards on ward
licenses_zip_ward = licenses.merge(zip_demo, on='zip') \
            			.merge(wards, on='ward')

# Print the results by alderman and show median income
print(licenses_zip_ward.groupby('alderman').agg({'income':'median'}))
```

EXERCISE 3
```python 
# Merge land_use and census and merge result with licenses including suffixes
land_cen_lic = land_use.merge(census, on='ward') \
                    .merge(licenses, on='ward', suffixes=('_cen','_lic'))

# Group by ward, pop_2010, and vacant, then count the # of accounts
pop_vac_lic = land_cen_lic.groupby(['ward','pop_2010','vacant'], 
                                   as_index=False).agg({'account':'count'})

# Sort pop_vac_lic and print the results
sorted_pop_vac_lic = pop_vac_lic.sort_values(['vacant', 'account', 'pop_2010'], 
                                             ascending=[False, True, True])

# Print the top few rows of sorted_pop_vac_lic
print(sorted_pop_vac_lic.head())
```
