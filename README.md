# Stock Market Portfolio Optimization with Python: 📊📈🐍

# Overview:

This project focuses on optimizing a stock market portfolio using Python. The goal is to achieve the best possible balance of risk and return for a given portfolio by applying modern portfolio theory (MPT) and various financial optimization techniques. The project incorporates data analysis, financial modeling, and visualization to guide investors in making data-driven decisions.

# Introduction:
Stock market portfolio optimization is the process of selecting the best portfolio (asset distribution) out of the set of all portfolios being considered, according to some objective, such as maximizing return or minimizing risk. This project implements optimization techniques using Python to calculate the optimal weights for a portfolio based on historical stock data.

The core techniques used in this project include:

Mean-Variance Optimization: Based on Modern Portfolio Theory by Harry Markowitz.

**Efficient Frontier:** Plotting the risk-return tradeoff of portfolios.

**Sharpe Ratio Maximization:** Adjusting portfolios to maximize the risk-adjusted return.

**Monte Carlo Simulation:** Random sampling of portfolio allocations to identify optimal solutions.

**Imports:** It imports necessary libraries:

 - pandas for data manipulation.
 - yfinance for fetching stock market data.
 - date and timedelta from datetime for date handling.

**Date Range:**

- It defines the time period for which stock data will be downloaded. The end_date is set to today, and the start_date is one year before today.

**Stock Tickers:**

- The script specifies a list of stock tickers (tickers) to download data for. In this case, it includes major Indian stocks: Reliance, TCS, Infosys, and HDFC Bank.

**Download Data:**

- Using yfinance, the script downloads historical stock data (Open, High, Low, Close, Volume, etc.) for the specified tickers and date range.

**Data Reshaping:**

It resets the index to make the Date a column.
  - The melt function is used to reshape the DataFrame from wide to long format, with each row representing a unique combination of Date, Ticker, and Attribute (e.g., Open, Close).
  - The pivot_table function is then used to reshape the DataFrame again, this time creating columns for each Attribute (Open, High, Low, etc.), organized by Date and Ticker.

**Final DataFrame:**

- The resulting stock_data DataFrame is a tidy dataset with columns for Date, Ticker, and each stock attribute.

Now, let’s have a look at the stock market performance of these companies in the stock market over time:

This script visualizes the adjusted close prices of different stocks over time using matplotlib and seaborn. Here's a breakdown of what it does:

**Imports:**

 - matplotlib.pyplot for plotting.
 - seaborn for enhanced visualization.

**Data Preparation:**

 - The Date column in stock_data is converted to a datetime object for accurate time-series plotting.
 - The Date column is set as the index to facilitate easy plotting, and then reset to ensure it's available as a column for plotting.

**Plot Configuration:**

 - A figure is created with a size of 14x7 inches.
 - The seaborn style is set to 'whitegrid' for a clean background with grid lines.
 - The sns.lineplot function is used to create a line plot:
    - x='Date': The x-axis represents the date.
    - y='Adj Close': The y-axis represents the adjusted close price.
    - hue='Ticker': Different colors are used for different tickers.
    - marker='o': Circular markers are added at each data point.

**Plot Customization:**

- The plot is titled "Adjusted Close Price Over Time."
- Axis labels are added with a font size of 14.
- A legend is added to distinguish between the different tickers, with customized font sizes.
- The x-axis ticks are rotated by 45 degrees for better readability.
- A grid is added for easy interpretation of the data.

**Displaying the Plot:**

- The plt.show() function is called to display the plot.

**Output Visualization:**

When you run this script, you'll see a line plot with the adjusted close prices of each stock (Reliance, TCS, Infosys, HDFC Bank) plotted over time. The lines will be distinct for each stock due to the color coding provided by hue='Ticker'. Markers on the lines will indicate the actual data points, and the grid will make it easier to see trends and changes in stock prices over time.
This visualization provides a clear comparison of how different stocks have performed over the selected time period.
The graph displays the adjusted close prices of four stocks (HDFCBANK.NS, INFY.NS, RELIANCE.NS, TCS.NS) over time from July 2023 to July 2024. It highlights that TCS has the highest adjusted close prices, followed by RELIANCE, INFY (Infosys), and HDFCBANK. The prices for RELIANCE and TCS show noticeable upward trends, which indicates strong performance, while HDFCBANK and INFY exhibit more stability with relatively lower price fluctuations.

Now, let’s compute the 50-day and 200-day moving averages and plot these along with the Adjusted Close price for each stock:
The next part of code is here,
This script calculates and visualizes the 50-day and 200-day moving averages for each stock in your dataset. It also generates bar plots for the trading volume of each stock. Here's a detailed explanation:

# 1. Moving Averages Calculation
 - short_window = 50 and long_window = 200 define the window lengths for calculating the moving averages.

  - 50-Day Moving Average: Represents the average adjusted close price over the last 50 trading days.
  - 200-Day Moving Average: Represents the average adjusted close price over the last 200 trading days.

**The script iterates through each unique stock ticker in your dataset:**
- Filtering Data: For each ticker, a subset of the data (ticker_data) is created.

**Calculating Moving Averages:**
- The 50-day moving average (50_MA) is calculated using the .rolling(window=short_window).mean() method.
- The 200-day moving average (200_MA) is calculated similarly.


# 2. Plotting Adjusted Close Prices and Moving Averages

**For each ticker, a line plot is created:**
   - Adj Close: The actual adjusted close prices are plotted.
   - 50_MA: The 50-day moving average is plotted.
   - 200_MA: The 200-day moving average is plotted.

**Plot Customization:**

 - Title: The plot is titled with the ticker symbol and a description of the data.
 - Axis Labels: Dates are plotted on the x-axis, and prices on the y-axis.
 - Legend: A legend identifies the different lines on the plot.
 - Grid: A grid is added to improve readability.
 - Rotation: The x-axis ticks are rotated by 45 degrees for better visibility.
 - Layout: plt.tight_layout() is used to adjust the subplot parameters for a better fit.

# 3. Plotting Trading Volume
A bar plot is created for the trading volume of each ticker:
  - Volume: The traded volume is plotted as bars, using an orange color for visibility.

**Plot Customization:**
  - Similar customizations are applied, with appropriate titles and axis labels.

**Output:**

For each ticker (Reliance, TCS, Infosys, HDFC Bank), you'll see:

**Line Plot:**
  - The adjusted close price over time.
  - The 50-day and 200-day moving averages overlaid on the price data.

**Bar Plot:**
  - The trading volume for each day.

These plots allow you to analyze trends in stock prices and volumes, with the moving averages helping to smooth out short-term fluctuations and highlight longer-term trends. This is particularly useful for identifying potential buy or sell signals in the context of technical analysis.

For HDFCBANK and INFY, the prices initially decline but later show signs of recovery, as indicated by the moving averages. RELIANCE and TCS display a more consistent upward trend in their adjusted close prices. The volume traded graphs highlight significant trading activity at various points, with spikes indicating high trading volumes, particularly noticeable in HDFCBANK and RELIANCE around early 2024. These insights are crucial for understanding price movements and trading behaviours, which assist in making informed investment decisions.

Now, let’s have a look at the distribution of daily returns of these stocks:


This script calculates and visualizes the distribution of daily returns for each stock in your dataset. Here's what the code does in detail:

# 1. Daily Return Calculation: 
 - stock_data['Daily Return']: This line calculates the daily return for each stock.
 - groupby('Ticker')['Adj Close'].pct_change(): The .groupby('Ticker') ensures that the percentage change is calculated separately for each stock ticker, based on the adjusted close    prices.    - 
 - The .pct_change() function computes the percentage change between the current and previous trading day's adjusted close price.

# 2. Plotting the Distribution of Daily Returns: 

**- Figure Setup:**
  - A figure is created with a size of 14x7 inches.
  - sns.set(style='whitegrid') sets the style of the plot to 'whitegrid', giving it a clean appearance with grid lines.

**- Plotting for Each Ticker:**

  - The script loops through each unique ticker.
  - For each ticker, it filters the data (ticker_data) and plots a histogram of the daily returns.
    - sns.histplot: This function is used to plot the histogram.
    - ticker_data['Daily Return'].dropna(): The dropna() function removes any NaN values from the daily returns, ensuring that the histogram only includes valid data.
    - bins=50: The histogram is divided into 50 bins, which controls the granularity of the histogram.
    - kde=True: A Kernel Density Estimate (KDE) line is overlaid on the histogram, providing a smoothed estimate of the distribution.
    - label=ticker: Each histogram is labeled with its corresponding stock ticker.
    - alpha=0.5: This sets the transparency level of the histogram bars, allowing multiple histograms to overlap without completely obscuring each other.

# 3. Plot Customization
- Title: The plot is titled "Distribution of Daily Returns."
 - Axis Labels:
   -The x-axis is labeled "Daily Return."
   -The y-axis is labeled "Frequency."
- Legend:
  - A legend is added to distinguish between the histograms for different tickers.
  - The legend title and font sizes are customized.
  - Grid: A grid is added to the plot for better readability.
  - Layout: plt.tight_layout() is used to ensure that all plot elements fit nicely within the figure, preventing overlapping or cutoff text.

# Outcome:
When you run this script, you'll see a single figure containing overlapping histograms of the daily returns for each stock ticker (Reliance, TCS, Infosys, HDFC Bank). Each histogram is color-coded according to the stock ticker, and the KDE lines provide a smoothed view of each distribution.

This visualization helps in understanding the return distribution for each stock, showing how frequently certain returns occur, and giving insights into the volatility and risk profile of each stock. Stocks with wider distributions and more extreme daily returns might be considered more volatile, while narrower distributions indicate more stable performance.


The distributions are approximately normal, centred around zero, which indicates that most daily returns are close to the average return. However, there are tails on both sides, which reflect occasional significant gains or losses. INFY and RELIANCE appear to have slightly wider distributions, which suggests higher volatility compared to HDFCBANK and TCS.
INFY and TCS have a high positive correlation (0.71), which indicates that they tend to move in the same direction. HDFCBANK has a moderate positive correlation with RELIANCE (0.37) and a low correlation with INFY (0.17) and TCS (0.10). RELIANCE shows a low correlation with INFY (0.19) and TCS (0.13). These varying correlations suggest potential diversification benefits; combining stocks with lower correlations can reduce overall portfolio risk.

# Portfolio Optimization:

Now, using Modern Portfolio Theory, we can construct an efficient portfolio by balancing risk and return. We will:

1. Calculate the expected returns and volatility for each stock.
2. Generate a series of random portfolios to identify the efficient frontier.
3. Optimize the portfolio to maximize the Sharpe ratio, which is a measure of risk-adjusted return.


# The output shows a diversified portfolio with the following allocations:

1. HDFCBANK (30.85%)
2. INFY (10.59%)
3. RELIANCE (18.02%)
4. TCS (40.53%).

TCS has the highest allocation, which indicates its significant contribution to the portfolio’s performance, while INFY has the smallest allocation. This balanced allocation aims to maximize returns while minimizing risk by leveraging individual stock performances and their correlations.

# Conclusion:

So, this is how stock market portfolio optimization works. Stock market portfolio optimization involves analyzing price trends, calculating expected returns and volatilities, and determining the correlations between different stocks to achieve diversification.

# OUTPUT:
https://github.com/user-attachments/assets/b56048e8-efda-4f98-a1d6-7ffca93db478




