# Python Data Science Toolbox (Part 1)

**Write your Own Function**

str() #untuk mengembalikan ke string 
```python 
x = str(5) 

print(x)

#untuk mengetahui tipe datanya dapat menggunakan 
print(type(x))
``` 

**Defining Function in Python**

```python 
def square():   #function header 
  new_value = 4**2  #function body 
  print(new_value)
  
square() #cara buat manggil functionnya
```

**Function Parameter**
```python 
def square(value):   #function header 
  new_value = value**2  #function body 
  print(new_value)
  
square(4) #cara buat manggil functionnya maka akan menghasilkan 16. nilai value dapat diubah-ubah
```

**Return values from functions**
```python 
def square(value):   #function header 
  new_value = value**2  #function body 
  return new_value
num = square(4)

print(num)
```
**Docstring**

digunakan untuk mendeskripsikan fungsi yang telah dilakukan. 


