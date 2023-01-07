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

**Multiple Parameters and Return Values**

Multiple Function Parameters

lebih dari 1 parameter ataupun nilai 

```python 
def raise_to_power(value1, value 2): 
    new_value = value1**value2
    return new_value 
#call function 
result = raise_to_power(2,3)
print(result)
```

**A quick Jump into Tuples**

make function return multiple with **Tuples**

Tuples : Like a list (can contain multiple values), immutable (tidak bisa dimodif), strukturnya menggunakan ()

**Unpacking Tuples**

```python 
even_nums = (2,4,6) 
a,b,c = even_nums
```

**Returning multiple values**

```python 
def raise_to_power(value1, value 2): 
    new_value = value1**value2
    return new_value 
#call function 
result = raise_to_power(2,3)
print(result)
```

```python 
def raise_both(value1, value2):
  new_value1 = value1**value2
  new_value2 = value2**value1
  
  new_tuple = (new_value1, new_value2)
  
  return new_tuple

result = raise_both(2,3)

print(result)
```






