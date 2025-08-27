# GS_ETF_PORTFOLIO_OPTIMIZATION
## Project Overview
This project explores ETF portfolio optimization techniques with a focus on risk-adjusted returns, diversification, and practical applicability in financial markets. Using Python, the notebook implements quantitative finance methods to analyze exchange-traded funds (ETFs), evaluate their historical performance, and construct an optimized portfolio.


## Description
This Python program is designed to help users understand and implement portfolio optimization strategies. This adaptation demonstrates the process with real-world Goldman Sachs ETFs. The entire project can be run conveniently in a Google Colab environment, which allows for direct Python code execution without requiring local installation.

The project guides you through the process of:
• Acquiring historical price data for selected ETFs.

• Calculating key financial metrics such as daily returns, covariance, variance, and volatility.

• Visualizing portfolio performance trends.

• Applying advanced optimization algorithms to achieve a maximal Sharpe ratio, indicating a portfolio with the best risk-adjusted return.

• Providing a discrete allocation plan, detailing the number of shares to purchase for each ETF based on your total investment amount.

## Key Features
• Data Acquisition: Automatically fetches historical adjusted close price data for user-defined iShares ETFs using pandas_datareader.

• Financial Analysis & Metrics:

    ◦ Calculates daily simple returns for each ETF.
    ◦ Determines the annualized covariance matrix, which quantifies the directional relationship and co-movement between asset prices.
    ◦ Computes portfolio variance and volatility (standard deviation), which represent the portfolio's overall risk.
    ◦ Calculates the annual portfolio return.
    
• Visual Data Representation: Generates plots to visually display the historical adjusted close price trends of the ETFs within the portfolio.

• Advanced Portfolio Optimization:

    ◦ Utilizes the PyPortfolioOpt library, a powerful tool for modern portfolio theory.
    ◦ Calculates expected returns and the annualized sample covariance matrix of asset returns.
    ◦ Optimizes the portfolio to achieve the maximal Sharpe ratio, a critical metric that measures the excess return an investment receives for a given amount of volatility, comparing its performance against a risk-free investment.
    ◦ Outputs optimal "cleaned weights" for each ETF, indicating the ideal proportion of your portfolio to allocate to each asset for the maximal Sharpe ratio.
    ◦ Presents the expected annual return, annual volatility (risk), and the Sharpe ratio of the optimized portfolio, demonstrating how strategic adjustments can lead to better risk-adjusted performance.
    
• Discrete Allocation Planning: Based on the optimized weights and a specified total portfolio value (e.g., $15,000), the program calculates the discrete number of shares of each ETF to buy, along with any remaining funds.

## How It Works
The program follows a structured approach to portfolio optimization:
1. Environment Setup: The code is designed to run in Google Colab, making it accessible and easy to use.
   
2. Library Imports: Essential Python libraries like pandas_datareader, pandas, numpy, datetime, matplotlib.pyplot, and PyPortfolioOpt are imported to handle data, perform calculations, and plot results.
   
3. Asset Definition: The user defines the GS ETF tickers (e.g., "AAAU", "GSLC", "GSSC", "GHYB" – note: the original source uses FAANG stocks; you would replace these with your desired iShares ETFs) that will constitute the portfolio.
   
4. Initial Weights: An initial set of weights is assigned to each ETF (e.g., equal distribution).
   
5. Date Range Selection: A historical start date (e.g., 2018-01-01) and today's date as the end date are set for data retrieval.
   
6. Data Retrieval: Historical adjusted close prices for the selected iShares ETFs are fetched and stored in a Pandas DataFrame.
   
7. Initial Portfolio Analysis:
    ◦ The daily simple returns are calculated.
    ◦ The annualized covariance matrix is computed to understand how the ETF prices move relative to each other.
    ◦ The initial portfolio variance, volatility (risk), and annual return are calculated and displayed.
    ◦ A visual representation of the ETFs' historical adjusted close prices is generated.
   
8. Optimization with PyPortfolioOpt:
    ◦ The PyPortfolioOpt library is used to calculate expected returns and the sample covariance matrix.
    ◦ The portfolio is optimized to maximize the Sharpe ratio, providing a set of optimal weights for each ETF. The clean_weights helper method is used to refine these weights by setting small values to zero and rounding others.
    ◦ The optimized expected annual return, volatility, and Sharpe ratio are then displayed, showing the improved risk-adjusted performance.
   
9. Discrete Allocation: Finally, given a total investment amount, the program determines the exact number of shares of each ETF to purchase based on the optimized weights, and calculates any remaining cash

## Results
The project demonstrates the effectiveness of portfolio optimization when applied to a set of Goldman Sachs ETFs.

Before Optimization (Equal Weights)

An initial portfolio was constructed with an equal allocation of 20% to each ETF. Its performance metrics were:

Expected annual return: 12.0%

Annual volatility (risk): 13.0%

Annual variance: 2.0%

This allocation provided a balanced but unoptimized portfolio, leaving room for improvement in risk-adjusted performance.

After Optimization (Maximizing Sharpe Ratio)

Using the PyPortfolioOpt library, the portfolio was optimized to maximize the Sharpe ratio. The optimal allocation favored a mix of the Goldman Sachs ActiveBeta U.S. Large Cap Equity ETF (GSLC) and Goldman Sachs Physical Gold ETF (AAAU), while assigning negligible weight to the other ETFs.

The optimized portfolio achieved:

Optimal Weights:

AAAU: 69.6%

GSLC: 30.4%

GSSC, GHYB: 0%

Expected annual return: 15.4%

Annual volatility: 12.7%

Sharpe ratio: 1.21

## Interpretation

The optimization improved the expected return by ~3.4 percentage points while simultaneously reducing portfolio risk (volatility) compared to the equal-weight portfolio. This resulted in a significantly higher risk-adjusted performance, as captured by the Sharpe ratio (from below 1.0 to 1.21).
