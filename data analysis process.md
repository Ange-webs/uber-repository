Here are the steps to clean the uber dataset
first import panda
```python
import pandas as pd
```
loading data
```python
data= pd.read_csv("uber.csv")
```
displaying data iin  the  dataset
```python
data
```
output 
![](/images/data.png)
checking null values in dataset
```python
data.isna()
```
![](/images/dropping_null.png)

Removing Duplicates
```python
data.drop_duplicates
```

Output
![](/images/dropping_duplicates.png)

CALCULATIONS

Calculating mean fareb amount
```python
fare_age = data['fare_amount'].mean()
print("fare_amount mean:", fare_age)****
```
Output
![](/images/mean.png)

Calculating median
```python
data = pd.DataFrame(data)

print("Median fare_amount:", data['fare_amount'].median())  
```
Output
![](/images/median.png)
CAlculating Mode
```python
print("mode =", data['fare_amount'].mode())
```
Output
![](/images/mode.png)
Calculating standard deviation
```python
print("Std Dev of Age:", data['fare_amount'].std())
```
Output
![](/images/std_deviation.png)
Calculating percentiles
```python

print("25th percentile (Q1):", data['fare_amount'].quantile(0.25))
print("50th percentile (Median):", data['fare_amount'].quantile(0.5))
print("75th percentile (Q3):", data['fare_amount'].quantile(0.75))
```
Output
![](/images/quartiles.png)
Calculatinng Range
```python
range_value = data['fare_amount'].max() - data['fare_amount'].min()
print("Range of fare amount:", range_value)
```
Output
![](/images/range.png)
Calculating outliers
```python
Q1 = data['fare_amount'].quantile(0.25)
Q3 = data['fare_amount'].quantile(0.75)
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers = data[(data['fare_amount'] < lower_bound) | (data['fare_amount'] > upper_bound)]
print("Outliers:\n", outliers)
```
Output
![](/images/outliers.png)
Plotting box plot
```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.boxplot(x=data['fare_amount'])
plt.show()
```
Output
![](/images/boxplot.png)

Getting ready to plot
```python
import numpy as np

def haversine(lat1, lon1, lat2, lon2):
    # Convert to radians
    lat1, lon1, lat2, lon2 = map(np.radians, [lat1, lon1, lat2, lon2])
    R = 6371  # Earth radius in km
    dlat = lat2 - lat1
    dlon = lon2 - lon1
    a = np.sin(dlat/2)*2 + np.cos(lat1)*np.cos(lat2)*np.sin(dlon/2)*2
    c = 2 * np.arcsin(np.sqrt(a))
    return R * c
data['distance_km'] = haversine(
    data['pickup_latitude'], data['pickup_longitude'],
    data['dropoff_latitude'], data['dropoff_longitude']
)
data['pickup_datetime'] = pd.to_datetime(data['pickup_datetime'])
data['hour'] = data['pickup_datetime'].dt.hour
```
Fare amount vs Distance Plot
```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.scatterplot(x='distance_km', y='fare_amount', data=data, alpha=0.3)
plt.title('Fare Amount vs. Distance')
plt.xlabel('Distance Traveled (km)')
plt.ylabel('Fare Amount ($)')
plt.show()
```
Output
![](/images/fare_amount_vs_distance.png)
Average fare by hour day
```python
import matplotlib.pyplot as plt

avg_fare_by_hour = data.groupby('hour')['fare_amount'].mean().sort_index()

plt.figure(figsize=(10, 6))
plt.plot(avg_fare_by_hour.index, avg_fare_by_hour.values, marker='o', color='teal')
plt.title('Average Fare by Hour of Day')
plt.xlabel('Hour of Day')
plt.ylabel('Average Fare Amount ($)')
plt.xticks(range(0, 24))
plt.grid(True)
plt.tight_layout()
plt.show()
```
Output 
![](/images/average_fare_by_hour_day.png)
Adding additional columns
```python
data['pickup_datetime'] = pd.to_datetime(data['pickup_datetime'])
data['hour'] = data['pickup_datetime'].dt.hour
data['day'] = data['pickup_datetime'].dt.day
data['month'] = data['pickup_datetime'].dt.month
data['day_of_week'] = data['pickup_datetime'].dt.day_name()
print(data[['pickup_datetime', 'hour', 'day', 'month', 'day_of_week']].head())
```
Output

![](/images/adding_colums.png)
Peak status check
```python
def peak_status(hour):
    if 7 <= hour <= 9 or 16 <= hour <= 19:
        return "Peak"
    else:
        return "Off-Peak"
data['peak_status'] = data['hour'].apply(peak_status)
print(data[['hour', 'peak_status']].head(10))
```
Output
![](/images/peak_status.png)
ADding another column 
```python
data['day_of_week'] = pd.Categorical(data['day_of_week'],
                                   categories=['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'],
 ordered=True)
```

SAving the new dleaned data
```python
data.to_csv('uber_enhanced.csv', index=False)
print(" File 'uber_enhanced.csv' saved successfully.")
```
Output
![](/images/saving.png)





