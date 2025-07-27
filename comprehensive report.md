# Uber Fares Dataset Analysis – Comprehensive Report

# Uber Fares Analysis Report

## 1. Introduction  
This project explores and analyzes the Uber Fares dataset using Python for preprocessing and Power BI for visualization. The goal is to uncover insights into ride fares, time-based patterns, geographic trends, and to develop an interactive dashboard.

---

## 2. Methodology  

### 2.1 Data Source  
- **Dataset**: Uber Fares Dataset on Kaggle  
- **Tools Used**: Python (for data cleaning and feature engineering), Power BI Desktop (for visualization)  

### 2.2 Data Loading and Initial Exploration  
- Loaded dataset using `pandas`.  
- Checked structure with `.info()` and `.head()`.  

![](/images/data.png)

---

## 3. Data Cleaning  

### 3.1 Handling Missing & Invalid Values  
- Removed rows with missing or invalid values.  using `.isnull().sum()` 

 

### 3.2 Saving Cleaned Data  
- Exported cleaned data to CSV for Power BI.  

 

---

## 4. Exploratory Data Analysis (EDA)  

### 4.1 Descriptive Statistics  
- Analyzed mean, median, mode, standard deviation, and quartiles.  

*(Screenshot: Summary statistics.)*  

### 4.2 Fare Distribution  
- Visualized fare distribution using histograms or boxplots.  

*(Screenshot: Fare histogram or boxplot.)*  

### 4.3 Relationship Analysis  
- Explored relationships like fare vs. distance or fare vs. hour.  

*(Screenshot: Scatter plots or line charts.)*  

---

## 5. Feature Engineering  

### 5.1 Extracting Date-Time Features  
- Created features: `hour`, `day`, `month`, `day_of_week`, `is_peak_hour`.  
 

### 5.2 Exporting for Power BI  
- Exported enhanced dataset as `enhanced_uber.csv`.  



---

## 6. Power BI Visualizations  

### 6.1 Data Import  
- Loaded cleaned and enhanced data into Power BI.  

*(Screenshot: Data loaded in Power BI.)*  

### 6.2 Charts Created  
- **Visualizations**: Fare distribution, monthly ride volume, hourly patterns, geospatial maps.  


---

## 7. Power BI Dashboard 

  ![](/images/powerbi.png)

### 7.1 Layout  
- **Features**: Interactive filters, time series analysis, geospatial plots.  

*

---

## 8. Results and Insights  

**Key Discoveries**:  
- Peak hours: Evenings (5–7 PM) and weekends (Friday–Sunday).  
- Busiest location: Manhattan hotspots.  

---

## 9. Conclusion  
Combined Python and Power BI to extract and visualize insights effectively.  

---

## 10. Recommendations  
- Apply surge pricing during peak hours.  
- Offer promotions on off-peak days.  
- Expand service to underserved regions.  




**Features in the Dataset:**
- `fare_amount`: Total fare charged (USD)
- `pickup_datetime`: Date and time of pickup
- `pickup_longitude`, `pickup_latitude`: Pickup GPS coordinates
- `dropoff_longitude`, `dropoff_latitude`: Dropoff GPS coordinates
- `passenger_count`: Number of passengers per trip
- `key`: Unique ride identifier

---

##  Data Cleaning Methodology

Cleaning steps were conducted in **Python (Pandas)**:

1. **Missing Values**
   - Dropped rows where `dropoff_longitude` or `dropoff_latitude` were null.

2. **Invalid Values**
   - Removed entries where:
     - `fare_amount` was negative or zero
     - `passenger_count` was zero or above six
     - Coordinates were outside the realistic NYC bounds

3. **Datetime Conversion**
   - Converted `pickup_datetime` to datetime format
   - Extracted additional fields: `hour`, `day`, `month`, `day_of_week`

4. **Export**
   - Cleaned data saved as `cleaned_uber.csv`
   - Enhanced data (with new features) saved as `enhanced_uber.csv`

---

##  Key Visualizations (Power BI)

Data visualized in **Power BI Desktop**, highlighting:

### 1. Fare Distribution
- **Histogram** and **boxplot** of fare values
- Skewed distribution with several outliers

### 2. Fare vs Hour of Day
- Line chart showing higher fares during evening rush hours

### 3. Passenger Count Breakdown
- Bar chart showing majority of rides had 1 or 2 passengers

### 4. Geographic Mapping
- Pickup and dropoff points visualized on an NYC map
- High concentration in Manhattan

### 5. Temporal Trends
- Ride frequency by hour, day of the week, and month
- Interactive slicers for exploration

---

## Insights and Outcomes

### Temporal Patterns
- **Peak hours:** 5–8 PM on weekdays
- **Busy days:** Fridays and weekends

### Fare Patterns
- Higher fares observed during peak hours and weekends
- Majority of fares ranged between $5 and $15

### Spatial Insights
- Most common ride origin and destination: **Manhattan**
- Less activity in boroughs like Staten Island

### Passenger Trends
- Over 60% of rides had 1 passenger
- Group rides (4–6 passengers) were rare

### Recommendations
- Introduce **surge pricing** during peak evening hours
- Offer **discounts during off-peak** to increase usage
- Expand service coverage in **low-traffic areas**
