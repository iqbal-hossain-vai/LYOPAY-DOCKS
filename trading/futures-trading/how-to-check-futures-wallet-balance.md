# How to check futures wallet balance?

## **How to check futures wallet balance?**&#x20;

You can check your wallet balance in two sections on the futures trading interface. The first section is on the Order Entry Panel. The second section is on the **\[Assets]** widget, located on the bottom right corner of your trading interface.

1. On the \[Assets] widget, you can view the balances of different assets in your Futures Wallet. For USDⓈ-M Futures, you will be able to view balances in USDT.
2. Alternatively, you may click on \[Wallet] to check your Futures Wallet balance.
3. Margin balance factors in unrealized profit and loss, and as such, the margin balance will fluctuate in real-time if there are open positions.
4. To view the balance of each asset, click on the \[Assets] tab.

**Notes**:

* Margin Balance = Wallet Balance + Unrealized P\&L. (Your positions will be liquidated once Margin Balance <= Maintenance Margin.)
* Wallet Balance = Total Net Transfer + Total Realized Profit + Total Net Funding Fee - Total Commission.
* Unrealized profit and loss on your positions are calculated based on Mark Price.
* Available for Order (i.e. Available margin for opening a position):
  * For USDⓈ-M Futures: Available for Order = max(0, crossWalletBalance + ∑cross Unrealized P\&L - (∑cross initial margin + ∑isolated open order initial margin)
  * Isolated open order initial margin = abs(isolated present notional) \* IMR - abs(size) \* IMR \* mark price
  * Isolated open order initial margin = abs(isolated present notional) \* IMR - abs(size) \* contract Size \* IMR / mark price
* Balance (i.e. Wallet Balance): Wallet Balance = Total Net Transfer + Total Realized Profit + Total Net Funding Fee - Total Commission
