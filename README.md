# Chainlink Price Ratio (WIP)

### Description

This notebook queries prices from chainlink price feeds, and builds a history of price ratios from the asynchronous price feed updates. All zero prices are removed from the analysis, as this scenario should trigger the backup oracles in AAVE. To use my code, you will need an infura account or something similar.

To obtain historical data, I queried the associated chainlink contracts for the latest round number. Each query for a round is associated with five fields:

1. Round ID
2. Answer (Price)
3. Started At (Timestamp)
4. Updated At (Timestamp)
5. Answered in Round ID (Functions as a way for contracts to check that the answer is actually being updated)

For AAVE liquidations, the important fields are the Updated At timestamp and the answer. Because we are calculating price ratios between price feeds but the updates are asynchronous, most timestamps only have results for a subset of currencies. The rest are imputed with the price from the most recently updated price. This should reflect the actual behavior of querying the chainlink oracles at certain points in history. 

### Limitations

* With a free infura account, I can only afford to query about 10000 rounds per day.
* Many of the price feeds are very new so there's not that much data.
* The tools don't seem to exist right now to match up timestamp data to block number, so this makes tracing transactions very painful.

https://governance.aave.com/t/proposal-provide-better-oracle-mechanism-for-stablecoins/4720
