<img width="850" height="470" alt="download" src="https://github.com/user-attachments/assets/a3c77167-7477-40e2-9df1-88a885a303a8" />

# High Frequency Quant Risk Engine

I built this project to solve a common problem in financial risk management: traditional risk models often fail during market crashes because they rely on daily averages instead of high-frequency tick data. My goal was to create an end-to-end pipeline that can process streaming market data, detect sudden liquidity drops, and calculate exact capital loss limits for a $10M multi-asset portfolio holding stocks, crypto, and currencies.

To test this at scale, I simulated 1,000,000 high-frequency trade records. I used DuckDB inside Python to run fast SQL window functions directly on the dataset, calculating log returns, rolling volatility, and volume spikes. After transforming the data, I trained an XGBoost classification model to spot tail-risk anomalies before they trigger portfolio-wide losses.

Finally, I ran 10,000 Monte Carlo simulations to map out thousands of potential market outcomes. The engine calculated a 99% Value at Risk of approximately $10.18M, meaning there is only a 1% chance of losses exceeding this threshold over the period. In the worst 1% of market scenarios, the Expected Shortfall reached $11.91M. The whole project demonstrates how combining SQL, machine learning, and quantitative finance helps risk managers set proper capital reserves and protect assets during extreme market stress.
