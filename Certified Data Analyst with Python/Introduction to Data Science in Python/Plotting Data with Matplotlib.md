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

**Styling Graphs**

Changing Line Color 

<img width="197" alt="2022-07-23_11h22_00" src="https://user-images.githubusercontent.com/87213160/180590251-cb9f595d-2d56-434f-9b79-1888a5ea35fe.png">

Changing Line Width

<img width="203" alt="2022-07-23_11h23_04" src="https://user-images.githubusercontent.com/87213160/180590270-d82578c7-f2f5-45f6-8564-de160f788d87.png">

Changing Line Style 

<img width="220" alt="2022-07-23_11h23_34" src="https://user-images.githubusercontent.com/87213160/180590280-e762d4f9-7863-4059-96f6-4cfcaf49c301.png">

Adding Marker

<img width="363" alt="2022-07-23_11h24_42" src="https://user-images.githubusercontent.com/87213160/180590295-6d4ace2c-08d6-4a94-bf05-cbe535c015c2.png">

Setting a Style 

<img width="364" alt="2022-07-23_11h26_19" src="https://user-images.githubusercontent.com/87213160/180590333-c673e570-6a9a-4630-92c8-80d3f2bb0142.png">

```python
# Change the color of Phoenix to `"DarkCyan"`
plt.plot(data["Year"], data["Phoenix Police Dept"], label="Phoenix", color="DarkCyan")

# Make the Los Angeles line dotted
plt.plot(data["Year"], data["Los Angeles Police Dept"], label="Los Angeles", linestyle=":")

# Add square markers to Philedelphia
plt.plot(data["Year"], data["Philadelphia Police Dept"], label="Philadelphia", marker="s")

# Add a legend
plt.legend()

# Display the plot
plt.show()
```
<img width="739" alt="2022-07-23_11h29_39" src="https://user-images.githubusercontent.com/87213160/180590389-dd97c493-0547-492e-97f9-a9103daf63f3.png">

```python
# Change the style to fivethirtyeight
plt.style.use('fivethirtyeight')

# Plot lines
plt.plot(data["Year"], data["Phoenix Police Dept"], label="Phoenix")
plt.plot(data["Year"], data["Los Angeles Police Dept"], label="Los Angeles")
plt.plot(data["Year"], data["Philadelphia Police Dept"], label="Philadelphia")

# Add a legend
plt.legend()

# Display the plot
plt.show()
```
```python
# Change the style to ggplot
plt.style.use('ggplot')

# Plot lines
plt.plot(data["Year"], data["Phoenix Police Dept"], label="Phoenix")
plt.plot(data["Year"], data["Los Angeles Police Dept"], label="Los Angeles")
plt.plot(data["Year"], data["Philadelphia Police Dept"], label="Philadelphia")

# Add a legend
plt.legend()

# Display the plot
plt.show()
```

```python
# x should be ransom.letter and y should be ransom.frequency
plt.plot(ransom.letter, ransom.frequency,
         # Label should be "Ransom"
         label="Ransom",
         # Plot the ransom letter as a dotted gray line
         linestyle=':', color='gray')

# Display the plot
plt.show()
```
<img width="457" alt="2022-07-23_11h34_44" src="https://user-images.githubusercontent.com/87213160/180590497-f91e54a1-3991-4214-87cc-8381b67c240f.png">

```python 
# Plot each line
plt.plot(ransom.letter, ransom.frequency,
         label='Ransom', linestyle=':', color='gray')
plt.plot(suspect1.letter, suspect1.frequency, label='Fred Frequentist')
plt.plot(suspect2.letter, suspect2.frequency, label='Gertrude Cox')

# Add x- and y-labels
plt.xlabel("Letter")
plt.ylabel("Frequency")

# Add a legend
plt.legend()

# Display plot
plt.show()
```
<img width="447" alt="2022-07-23_11h37_43" src="https://user-images.githubusercontent.com/87213160/180590572-6ba7fd4c-3ce7-446e-abb0-65c06c6df8bc.png">

