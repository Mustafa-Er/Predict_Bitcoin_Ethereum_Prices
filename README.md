**General Information**
​

Data ranges from 2019-09-01 to 2023-05-31. Information about features is below.
​
**Features:**

* open_time: Kline Open time in unix time format
* open: Open Price
* high: High Price
* low: Low Price
* close: Close Price
* volume: Volume
* close_time: Kline Close time in unix time format
* quote_volume: Quote Asset Volume
* count: Number of Trades
* taker_buy_volume: Taker buy quote asset volume during this period
* taker_buy_quote_volume: Taker buy base asset volume during this period
* ignore : Ignore(you can drop this feature)
​
* quantile_transform_close_price: Quantile Transform of Close Prices
  
​
**Time_Based_Features**
* month: The month of the date of the data
* year: The year of the date of the data
* quarter: The quarter of the date of the data
* weekofyear: The weekofyear of the date of the data
  
​
**Financial_Terms**
* rsi_7_days: RSI Values for 7 day periods (If you dont know mean of RSI, you can look at link which exist on RSI header)
* rsi_14_days: RSI Values for 14 day periods
* rsi_30_days: RSI Values for 30 day periods
* ema_12_days: Exponential Movement Average for 12 day periods (If you dont know mean of EMA, you can look at link which exist on Exponential Moving Average header)
* ema_26_days: Exponential Movement Average for 26 day periods
* middle_band: Average of Close Prices for 20 day periods.We used this feature for bollinger bands.
* std_dev: Standart Deviation of Close Prices for 20 day periods.We used this feature for bollinger bands.
* upper_band: It equals middle_band + 2 * std_dev. We used this feature for bollinger bands.
* lower_band: It equals middle_band - 2 * std_dev. We used this feature for bollinger bands.
* is_price_above_upper_band : This feature is binary variable which see if close price higher than upper_band
* is_price_below_lower_band :This feature is binary variable which see if close price lower than lower_band
* bandwidth: It equals to upper_band - lower_band. I mean, it means differences between upper band to lower band
* is_bandwidth_gt_6000 : This feature is binary variable which see if **bandwidth for bitcoin** higher than 6000
* is_bandwidth_gt_400: This feature is binary variable which see if **bandwidth for bitcoin** higher than 400
  
​
**OnChain Indicators**

​
This indicators taken from IntoTheBlock. I add this data to github/data section. This datas are daily basis. So I create daily dataset from hourly dataset to see onchain indicator effect on model. So from OnChain Indicator header, I have a 4 datasets(hourly and daily datasets for bitcoin and ethereum)
You can see details on OnChain Indicatore header to understand mean of indicators.
​
* sum_of_tweets : sum of positive, neutral, negative tweets for bitcoin and ethereum. 
* total_flow : The Total Flows indicator provides indication of instances of high centralized exchange activity. So when does centralized exchange activity tend to increase? In general, we see spikes in Total Flows when there are either local tops/bottoms (shown in blue), but also when there are price breakouts (orange). Conversely, Total Flows tend to drop during periods of accumulation or consolidation as highlighted in yellow. While Total Flows can be indicative of market positioning, there are also natural flows managed by centralized exchanges which can lead to sudden outliers that may not necessarily be predictive of price changes. 
* local_minima_total_flows : This features is binary variable which If point is local minimum of total_flow
* local_maxima_total_flows : This features is binary variable which If point is local maximum of total_flow
* inflow : Exchange inflows are helpful to track funds going into exchanges. Spikes in inflows tend to coincide with and sometimes precede periods of high volatility as shown above. This can potentially be interpreted as a sign of holders looking to sell in centralized exchanges.At the same time, there are natural fluctuations in inflows as centralized exchanges and institutional players manage their funds. For instance, unsurprisingly inflows tend to drop on weekends and increase during the week. Overall, Inflow Volume can be helpful to spot periods of high volatility, but users should also consider there are natural fluctuations in the indicator which make it less predictive during periods of low volatility.
* local_maxima_inflow : This features is binary variable which If point is local maximum of inflow volume
* outflow : While Inflow Volume at times anticipate volatility, Outflow Volume is often more reactive. In other words, Outflow Volume often spikes following either a crash or a significant break-out as shown in the example above. This could potentially be interpreted as users going long and opting to hold their crypto outside centralized exchanges.
* outflow_transaction_count : The Outflow Transaction Count indicator provides indication of users withdrawing their funds from centralized exchanges likely to store in safer cold wallets. This is a valuable approximation of users going long and opting to hold their own funds. For this reason, outflows tend to spike as price crashes as pointed in the example above. While this can be the case on several occasions, natural fluctuations in exchanges’ flows can often have smaller spikes without regards to price action as well.
* local_maxima_outflow_transaction_count : This feature is binary variable which If point is local maximum of outflow_transaction_count 
* inflow_transaction_count : As the name suggests, the Inflow Transaction Count indicator provides the number of incoming crypto transactions entering exchanges. While the Inflow Volume measures the aggregate dollar amount, which is influenced by whales’ transactions, the Inflow Transaction Count is a better approximation of the number of users sending funds into exchanges. This indicator has also shown to rise along and anticipate periods of high volatility. For example, on September 1st, inflow transactions for Bitcoin hit a 3-month high preceding a decrease in price of 14% over the following 48 hours. While this pattern does tend to emerge, natural fluctuations in inflow transactions can also increase at times.
* local_maxima_inflow_transaction_count: This feature is binary variable which If point is local maximum of inflow_transaction_count 
* netflow: Net Flows = Inflow Volume - Outflow Volume. The Net Flows indicator highlights trends of traders sending money in and out of exchanges. Recall that Net Flows are positive when more funds are entering than leaving exchanges. Therefore, we observe that positive Net Flows tend to coincide with periods following large increases in price (like LINK when it tripled between April and July) or confirmation of down-trends (as seen with LINK in late August). Conversely, Net Flows are negative when a greater volume is being withdrawn from exchanges. This could be seen as a sign of accumulation (LINK in early August) or addresses buying back following large declines (LINK in early September). While Net Flows also affect large cap crypto-assets, smaller cap tokens are more susceptible to large changes in prices deriving from exchange flows. This is simply a result of smaller caps requiring less capital in order to make market-moving trades. This is worth considering when using the Net Flows indicator to trade.
* local_minima_netflow : This features is binary variable which If point is local minimum of netflow
* local_maxima_netflow : This feature is binary variable which If point is local maximum of netflow
