# Failed orders in futures

## **Failed orders in futures** &#x20;

Sometimes, the order you place in the futures market may fail or may not be filled. Here are some possible reasons.&#x20;

### Reasons for place order failure:

1. **Your margin balance is insufficient** \
   \
   Here's how to check the margin balance: 1. There are other open orders using the margin, 2. the order amount exceeds the position amount, and you need extra margin to open the position. \
   \
   The lower the leverage, the higher the required margin balance. Altering the leverage could solve the insufficient balance issue.\

2. **Limited position** \
   \
   For stop-limit orders, the margin balance of the net position is not enough due to the exceeded amount of reverse position. Different maximum notional size the trader can open depends on diverse leverage.\

3. **Your order did not meet the minimum contract quantity** \
   \
   There are specific minimum contact quantities in a contract.\

4. **It was a reduce-only order** \
   \
   The user cannot place the reduce-only order if there is no reverse position.

### Reasons for unfilled orders:

1. **No matching price on the market** \
   \
   The market price does not meet your set price. In a Stop-limit order, when the market price hits the trigger price, the order will be added to the market depth pool. When it hits the set price, the order will be filled. In Stop Market orders, the trigger price could be set at the market price or the latest price based on various demands.\

2. **Deviating hugely from the market price** \
   \
   No matching orders in the market depth pool at the set price. Should the position be very large, it could be partially filled.\

3. **You did not pass the Margin check (for stop limit and stop market orders)** \
   \
   For Stop Limit and Stop Market orders, you need to fill in the trigger price and filled price (In Stop Market orders, the trigger price could be set at the market price or the latest price based on concrete requests). The system will then execute double margin checks before placing an order and before filling the order. Once the order is triggered, the second margin check will be conducted instantly. In this case, if there is any loss or some margin balance has been transferred out from the futures account, resulting in an inadequate margin balance, the order status will be shown as expired.
