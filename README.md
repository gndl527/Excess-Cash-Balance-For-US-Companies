# Excessive Cash Losing Investors Billions: A Research to Show the Numbers

### Problem Statement 

Cash, as an asset class, is widely recognized in the investment community as the worst asset to hold in a portfolio or balance sheet. Companies and portfolio managers hold cash mainly because it provides liquidity and a means for crisis management. However, since cash is a non-operating asset and subject to inflation, it is extremely unreasonable for publicly-traded companies to hold more cash on their balance sheet rather than giving it back to investors, who could in turn find other potential investments to generate returns. Corporate managers tendency to keep more-than-needed cash in hand, rather than paying it out as dividend, is one of biggest value-sucker in public equity today. 

In this project, we aim to find the companies with the most excessive cash on their balance sheet and the impact of this cash to investors. We will look at three questions:

1. Where and how can we effectively collect market data? Can we build an efficient tool to get the data? 
2. Which companies in the S&P 500 has the most excessive cash in their balance sheet and how much?
3. What's the estimated value loss for investors as a result of these excessive cash holding? (If they were to get this cash as dividend and reinvest them back to capital market, what would the estimated return be)
4. What are the limitations we are facing and how can we scale this project to better model the numbers and drive more insightful recommendations.


**Author**

[David Li](https://www.linkedin.com/in/davidgnli/)

This project was completed in cooperation with [General Assembly](https://generalassemb.ly) in October 2019.

---

### Data Sources
1. [Yahoo Finance](https://finance.yahoo.com/): One of the best sources for public market data.
2. [Data Hub](https://datahub.io/core/s-and-p-500-companies-financials#data-cli): This is where we get a very clean csv file for the S&P 500 stocks and their sectors.

---

### Project Files

Here is the workflow order to follow when running through the notebooks, which can be found in the [code folder](./code):

- [GA Capstone Jupyter Notebook Code](./code/)
- [GA Capstone Presentation](./slides/)

---

### Executive Summary

The evaluation of cash has been traditionally viewed as a seemingly easy task. Analysts usually just place cash on face value and add it back to the valuation of the company. In my opinion, this method is not only biased but flawed. Should cash be considered equally valuable in the hands of Alphabet, a high growth and highly profitable company, and GE, a great company with very limited growth and upside left in it? The answer is pretty obvious in my opinion. I believe tons of value can be extracted if corporate managers simply return these extra cash back to investors through either stock buyback or dividend.

First, we created a set of tools that allow us to directly scrape data from the internet. We collected cash balances, among other financial statistics and financial statements for 474 companies tracked by the S&P 500 to look at which companies and which industries hold the most excessive cash and what the damage had been for investors in terms of value. The key data to collect is the cash balance, financial statements, growth rate and market statistics such as retention rate, dividend rate. We will setup metrics to determine the value differences between a company that holds too much cash versus similar companies who give cash back to investors. 

Second, we cleaned up the data as there were a lot of null values. We had to deduce it by certain factors. This raw data is extremely valuable in the sense that it allows us to see the how cash is used and reserved across different industries. We were able to derive a number of interesting visualizations from this process.

Lastly, the modeling process is fairly straight forward. There are much room for improvement to adjust the data and perform additional feature engineering. But we chose a very simply linear regression model to project the "fair cash balance" for each of the 474 companies. We derived some very interesting results.


---

### Conclusion, Limitations and Next Steps

##### Conclusions
1. As a result of the this project, we found that in terms of pure scale of excessive cash, financial services and asset managers such as The Bank of New York Mellon Corp, State Street, Lincoln Nations hold the champions. This is not surprising as these companies hold a large portfolio and are engaged in services that require cash to provide liquidity.
2. Outside of financial services firms, the Top 3 goes to Oracle, Facebook and Ford. The details of these companies, their excessive cash, cash/asset ratios and estimated loss of value for public investors can be found in the notebook.

##### Limitations
1. We have financial statement up to only 4 years and market statistics for one the current period: Yahoo Finance requires premium account to go deeper into history. With more data, we could calculate better growth rate and dive deeper into how the companies evolved through the years.
2. The financial statement we collected is the annual statement, many of which were published a long time ago. As market conditions change over time, we are subject to historical bias.
3. This goes without saying, the tools we created are limited to publicly traded companies that reports earnings. With that being said, ETFs and other asset class would not do have these attributes.
4. Yahoo updates its site from time to time. So this would likely not be a long-term solution. We might be able to use other sources for future use, such as the SimFin API.
5. Scraping is slow because of caution of being blacklisted. We implemented random sleep in the function. We could use rotating proxies to speed things up.
6. Yahoo finance has very incomplete data for a few companies. Due to time constraints, some of these values need to be deduced from other factors. There are many ways to find these values in the official 10K and 10Q given a longer span of time.
7. There are opportunities for better feature engineering. We could get a more accurate growth rate with more historical data. We could also calculate elements such as the WACC, return on capital and other extremely import metrics given more time and better quality data.

##### Next Steps
1. Get more historical data to better understand the company's growth trajectory instead of just relying on current day statistics.
2. Deep dive into sectors and industries within those sectors to understand how companies with different characteristcs behave.
3. Understanding macro market environment, such as interest rate, inflation, unemployment and overall GDP growth.
4. Putting these company on a global scale, looking not only how companies perform in the US but how they behave in Europe, Asia Pacifics, South America and other global and regional markets.
5. Infer better data points that are more correlated with our target, such as weight average cost of capital, return on capital, research and operations, etc.