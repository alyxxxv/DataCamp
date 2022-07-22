# Plotting Data with Matplotlib

import matplotlib 

```python
from matplotlib import pyplot as plt
```

```python 
plt.plot(x_values, y_values)
plt.show()
```
<img width="381" alt="2022-07-22_21h09_03" src="https://user-images.githubusercontent.com/87213160/180456931-3e07d6ad-aa82-4683-be32-d698e83afc64.png">

<img width="361" alt="2022-07-22_21h10_30" src="https://user-images.githubusercontent.com/87213160/180457201-7fce66f9-79f8-42a7-8b9c-f3aa5c4c0943.png">

```python 
# From matplotlib, import pyplot under the alias plt
from matplotlib import pyplot as plt

# Plot Officer Deshaun's hours_worked vs. day_of_week
plt.plot(deshaun.day_of_week, deshaun.hours_worked)

# Display Deshaun's plot
plt.show()
```

```python
# Plot Officer Deshaun's hours_worked vs. day_of_week
plt.plot(deshaun.day_of_week, deshaun.hours_worked)

# Plot Officer Aditya's hours_worked vs. day_of_week
plt.plot(aditya.day_of_week, aditya.hours_worked)

# Plot Officer Mengfei's hours_worked vs. day_of_week
plt.plot(mengfei.day_of_week, mengfei.hours_worked)

# Display all three line plots
plt.show()
```

**Adding and Labels**

```python 
plt.xlabel("letter")
plt.ylabel("frequency")
plt.title("Judulnya apa yaaa")
plt.show()
```

adding legend

<img width="193" alt="2022-07-22_21h18_37" src="https://user-images.githubusercontent.com/87213160/180458848-131731b0-046a-4efd-9eda-a717238f4cf0.png">

arbitrary text 

<img width="369" alt="2022-07-22_21h19_16" src="https://user-images.githubusercontent.com/87213160/180458963-503bd4ce-7cdf-4a0c-a3d9-7e949cb7ad7a.png">

modify text

<img width="361" alt="2022-07-22_21h19_49" src="https://user-images.githubusercontent.com/87213160/180459057-f30e6140-be9a-433e-b6c6-dd7ba6faeddd.png">

```python
# Officer Deshaun
plt.plot(deshaun.day_of_week, deshaun.hours_worked, label='Deshaun')

# Add a label to Aditya's plot
plt.plot(aditya.day_of_week, aditya.hours_worked, label='Aditya')

# Add a label to Mengfei's plot
plt.plot(mengfei.day_of_week, mengfei.hours_worked, label='Mengfei')

# Add a command to make the legend display
plt.legend()

# Display plot
plt.show()
```
```python
# Lines
plt.plot(deshaun.day_of_week, deshaun.hours_worked, label='Deshaun')
plt.plot(aditya.day_of_week, aditya.hours_worked, label='Aditya')
plt.plot(mengfei.day_of_week, mengfei.hours_worked, label='Mengfei')

# Add a title
plt.title("Time Spent on Bayes Kidnapping")

# Add y-axis label
plt.ylabel("Hours Worked per Day")

# Legend
plt.legend()
# Display plot
plt.show()
```




