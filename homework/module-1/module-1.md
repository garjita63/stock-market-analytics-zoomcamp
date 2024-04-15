
## Question 1: [Macro] Average growth of GDP in 2023

What is the average growth (in %) of GDP in 2023?

Download the timeseries Real Gross Domestic Product (GDPC1) from FRED (https://fred.stlouisfed.org/series/GDPC1). Calculate year-over-year (YoY) growth rate (that is, divide current value to one 4 quarters ago). Find the average YoY growth in 2023 (average from 4 YoY numbers). Round to 1 digit after the decimal point: e.g. if you get 5.66% growth => you should answer 5.7

### Answer 1 : 

![image](https://github.com/garjita63/stock-market-course/assets/77673886/e38a94e3-6615-4d67-a558-3e599c51af2c)

![image](https://github.com/garjita63/stock-market-course/assets/77673886/c4ed10d0-9ed9-4479-babd-6c2d7fc7c33e)


## Question 2. [Macro] Inverse "Treasury Yield"

Find the min value of (dgs10-dgs2) after since year 2000 (2000-01-01) and write it down as an answer, round to 1 digit after the decimal point.

Download DGS2 and DGS10 interest rates series (https://fred.stlouisfed.org/series/DGS2, https://fred.stlouisfed.org/series/DGS10). Join them together to one dataframe on date (you might need to read about pandas.DataFrame.join()), calculate the difference dgs10-dgs2 daily.

(Additional: think about what does the "inverted yield curve" mean for the market and investors? do you see the same thing in your country/market of interest? Do you think it can be a good predictive feature for the models?)


### Answer 2 :

![image](https://github.com/garjita63/stock-market-course/assets/77673886/971a1cb0-08e3-4a4d-9f36-969b33001f3f)

![image](https://github.com/garjita63/stock-market-course/assets/77673886/20a083ee-030f-4e06-944d-b636e6451aca)



