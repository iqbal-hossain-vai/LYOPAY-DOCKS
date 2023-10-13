# How to use the stop-limit function?

## How to use the stop-limit function?

### **What is a stop-limit order?**

A stop-limit order is a market order that has both a stop price and a limit price. When the stop price is reached, it triggers the limit order. The limit price is the specific price of the limit order the stop price triggers. Once your stop price has been reached, the limit order is immediately placed on the order book.

The stop and limit prices can be the same. However, it’s recommended for sell orders to set the stop price (trigger price) slightly higher than the limit price. The price difference allows for a safety gap in price between the time the order is triggered and when it is fulfilled.&#x20;

{% hint style="info" %}
For buy orders, set your stop price slightly lower than the limit price. This will also reduce the risk of your order not being fulfilled.
{% endhint %}

### **Stop-limit terms and mechanics**

**Stop price**: When the asset’s price reaches the given stop price, the stop-limit order is executed to buy or sell the asset at the given limit price or better.

**Limit price**: The selected (or potentially better) price that the stop-limit order is executed.

**Quantity**: The number of assets to buy or sell in the stop-limit order.

Example: The last traded price of LYO Credit token is 498 LYO, and you feel that there is resistance around 500 LYO. If you think that the price will go higher after the price reaches the resistance level, you can put a Stop-Limit order to automatically buy more LYO at the price of 502 LYO. This way, you won’t have to continuously watch market movements waiting for the price to reach your target price.
