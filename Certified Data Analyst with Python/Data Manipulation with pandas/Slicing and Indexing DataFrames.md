# Slicing and Indexing DataFrames

**Explisit Indexes**
Setting a column as index
```python 
dogs_ind = dogs.set_index("name")
print(dogs_ind)
```
Removing Index 
```python 
dogs_ind.reset_index(drop=True)
```
indexes make subsetting simpler. 
```python
dogs[dogs["name"].isin(["Bella", "Stella"])]
#atau 
dogs_ind.loc[["Bella", "Stella"]]
```
multiple column in indexes
```python 
dogs1= dogs.set_index(["Breed", "color"])
print(dogs1)
```
Subset inner levels with a list of tuples
```python 
dogs_ind3.loc[[("Labrador", "Brown"), ("Chihuahua", "Tan")]]
```
<img width="422" alt="2022-07-28_20h39_23" src="https://user-images.githubusercontent.com/87213160/181519356-ed24a4eb-b51e-46e1-bf2c-d9a995704ef4.png">

Sorting by index values 
```python 
dogs_ind3.sort_index()
```
Controlling sort_index
```python 
dogs_ind3.sort_index(level=["color", "breed"], ascending=[True, False])
```
<img width="259" alt="2022-07-28_20h41_37" src="https://user-images.githubusercontent.com/87213160/181519839-8bc47720-a9ab-4b40-99f4-59b47d4cc80d.png">

