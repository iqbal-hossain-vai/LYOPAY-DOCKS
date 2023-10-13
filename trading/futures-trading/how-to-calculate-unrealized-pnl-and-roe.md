# How to calculate unrealized PNL and ROE%?

## How to calculate unrealized PNL and ROE%?

* **Users choose mark price as price basis**:

Unrealized PNL = position size \* direction of order \* (mark price - entry price)

ROE% =Unrealized PNL in USDT / entry margin = ( ( mark price - entry price ) \* direction of order \* size ) / （position\_amount \* contract\_multiplier \* mark\_price\* IMR）

\*IMR = 1/Leverage

* **Users choose the latest price as price basis**:

Unrealized PNL = position size \* direction of order \* (latest price - entry price)

ROE% = Unrealized PNL in USDT / entry margin = ( ( latest price - entry Price ) \* direction of order \* size ) / （position\_amount \* contract\_multiplier \* mark\_price\* IMR）

Direction of order: 1 for long order；-1 for short order.
