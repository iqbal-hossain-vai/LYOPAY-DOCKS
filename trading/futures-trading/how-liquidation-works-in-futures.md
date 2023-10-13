# How liquidation works in futures?

## How liquidation works in futures?

Futures exchanges have established various risk management mechanisms to protect highly leveraged traders from incurring significant losses. One of which is liquidation, a risk control feature that prevents traders from falling into negative equity.

In volatile markets, leveraged positions are prone to price gaps and may cause a trader’s equity to plunge into negative territory instantaneously. In these situations, losses can exceed the maintenance margin.

Here's an example of how it plays out in real life:

Consider two traders, Alice and Bob, both initiated opposing positions in BTC/USDT perpetual futures worth 1 BTC with 20x leverage. Both Alice and Bob have a wallet balance of 5,000 USDT each. Table 1 describes the details of their respective positions.

Table 1 - Position details of Alice and Bob

|       | <h4 id="_4gdbuldop4bf"><strong>Position</strong></h4> | <h4 id="_b6kfwwr7v6vp"><strong>Entry Price</strong></h4> | <h4 id="_4g5cmun962ar"><strong>Notional Value</strong></h4> | <h4 id="_a8dzrg6zcwql"><strong>Initial Margin</strong></h4> | <h4 id="_y7ct1ryuihk1"><strong>Maintenance Margin</strong></h4> | <h4 id="_66i0tf3vhi1f"><strong>Liquidation Price</strong></h4> |
| ----- | ----------------------------------------------------- | -------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------- | -------------------------------------------------------------- |
| Alice | Long                                                  | $55,000                                                  | $55,000                                                     | 5%                                                          | 0.5%                                                            | $50,200                                                        |
| Bob   | Short                                                 | $55,000                                                  | $55,000                                                     | 5%                                                          | 0.5%                                                            | $59,750                                                        |

Let’s assume a 10% fall in BTC/USDT perpetual prices to $49,500. In this scenario, Alice incurs a loss of $5,500 in her long trade, while Bob profits $5,500 on his short trade. The consequent events are as follows:

* Alice depletes her margin and is subjected to liquidation.
* The price at which margin drops to zero is called the liquidation price. For Alice, $50,200 is the liquidation price.
* Instantaneously, the exchange liquidates Alice’s position at $50,200 to ensure that Alice does not fall into negative equity.

In a volatile market, it is extremely difficult to ensure that the losing positions are liquidated precisely at their liquidation price. Furthermore, liquidating beyond the bankruptcy price would mean that Bob receives fewer profits and Alice would incur more losses.

To prevent these occurrences, exchanges tend to liquidate the losing positions at a price better than the liquidation price.

In cases where an exchange is unable to liquidate positions before a trader reaches negative equity, the following methods will be used to cover the losses of bankrupt positions:

* Insurance Fund: A fund that is maintained by the exchange to ensure that profitable traders receive their profits in full and cover for any excess losses incurred by a bankrupt trader.
* Auto-deleverage liquidations (ADLs): In ADLs, the exchange selects opposing traders in order of leverage and profitability, from which positions are automatically liquidated to cover for the losing trader’s position.
