
## Question 1: [Macro] Average growth of GDP in 2023

What is the average growth (in %) of GDP in 2023?

Download the timeseries Real Gross Domestic Product (GDPC1) from FRED (https://fred.stlouisfed.org/series/GDPC1). Calculate year-over-year (YoY) growth rate (that is, divide current value to one 4 quarters ago). Find the average YoY growth in 2023 (average from 4 YoY numbers). Round to 1 digit after the decimal point: e.g. if you get 5.66% growth => you should answer 5.7

### Answer 1 : 
```
import pandas as pd

# Read dataset
df = pd.read_csv("GDPC1.csv")

# Assuming your dataframe is named df
# Convert DATE column to datetime if it's not already in datetime format
df['DATE'] = pd.to_datetime(df['DATE'])

# Shift GDPC1 column by 4 rows to get value from one year ago
df['GDPC1_one_year_ago'] = df['GDPC1'].shift(4)

# Calculate YoY growth rate
df['YoY_growth'] = df['GDPC1'] / df['GDPC1_one_year_ago'] - 1

# Filter dataframe to include only rows from 2023
df_2023 = df[df['DATE'].dt.year == 2023]

# Calculate average YoY growth rate for 2023
average_YoY_growth_2023 = df_2023['YoY_growth'].mean()

# Round to 1 decimal point
average_YoY_growth_2023_rounded = round(average_YoY_growth_2023 * 100, 1)

print("Average YoY growth rate in 2023: {}%".format(average_YoY_growth_2023_rounded))

```
![image](https://github.com/garjita63/stock-market-course/assets/77673886/e38a94e3-6615-4d67-a558-3e599c51af2c)


