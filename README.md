# Chainlink Price Ratio (WIP)

### Description

This notebook queries prices from chainlink price feeds, and builds a history of price ratios from the asynchronous price feed updates. All zero prices are removed from the analysis, as this scenario should trigger the backup oracles in AAVE.


### Limitations

With a free infura account, I can only afford to query about 10000 rounds per day.
