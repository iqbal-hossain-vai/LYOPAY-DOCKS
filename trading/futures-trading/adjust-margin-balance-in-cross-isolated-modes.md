# Adjust margin balance in cross/isolated modes

## **Adjust margin balance in cross/isolated modes**

1. In the Isolated margin mode, you can adjust the margin balance allocated to your position in the **\[Positions]** tab. Click the **\[Edit]** icon to adjust the margin balance.
2. Enter the amount you would like to add or remove. Then, click **\[Confirm]**.
3. Calculations for maximum addable/removable margin in Cross and Isolated margin modes.

### Cross margin mode:

The following calculations are the maximum withdrawal amount in Cross Margin Mode. The two formulas apply when your wallet balance has no gift money or has not used cross collateral:

* Cross Wallet Balance - ∑isolated open order initial margin - cross Position Maintenance Margin

For wallets with unrealized profits or losses, the maximum withdrawal amount must not exceed the following formula:

* Cross Wallet Balance + ∑cross Unrealized PNL - ∑cross initial margin - ∑isolated open order initial margin

Isolated Margin Mode:

The following are calculations for maximum addable and maximum removable margin:

### USDⓈ-Margined contracts <a href="#_lblp7zhsb9qp" id="_lblp7zhsb9qp"></a>

| Field                                  | Calculation                                                                                                                                            |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Max. addable amount to isolated margin | min.（crossWalletBalance - ∑isolated open order initial margin - ∑crossPosition MM, Available for Order）                                                |
| Max. removable from isolated margin    | max.（0，min (isolatedWalletBalance - isolatedPosition MM, isolatedWalletBalance + size \* (mark price - Entry Price) - mark price \* abs(size) \* IMR)） |

