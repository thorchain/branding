# CONTINUOUS LIQUIDITY POOLS

## Implementation specification for the continuous liquidity pools in THORChain
devs@thorchain.org

V0.1 September 2018

### Abstract 
>THORChain uses continuous liquidity pools to allow on-chain conversions of tokens into and out of Rune and a mathematical price. The continuous liquidity pools are permissionless; anyone can add or remove liquidity and anyone can use the pools to convert between assets. The pools rely on permissionless arbitrage to ensure correct market pricing of assets at any time. 


### Theory

Tokens on one side of the pool are bound to the tokens on the other. We can now determine the output given an input and pool depth.

![X * Y = K](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20X%20*%20Y%20%3D%20K)

![\frac{y}{Y} = \frac{x}{x + X} \rightarrow y = \frac{xY}{x + X}  ](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20%5Cfrac%7By%7D%7BY%7D%20%3D%20%5Cfrac%7Bx%7D%7Bx%20&plus;%20X%7D%20%5Crightarrow%20y%20%3D%20%5Cfrac%7BxY%7D%7Bx%20&plus;%20X%7D)

| **Unit** | **Definition**                                | **Unit** | **Definition** |
|----------|-----------------------------------------------|----------|----------------|
| `X`        | Balance of TKN in the input side of the pool  | `x`        | Input          |
| `Y`        | Balance of TKN in the output side of the pool | `y`        | Output         |
| `K `       | Constant                                      |          |                |


### Prices and Slip
We can now determine the expected slip trade and the pool, based only on the input and the depth of the input side of the pool.

![P_0 = \frac{X}{Y}, P_1 = \frac{X+x}{Y-y}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20P_0%20%3D%20%5Cfrac%7BX%7D%7BY%7D%2C%20P_1%20%3D%20%5Cfrac%7BX&plus;x%7D%7BY-y%7D)

![outputSlip = \frac{x/P_0 - t}{x/P_0}  = 1- \frac{Xy}{xY} = \frac{x}{x+X}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20outputSlip%20%3D%20%5Cfrac%7Bx/P_0%20-%20t%7D%7Bx/P_0%7D%20%3D%201-%20%5Cfrac%7BXy%7D%7BxY%7D%20%3D%20%5Cfrac%7Bx%7D%7Bx&plus;X%7D)

![poolSlip = \frac{P_1 - P_0}{P_0} = \frac{xY + Xy}{XY - Xy} = \frac{x (2X + x)}{X^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20poolSlip%20%3D%20%5Cfrac%7BP_1%20-%20P_0%7D%7BP_0%7D%20%3D%20%5Cfrac%7BxY%20&plus;%20Xy%7D%7BXY%20-%20Xy%7D%20%3D%20%5Cfrac%7Bx%20%282X%20&plus;%20x%29%7D%7BX%5E2%7D)


| **Unit** | **Definition** | **Unit**   | **Definition**                               |
|----------|----------------|------------|----------------------------------------------|
| `P0`       | Starting Price | `outputSlip` | Slip of the output compared to input         |
| `P1`       | Final Price    | `poolSlip`   | Slip of the pool after the output is removed |


### Liquidity Fee

Stakers stake symmetrically and earn liquidity fees, which is proportional to slip. Slip is proportional to trade size and liquidity depth. Thus staking is incentivised in pools with out-sized trades. Instead of immediately emitting the bonded tokens, we calculate an appropriate fee, then emit tokens after the fee is removed. 

`liqFee = tradeSlip*tokensOutputted`

![liqFee = \frac{x}{x+X}*\frac{xY}{x + X} = \frac{x^2Y}{(x+X)^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B120%7D%20%5Clarge%20liqFee%20%3D%20%5Cfrac%7Bx%7D%7Bx&plus;X%7D*%5Cfrac%7BxY%7D%7Bx%20&plus;%20X%7D%20%3D%20%5Cfrac%7Bx%5E2Y%7D%7B%28x&plus;X%29%5E2%7D)

`tokensEmitted = tokensOutputted - liqFee`

![tokensEmitted = \frac{x Y}{x + X}  - \frac{x^2Y}{(x+X)^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20tokensEmitted%20%3D%20%5Cfrac%7Bx%20Y%7D%7Bx%20&plus;%20X%7D%20-%20%5Cfrac%7Bx%5E2Y%7D%7B%28x&plus;X%29%5E2%7D)

![tokensEmitted = \frac{x Y X}{(x + X)^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20tokensEmitted%20%3D%20%5Cfrac%7Bx%20Y%20X%7D%7B%28x%20&plus;%20X%29%5E2%7D)

![tradeSlip = \frac{xY/X - tokensEmitted}{xY/X}  = \frac{x (2 X + x)}{(x + X)^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20tradeSlip%20%3D%20%5Cfrac%7BxY/X%20-%20tokensEmitted%7D%7BxY/X%7D%20%3D%20%5Cfrac%7Bx%20%282%20X%20&plus;%20x%29%7D%7B%28x%20&plus;%20X%29%5E2%7D)

| **Unit**          | **Definition**                                               | **Unit**   | **Definition**                               |
|-------------------|--------------------------------------------------------------|------------|----------------------------------------------|
| `tokensOutputted` | Tokens outputted from the formula before the fee is applied. | `outputSlip` | The slip of price between input and output   |
| `tokensEmitted `    | Tokens emitted from the pool after the fee is applied.       | `tradeSlip`  | The slip of price between input and emission |
|                   |                                                              | `poolSlip`   | The slip of price in the pool after the swap |




![Price_{user} = Price_{0} * (1 - tradeSlip)](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20Price_%7Buser%7D%20%3D%20Price_%7B0%7D%20*%20%281%20-%20tradeSlip%29)

![Price_{pool} = Price_{0} * (1 - poolSlip)](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20Price_%7Bpool%7D%20%3D%20Price_%7B0%7D%20*%20%281%20-%20poolSlip%29)


### Atomic Swap Calculations

We have a single pool, TKN1, paired to Rune.  We wish to swap TKN1 to Rune. 

| **Unit** | **Definition**                                | **Unit** | **Definition** |
|----------|-----------------------------------------------|----------|----------------|
| `X`        | Balance of TKN1 in the input side of the pool  | `x`        | Input of Token1          |
| `Y`        | Balance of Rune in the output side of the pool | `y`        | Output of Rune        |

![tokensOutputted = \frac{xY}{x + X}, outputSlip = \frac{x}{x+X}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20tokensOutputted%20%3D%20%5Cfrac%7BxY%7D%7Bx%20&plus;%20X%7D%2C%20outputSlip%20%3D%20%5Cfrac%7Bx%7D%7Bx&plus;X%7D)

![liqFee = \frac{x^2Y}{(x+X)^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20liqFee%20%3D%20%5Cfrac%7Bx%5E2Y%7D%7B%28x&plus;X%29%5E2%7D)

![tradeSlip = \frac{x (2X + x)}{(x + X)^2}, poolSlip = \frac{x (2X + x)}{X^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20tradeSlip%20%3D%20%5Cfrac%7Bx%20%282X%20&plus;%20x%29%7D%7B%28x%20&plus;%20X%29%5E2%7D%2C%20poolSlip%20%3D%20%5Cfrac%7Bx%20%282X%20&plus;%20x%29%7D%7BX%5E2%7D)

![tokensEmitted = \frac{x Y X}{(x + X)^2}](https://latex.codecogs.com/png.latex?%5Cdpi%7B100%7D%20%5Clarge%20tokensEmitted%20%3D%20%5Cfrac%7Bx%20Y%20X%7D%7B%28x%20&plus;%20X%29%5E2%7D)




















![]()

![]()