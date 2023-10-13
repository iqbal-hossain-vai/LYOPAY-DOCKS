# How to use LYOTRADE futures calculator?

## **How to use LYOTRADE futures calculator?**

You may use the LYOTRADE Futures Calculator to calculate the initial margin, profit & loss (PnL), return on equity (ROE), and liquidation price before placing any orders.

1. Click on the **\[Calculator]** icon on the Order Entry Panel (right-side of the futures trading interface).
2. You can choose **\[PNL]**, **\[Target Price]**, **\[Liquidation Price]**, **\[Max Open]**, or **\[Open Price]**.
3. Select **\[Long]** or **\[Short]**. Next, enter the entry price, exit price, and quantity of your order. You can choose the leverage level by moving your cursor along the slider bar.
4. Click **\[Calculate]**. The result for the initial margin, PnL, and ROE will be displayed on the right.

Notes for calculating P\&L, initial margin, and ROE:

### USDT-margined contracts

* Initial Margin = Quantity \* Entry Price \* IMR
  * IMR = 1 / leverage
* PnL:
  * Long = (Exit Price - Entry Price) \* Quantity
  * Short = (Entry Price - Exit Price) \* Quantity
* ROE% = PnL / Initial Margin = side \* (1 - entry price / exit price) / IMR
* Target price:
  * Long target price = entry price \* ( ROE% / leverage + 1 )
  * Short target price = entry price \* ( 1 - ROE% / leverage )
