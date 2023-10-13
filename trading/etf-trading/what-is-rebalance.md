# What is rebalance?

## What is rebalance?

Rebalance is the inherent mechanism of ETF products, which can be divided into regular rebalance and irregular rebalance.&#x20;

* Regular rebalance ensures that ETF products can achieve the target rate of return in each cycle.&#x20;
* Irregular rebalance is used to ensure that the net value of ETF will not return to zero and to control product risks.

### Regular rebalance&#x20;

Typically, ETF positions are periodically rebalanced by the platform at 00:00 (UTC+8) each day to make sure that the leverage ratio is the same as agreed.

### Irregular rebalance&#x20;

When the market fluctuates violently, if the volatility of the bottom asset relative to the last rebalance time point exceeds the given threshold (the threshold is set at 12%), we will actively rebalance the corresponding ETF to control the risk and ensure that the net value does not return to zero.

Please note that if the trend continues after an irregular rebalance is triggered, the loss for users will be smaller, but if the trend reverses immediately after the trigger, recovery of the product will be slower due to the reduction of the rebalance.
