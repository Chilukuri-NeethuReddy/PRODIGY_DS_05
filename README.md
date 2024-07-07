# PRODIGY_DS_05

##ProdigyInfoTech_TASK5

##TASK 5: Analyzing Traffic Accident Data
This project analyzes traffic accident data to identify patterns related to road conditions, weather, and time of day, and visualizes accident hotspots and contributing factors.


##Dataset:
The dataset used in this project is the RTA Dataset, containing information about traffic accidents.


##Steps:
1.Data Loading: Load the dataset and explore its structure.

2.Data Preprocessing: Convert time columns to datetime format and explore basic information about the dataset

3.Visualization: Visualize accidents by road surface conditions, weather conditions, time of day, and accident severity.

4.Correlation Analysis: Perform correlation analysis for numerical variables.

5.Summary Visualization: Display a pie chart of accident severity distribution.



##How to Run:

1.Clone the repository.

2.Ensure you have the necessary libraries installed (pandas, matplotlib, seaborn, folium).

3.Place the dataset (RTA Dataset.csv) in the same directory as the script.

4.Run the script (traffic_accident_analysis.py) to analyze and visualize the data.



##Code

```python

import pandas as pd

import matplotlib.pyplot as plt

import seaborn as sns

from IPython.display import display

# Load the dataset

data = pd.read_csv('RTA Dataset.csv')

# Convert time column to datetime format

data['Time'] = pd.to_datetime(data['Time'], format='%H:%M:%S').dt.time

# Display basic info about the dataset

print(data.info())

display(data.head())
```

![Screenshot 2024-07-07 112131](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_05/assets/174725064/8084315d-f47a-4aad-8a0c-815adc62005a)

![Screenshot 2024-07-07 112152](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_05/assets/174725064/2b55e88e-9092-4ed7-a217-eb3fa40d6dfc)

```python
sns.set(style="whitegrid")

# Create the bar plot for accidents by road conditions

plt.figure(figsize=(12, 6))

sns.countplot(y='Road_surface_conditions', data=data, palette='viridis')

plt.title('Accidents by Road Surface Conditions')

plt.xlabel('Count')

plt.ylabel('Road Surface Conditions')

plt.show()
```


![Screenshot 2024-07-07 112421](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_05/assets/174725064/8aba63a8-2a87-49ad-9008-9c589b9ef744)

```python

# Create the bar plot for accidents by weather conditions

plt.figure(figsize=(12, 6))

sns.countplot(y='Weather_conditions', data=data, palette='coolwarm')

plt.title('Accidents by Weather Conditions')

plt.xlabel('Count')

plt.ylabel('Weather Conditions')

plt.show()

```

![Screenshot 2024-07-07 112523](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_05/assets/174725064/8cbef780-9da8-4ed6-830c-6fe58d31b318)

```python

# Create the bar plot for accidents by time of day

plt.figure(figsize=(12, 6))

sns.histplot(data['Time'], bins=24, kde=True, color='red')

plt.title('Accidents by Time of Day')

plt.xlabel('Time')

plt.ylabel('Frequency')

plt.show()
```

![Screenshot 2024-07-07 112618](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_05/assets/174725064/60746d6a-93ec-4fc6-8c1e-3acefbf81b48)

```python
# Selecting numerical columns for correlation analysis
df_num = data.select_dtypes(include=['int64', 'float64'])

# Heatmap of correlation matrix for numerical columns
plt.figure(figsize=(15, 9))
sns.heatmap(df_num.corr(), annot=True, cmap=sns.diverging_palette(240, 10, n=9, center="light"))
plt.title('Correlation Matrix of Numerical Variables')
plt.show()
```

![Screenshot 2024-07-07 113002](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_05/assets/174725064/9f43d3e8-877e-43dc-b3e9-d59782b6e939)

```python
# Pie chart of accident severity
accidents_severity = data['Accident_severity'].value_counts()

fig, ax = plt.subplots(figsize=(8, 6), subplot_kw=dict(aspect="equal"))
labels = accidents_severity.index
sizes = accidents_severity.values
colors = ['red', 'green', 'pink']  # Define colors here
ax.pie(sizes, labels=labels, colors=colors, autopct='%1.1f%%', pctdistance=0.85)
circle = plt.Circle((0, 0), 0.5, color='white')
p = plt.gcf()
p.gca().add_artist(circle)
ax.set_title("Accident by Severity", fontdict={'fontsize': 16})
plt.tight_layout()
plt.show()
```

![Screenshot 2024-07-07 113044](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_05/assets/174725064/a7d0fdb9-6652-4716-b327-a2f6068118fd)








