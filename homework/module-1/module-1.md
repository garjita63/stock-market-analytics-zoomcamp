
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


## Question 3. [Index] Which Index is better recently?

Compare S&P 500 and IPC Mexico indexes by the 5 year growth and write down the largest value as an answer (%)

Download on Yahoo Finance two daily index prices for S&P 500 (^GSPC, https://finance.yahoo.com/quote/%5EGSPC/) and IPC Mexico (^MXX, https://finance.yahoo.com/quote/%5EMXX/). Compare 5Y growth for both (between 2019-04-09 and 2024-04-09). Select the higher growing index and write down the growth in % (closest integer %). E.g. if ratio end/start was 2.0925 (or growth of 109.25%), you need to write down 109 as your answer.

(Additional: think of other indexes and try to download stats and compare the growth? Do create 10Y and 20Y growth stats. What is an average yearly growth rate (CAGR) for each of the indexes you select?)

### Answer 3 :

![image](https://github.com/garjita63/stock-market-course/assets/77673886/aaa761a5-30c8-451c-af32-7f93d1a4d1d0)

![image](https://github.com/garjita63/stock-market-course/assets/77673886/97c4be39-d9f7-4655-b0d2-44ed758fc963)


## Question 4. [Stocks OHLCV] 52-weeks range ratio (2023) for the selected stocks

Find the largest range ratio [=(max-min)/max] of Adj.Close prices in 2023

Download the 2023 daily OHLCV data on Yahoo Finance for top5 stocks on earnings (https://companiesmarketcap.com/most-profitable-companies/): 2222.SR,BRK-B, AAPL, MSFT, GOOG, JPM.

Here is the example data you should see in Pandas for "2222.SR": https://finance.yahoo.com/quote/2222.SR/history

Calculate maximum-minimim "Adj.Close" price for each stock and divide it by the maximum "Adj.Close" value. Round the result to two decimal places (e.g. 0.1575 will be 0.16)

(Additional: why this may be important for your research?)

Answer 4 :

![image](https://github.com/garjita63/stock-market-course/assets/77673886/73ac2641-919f-4f99-a7b1-c6cd0c8e712b)

![image](https://github.com/garjita63/stock-market-course/assets/77673886/a0b5605c-3109-4884-9d43-7cfc779a08c4)


## Question 5. [Stocks] Dividend Yield

Find the largest dividend yield for the same set of stocks

Use the same list of companies (2222.SR,BRK-B, AAPL, MSFT, GOOG, JPM) and download all dividends paid in 2023. You can use get_actions() method or .dividends field in yfinance library (https://github.com/ranaroussi/yfinance?tab=readme-ov-file#quick-start)

Sum up all dividends paid in 2023 per company and divide each value by the closing price (Adj.Close) at the last trading day of the year.

Find the maximm value in % and round to 1 digit after the decimal point. (E.g., if you obtained $1.25 dividends paid and the end year stock price is $100, the dividend yield is 1.25% -- and your answer should be equal to 1.3)

Answer 5 :

![image](https://github.com/garjita63/stock-market-course/assets/77673886/1ac792dd-c34d-4173-a1fd-b241c077e716)

![image](https://github.com/garjita63/stock-market-course/assets/77673886/aee3989c-e737-4aec-a1f8-ecf0f5bf4b24)


## Question 6. [Exploratory] Investigate new metrics

Free text answer

Download and explore a few additional metrics or time series that might be valuable for your project and write down why (briefly).

### Answer 6

For my project, I've decided to explore a few additional metrics that could provide valuable insights into the performance and behavior of the selected stocks. Here are the metrics I'll be investigating:

Price-to-Earnings Ratio (P/E Ratio): The P/E ratio is a fundamental valuation metric that compares a company's current stock price to its earnings per share (EPS). A low P/E ratio may indicate that a stock is undervalued, while a high P/E ratio may suggest that it's overvalued. Understanding the P/E ratio can provide insights into investor sentiment and market expectations for future earnings growth.

Price-to-Book Ratio (P/B Ratio): The P/B ratio compares a company's market capitalization to its book value. It's calculated by dividing the current market price per share by the book value per share. A low P/B ratio may indicate that a stock is undervalued relative to its book value, while a high P/B ratio may suggest that it's overvalued. Examining the P/B ratio can help assess a stock's valuation compared to its intrinsic value.

Return on Equity (ROE): ROE measures a company's profitability by comparing net income to shareholders' equity. It shows how effectively a company is using its equity to generate profits. A high ROE indicates that a company is efficiently utilizing shareholder funds, while a low ROE may suggest inefficiency or poor performance. Analyzing ROE can provide insights into a company's profitability and management effectiveness.

Volatility (Historical Volatility): Volatility measures the degree of variation in a stock's price over time. It's often expressed as the standard deviation of the stock's returns. High volatility stocks tend to have larger price swings, which may present both opportunities and risks for investors. Understanding historical volatility can help assess the riskiness of a stock and its potential for price fluctuations.

By exploring these additional metrics, I aim to gain a deeper understanding of the financial performance, valuation, and risk profile of the selected stocks. These insights will help me make more informed investment decisions and better assess the potential opportunities and risks associated with each stock.

Here's how I would technically explore the project using Python, pandas, and other relevant libraries:

Data Collection:

First, I would define the list of stocks to analyze. For this example, let's use the same list: ['2222.SR', 'BRK-B', 'AAPL', 'MSFT', 'GOOG', 'JPM']. I would then use the yfinance library to download historical OHLCV data for each stock, covering the desired time period. Data Preprocessing:

Once the data is downloaded, I would preprocess it to ensure consistency and cleanliness. This might involve handling missing values, converting data types, and aligning the dataframes for further analysis. Exploratory Data Analysis (EDA):

Next, I would conduct exploratory data analysis to gain insights into the datasets. This could involve calculating summary statistics, visualizing price movements, and identifying any trends or patterns. Calculation of Additional Metrics:

With the OHLCV data in hand, I would calculate the additional metrics mentioned earlier: Price-to-Earnings Ratio (P/E Ratio) Price-to-Book Ratio (P/B Ratio) Return on Equity (ROE) Historical Volatility These metrics would be calculated based on the historical price and financial data available for each stock. Visualization:

I would create visualizations to present the calculated metrics and insights in a clear and intuitive manner. This could include line plots, bar charts, histograms, and scatter plots to illustrate trends, distributions, and relationships. Interpretation and Conclusion:

Finally, I would interpret the results of the analysis and draw conclusions about the financial performance and behavior of the selected stocks. I would discuss any notable findings, trends, or anomalies discovered during the exploration process. Below is a simplified example code snippet to demonstrate how some of these steps might be implemented:


## Question 7. [Exploratory] Time-driven strategy description around earnings releases

Free text answer

Explore earning dates for the whole month of April - e.g. using YahooFinance earnings calendar (https://finance.yahoo.com/calendar/earnings?from=2024-04-21&to=2024-04-27&day=2024-04-23). Compare with the previous closed earnings (e.g., recent dates with full data https://finance.yahoo.com/calendar/earnings?from=2024-04-07&to=2024-04-13&day=2024-04-08).

Describe an analytical strategy/idea (you're not required to implement it) to select a subset companies of interest based on the future events data.

### Answer 7

To develop a time-driven strategy around earnings releases, we can use historical earnings data and upcoming earnings calendar information to identify potential trading opportunities. Here's a suggested analytical strategy:

Collect Historical Earnings Data:

Gather historical earnings data for a range of companies, including earnings release dates, actual earnings per share (EPS), and consensus EPS estimates. This data can be obtained from financial websites like Yahoo Finance or specialized financial data providers. Analyze Previous Earnings Releases:

Analyze the previous earnings releases to identify patterns and trends in stock price movements before and after earnings announcements. Look for factors such as: Stock price behavior leading up to earnings (e.g., price trends, volatility). Deviation of actual EPS from consensus estimates and its impact on stock price. Market reaction post-earnings (e.g., price gap, magnitude of price change). Explore Upcoming Earnings Calendar:

Utilize the earnings calendar feature on Yahoo Finance or similar platforms to identify upcoming earnings releases for the month of April and beyond. Focus on companies with upcoming earnings releases that have historically exhibited significant price movements in response to earnings announcements. Screen for Potential Trading Opportunities:

Develop criteria to screen for potential trading opportunities based on the upcoming earnings calendar. This could include factors such as: Companies with a history of beating consensus EPS estimates. Companies with a history of significant price movements post-earnings. Stocks exhibiting technical patterns suggestive of potential price breakout or breakdown. Implement Trading Strategies:

Based on the screening criteria, select a subset of companies of interest for potential trading opportunities. Develop and backtest trading strategies tailored to capitalize on anticipated price movements around earnings releases. This could include: Buying options or initiating directional trades (long or short) before earnings based on anticipated price movement. Employing volatility-based strategies such as straddles or strangles to profit from expected price volatility post-earnings. Risk Management and Monitoring:

Implement robust risk management practices to limit downside risk and preserve capital. Monitor the selected trades closely, especially around earnings release dates, and adjust positions as needed based on real-time market conditions and new information. By following this analytical strategy, traders and investors can identify and capitalize on potential trading opportunities driven by earnings releases, while also managing risk effectively.

Below, I'll outline how you can implement the analytical strategy described earlier using data available in a Jupyter Notebook:

Collect Historical Earnings Data:

Download historical earnings data for a range of companies from Yahoo Finance using the yfinance library in Python. You can specify the date range and retrieve information such as earnings release dates, actual EPS, and consensus EPS estimates. Analyze Previous Earnings Releases:

Load the historical earnings data into pandas DataFrames and conduct exploratory data analysis (EDA) to analyze patterns and trends in stock price movements before and after earnings announcements. Calculate metrics such as price changes, EPS surprises, and volatility around earnings dates. Explore Upcoming Earnings Calendar:

Use web scraping techniques or API requests to fetch the upcoming earnings calendar data from Yahoo Finance or a similar platform. Extract relevant information such as companies with earnings releases scheduled for the month of April and beyond. Screen for Potential Trading Opportunities:

Apply filtering and screening criteria to identify potential trading opportunities based on the upcoming earnings calendar data. This could involve selecting companies with a history of significant price movements post-earnings or those expected to beat consensus EPS estimates. Implement Trading Strategies:

Based on the screening results, develop and implement trading strategies in Python. This may involve executing trades such as buying options, initiating directional trades, or employing volatility-based strategies using libraries like numpy, pandas, and scikit-learn. Risk Management and Monitoring:

Implement risk management techniques such as position sizing, stop-loss orders, and profit targets to manage downside risk effectively. Monitor the selected trades closely using real-time market data and adjust positions as needed. Below is a high-level outline of how you can structure your Jupyter Notebook to implement these steps:

Import necessary libraries: yfinance for fetching historical data, pandas for data manipulation, matplotlib and seaborn for visualization. Collect historical earnings data using yfinance. Analyze and visualize historical earnings data to identify patterns. Fetch upcoming earnings calendar data using web scraping or APIs. Screen for potential trading opportunities based on predefined criteria. Develop and implement trading strategies. Implement risk management techniques. Monitor trades and adjust positions as needed. By following this approach, you can implement the analytical strategy described earlier in a Jupyter Notebook using Python and relevant libraries. If you need further assistance with any specific step or code implementation, feel free to ask!
