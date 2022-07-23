# Different Types of Plots

**Making a scatter plot**

```python 
plt.scatter(df.x, df.y)
plt.show()
```
<img width="361" alt="2022-07-23_11h54_36" src="https://user-images.githubusercontent.com/87213160/180591020-b507ac65-f241-48bd-8921-59f7b8ba792a.png">

jika ingin membuat scatter plot yang transpharan, maka memakai alpha. 
alpha itu hanya menerima angka dengan rentang 0 hingga 1. 

<img width="365" alt="2022-07-23_11h55_53" src="https://user-images.githubusercontent.com/87213160/180591039-2e5d8645-40e4-48d3-b7de-89f28e7caf46.png">

exercise 
```python 
# Explore the data
print(cellphone.head())

# Create a scatter plot of the data from the DataFrame cellphone
plt.scatter(cellphone.x, cellphone.y)

# Add labels
plt.ylabel('Latitude')
plt.xlabel('Longitude')

# Display the plot
plt.show()
```
exercise : change the color to red 

```python
# Change the marker color to red
plt.scatter(cellphone.x, cellphone.y,
           color="red")

# Add labels
plt.ylabel('Latitude')
plt.xlabel('Longitude')

# Display the plot
plt.show()
```

exercise : change the marker into square 
```python
# Change the marker shape to square
plt.scatter(cellphone.x, cellphone.y,
           color='red',
           marker='s')

# Add labels
plt.ylabel('Latitude')
plt.xlabel('Longitude')

# Display the plot
plt.show()
```

exercise : change the transparency into 0.1 
```python
# Change the transparency to 0.1
plt.scatter(cellphone.x, cellphone.y,
           color='red',
           marker='s',
           alpha=0.1)

# Add labels
plt.ylabel('Latitude')
plt.xlabel('Longitude')

# Display the plot
plt.show()
```
**Making a Bar Chart**
<img width="368" alt="2022-07-23_12h03_29" src="https://user-images.githubusercontent.com/87213160/180591165-7850431a-c176-4670-a391-e1fa0d7e9efe.png">

Horizontal Bar Chart 

<img width="374" alt="2022-07-23_12h03_47" src="https://user-images.githubusercontent.com/87213160/180591173-e962912f-5bec-4ddd-bca6-42abad671754.png">

Stacked Bar Chart 

<img width="356" alt="2022-07-23_12h05_58" src="https://user-images.githubusercontent.com/87213160/180591236-c2b23d87-4b18-4ef7-96af-dc1d96ab83f2.png">

<img width="309" alt="2022-07-23_12h06_24" src="https://user-images.githubusercontent.com/87213160/180591247-ef7ee7a5-16d4-4e7a-b4c4-a7189d7e4c62.png">

Exercise : Create a bar chart of the column avg_hours_worked for each officer from the DataFrame hours.
```python
# Display the DataFrame hours using print
print(hours)

# Create a bar plot from the DataFrame hours
plt.bar(hours.avg_hours_worked, hours.officer)

# Display the plot
plt.show()
```

add error 
```python
# Display the DataFrame hours using print
print(hours)

# Create a bar plot from the DataFrame hours
plt.bar(hours.officer, hours.avg_hours_worked,
        # Add error bars
        yerr=hours.std_hours_worked)

# Display the plot
plt.show()
```

```python 
# Plot the number of hours spent on desk work
plt.bar(hours.officer, hours.desk_work, label='Desk Work')

# Plot the hours spent on field work on top of desk work
plt.bar(hours.officer, hours.field_work, bottom=hours.desk_work, label="Field Work")

# Add a legend
plt.legend()

# Display the plot
plt.show()
```

<img width="462" alt="2022-07-23_12h19_05" src="https://user-images.githubusercontent.com/87213160/180591636-aa9d3ce3-1606-4e5c-b94c-cff6a0b1863a.png">

**Making Histogram**

```python 
plt.hist(gravel.mass)
plt.show()
```

changing bins. 
```python 
plt.hist(gravel.mass, bins=10)
plt.show()
```

changing range 
```python 
plt.hist(gravel.mass, range=(xmin, xmax))
plt.show()
```

Normalizing

<img width="363" alt="2022-07-23_12h24_40" src="https://user-images.githubusercontent.com/87213160/180591744-f966119e-e245-4e61-8e39-971034feb181.png">

Exercise 
```python 
# Create a histogram
plt.hist(gravel.radius,
         bins=40,
         range=(2, 8),
         density=True)

# Label plot
plt.xlabel('Gravel Radius (mm)')
plt.ylabel('Frequency')
plt.title('Sample from Shoeprint')

# Display histogram
plt.show()
```

<img width="447" alt="2022-07-23_13h10_29" src="https://user-images.githubusercontent.com/87213160/180592912-d3dd6a42-1b99-4568-9f69-2c66aa7b78da.png">


