# Project - Analyzing Stock Performance and Building a Dashboard


# PROJECT OVERVIEW

For this project, you will assume the role of a Data Scientist / Data Analyst working for a new startup investment firm that helps customers invest their money in stocks. Your job is to extract financial data like historical share price and quarterly revenue reportings from various sources using Python libraries and webscraping on popular stocks. After collecting this data you will visualize it in a dashboard to identify patterns or trends. The stocks we will work with are Tesla, Amazon, AMD, and GameStop.

# Dashboard Analytics Displayed

A dashboard often provides a view of key performance indicators in a clear way. Analyzing a data set and extracting key performance indicators will be practiced. Prompts will be used to support learning in accessing and displaying data in dashboards. Learning how to display key performance indicators on a dashboard will be included in this assignment. We will be using Plotly in this course for data visualization .

# Watson Studio


For this project you will use Skills Network Labs and Watson Studio. Skills Network Labs is a sandbox environment for learning and completing labs in courses. Whereas Watson Studio, a component of IBM Cloud Pak for Data, is a suite of tools and a collaborative environment for data scientists, data analysts, AI and machine learning engineers and domain experts to develop and deploy your projects.

# Stock shares

A company's stock share is a piece of the company; more precisely:

A stock (also known as equity) is a security that represents the ownership of a fraction of a corporation. This
entitles the owner of the stock to a proportion of the corporation's assets and profits equal to how much stock they own. Units of stock are called "shares." [1]

An investor can buy a stock and sell it later. If the stock price increases, the investor profits, If it decreases,
the investor with incur a loss.  Determining the stock price is complex; it depends on the number of outstanding shares, the size of the company's future profits, and much more. People trade stocks throughout the day. The stock ticker is a report of the price of a certain stock, updated continuously throughout the trading session by the various stock market exchanges. In this lab, you will use the  y-finance API to obtain the stock ticker and extract information about the stock. You will then be asked questions about your results.  



  # Using the yfinance Library to Extract Stock Data
  
    pip install yfinance 
    pip install pandas


    import yfinance as yf
    import pandas as pd
    
    
Using the Ticker module we can create an object that will allow us to access functions to extract data. To do this we need to provide the ticker symbol for the stock, here the company is Apple and the ticker symbol is # AAPL.

    apple = yf.Ticker("AAPL")
    
 Now we can access functions and variables to extract the type of data we need.
 
# Stock Info

Using the attribute info we can extract information about the stock as a Python dictionary.

    apple_info=apple.info
    apple_info 


We can get the 'country' using the key country

    apple_info['country']
    
# Extracting Share Price

A share is the single smallest part of a company's stock that you can buy, the prices of these shares fluctuate over time. Using the history() method we can get the share price of the stock over a certain period of time. Using the period parameter we can set how far back from the present to get data. The options for period are 1 day (1d), 5d, 1 month (1mo) , 3mo, 6mo, 1 year (1y), 2y, 5y, 10y, ytd, and max.

   apple_share_price_data = apple.history(period="max")

The format that the data is returned in is a Pandas DataFrame. With the Date as the index the share Open, High, Low, Close, Volume, and Stock Splits are given for each day.

    apple_share_price_data.head()


We can reset the index of the DataFrame with the reset_index function. We also set the inplace paramter to True so the change takes place to the DataFrame itself.

   apple_share_price_data.reset_index(inplace=True)
   
   We can plot the Open price against the Date:

    apple_share_price_data.plot(x="Date", y="Open")


# Extracting Dividends

Dividends are the distribution of a companys profits to shareholders. In this case they are defined as an amount of money returned per share an investor owns. Using the variable dividends we can get a dataframe of the data. The period of the data is given by the period defined in the 'history` function.

    apple.dividends
   
   
We can plot the dividends overtime:


apple.dividends.plot()










