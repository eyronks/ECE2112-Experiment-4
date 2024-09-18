# ECE2112 Programming Problems

This repository contains Python scripts for solving various programming problems in ECE2112. The problems are focused on the use of Data Wrangling and Data Visualization. Below are the details of each script included in this repository:

<br/> 

## Objectives of the Experiment 

  1. To identify the codes and functions needed in cleaning and visualizing data.
  
  2. To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization.

<br/> 

## ECE Board Exam Problem

Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.


**Import the necessary libraries for the script**

```python
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
```

**Function:** These libraries are essential to solve the problem because they provide the necessary tools for data manipulation, analysis, and visualization, as well as enhancing the aesthetics of the printed data frames.

<br/> 

**This section reads the data from an Excel file named boards2.xlsx into a Pandas Data Frame object called df.**

```python
# Read data from Excel file
data = pd.read_excel('board2.xlsx')
```

**Function:** This line of code is essential because it loads the data from the Excel file into a format that can be easily manipulated and analyzed using Pandas.

<br/> 

**Create the following data frames based on the format provided:** *Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon*

```python
# Create the required data frame for Instrumentation
Instru = data[(data['Track'] == 'Instrumentation') & (data['Hometown'] == 'Luzon') & (data['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]
Instru
```

**Output:**

![image](https://github.com/user-attachments/assets/8a0d0c96-7b1e-4881-a6a0-802407c9af86)

**Function:** This code creates a new data frame Instru that filters the original data to include only rows where the Track is 'Instrumentation', Hometown is 'Luzon', and Electronics score is greater than 70. It then selects only the Name, GEAS, and Electronics columns from the filtered data. Finally, it prints the resulting data frame in a visually appealing format using the tabulate library, with a fancy grid table format.

<br/> 

**Create a column to compute for the 'Average' in the data frame.**

```python
# Create a new column 'Average' in the original data frame
data['Average'] = data[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
```

**Function:** This line of code creates a new column called Average in Mindy's original data. The values in this new column are calculated by taking the mean of the Math, Electronics, GEAS, and Communication columns for each row, effectively computing the average score across these four subjects.

<br/> 

**Create the following data frames based on the format provided:** *Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female*

```python
# Create the required data frame for Mindy
Mindy = data.loc[(data['Hometown'] == 'Mindanao') & (data['Gender'] == 'Female') & (data['Average'] >= 55), ['Name', 'Track', 'Electronics', 'Average']]
Mindy
```

**Output:**

![image](https://github.com/user-attachments/assets/63ce6af9-ce3a-454d-92bf-1f0204ecb16d)

**Function:** The code creates a new DataFrame called Mindy by filtering the original data frame data based on two conditions: the Hometown must be 'Mindanao' and the Gender must be 'Female'. This filtered DataFrame is then further refined to only include rows where the Average score is 55 or higher. The resulting DataFrame Mindy only includes four columns: Name, Track, Electronics, and Average. Finally, the code prints the filtered data frame in a formatted table using the tabulate function, making it easy to visualize and understand the data.

<br/> 

**Create a visualization that shows how the different features contributes to average grade.**

```python
# Calculate the average grade for each feature
track_avg = data.groupby('Track')['Average'].mean()
gender_avg = data.groupby('Gender')['Average'].mean()
hometown_avg = data.groupby('Hometown')['Average'].mean()

# Create a figure and axis
fig, ax = plt.subplots(1, 3, figsize=(15, 5))

# Plot the average grades for each track
ax[0].bar(track_avg.index, track_avg.values)
ax[0].set_title('Average Grade by Track')
ax[0].set_xlabel('Track')
ax[0].set_ylabel('Average Grade')

# Plot the average grades for each gender
ax[1].bar(gender_avg.index, gender_avg.values)
ax[1].set_title('Average Grade by Gender')
ax[1].set_xlabel('Gender')
ax[1].set_ylabel('Average Grade')

# Plot the average grades for each hometown
ax[2].bar(hometown_avg.index, hometown_avg.values)
ax[2].set_title('Average Grade by Hometown')
ax[2].set_xlabel('Hometown')
ax[2].set_ylabel('Average Grade')

# Show the plot
plt.tight_layout()
plt.show()
```

**Output:**

![image](https://github.com/user-attachments/assets/29100826-44d5-42f5-823a-683889595537)

**Function:** This code calculates the average grade for each feature (Track, Gender, and Hometown) and visualizes the results using bar plots. It first calculates the average grades using the groupby and mean functions. Then, it creates a figure with three subplots, each displaying the average grades for one feature. The plots are customized with titles, labels, and a layout to facilitate easy comparison of the average grades across different features.

<br/>

## Discussion 

The given code solves the problem by following a structured approach. It begins by importing the necessary libraries, pandas and matplotlib, and reading the data from an Excel file using pd.read_excel. The code then filters the data to create two data frames, Instru and Mindy, based on specific conditions. Additionally, a new column 'Average' is created in the original data frame by calculating the mean of four features: Math, Electronics, GEAS, and Communication.


The code then proceeds to calculate the average grades for each feature using groupby and mean functions. This is followed by the creation of three bar plots using matplotlib to visualize the average grades for each track, gender, and hometown. The plots provide a clear and concise representation of the data insights, enabling effective analysis and comparison of the average grades across different categories.


Overall, the code demonstrates effective data filtering and feature engineering techniques using Pandas, and the use of groupby and mean functions enables efficient calculation of average grades for each feature. The visualization of results using matplotlib provides a comprehensive solution to the problem, making it easy to understand and interpret the data insights.

<br/>

##

**Author:** Aaron Chastine V. Villajin

**Submitted to:** Engr. Ma. Madecheen S. Pangaliman, M.Sc.
