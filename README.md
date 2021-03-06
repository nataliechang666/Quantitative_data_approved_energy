# Weather Normolization

- Data processing and data analysis
- Prediction Model 1. Linear Regression 2. lightGBM Regressor
- Conclusion 2020 vs 2021

# Data processing and data analysis
First, we download the Histoircal load data from NYISO between 2020/01/01 to 2020/12/31 in N.Y.C and Historical weather in NOAA with same time period. Since NYISO data reports 5-min interval and NOAA data is hour interval, we combine it to the same hourly time and finally gets 11579 rows. Second, we clean the data by reducing it to remaining "date", "source", "backup" data and "hourly" data with total 27 columns. We fill in the 0 for missing value and using label encoding in category columns like "BackupElements" or "BackupEquipment". Also, we find that there are some inconsistent recording problems like some records include "s" after the time column or "V" after visibility column. Thus, we delete them out.

For the data analysis part, we can see that actual load is highest in the summer and least in the spring and fall from this figure. This result is not difficult to imagine, because the summer heat requires more electricity to dissipate heat.

<img src="Load_Time.png" alt="Cover" width="50%"/>

The correlation plot shows that the temperature of "HourlyDryBulb", "HourlyWetBulb", "HourlyDewPoint" has positive correlation to the Actual Load.

<img src="correlation.png" alt="Cover" width="50%"/>

# Prediction Model
We use 80% data for training and 20% for testing. The linear regression gets around 0.22 R squared accuracy. It is low and we can say it is because there are not linear between features and label. Next, we uses lightGBM Regressor and after parameter tuning, we get around 0.74 R squared accuracy.

The feature important shows "HourlyAltimeterSetting" is the most important column in lightGBM model.

# Conclusion 2020 vs 2021

<img src="2020vs2021.png" alt="Cover" width="50%"/>


