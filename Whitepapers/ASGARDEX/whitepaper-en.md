# ASGARDEX

## A lightning fast decentralised exchange built on the THORChain protocol.
devs@thorchain.org

V0.1 September 2018

### Abstract 
>ASGARDEX is the first decentralised exchange to be built on THORChain, intended to break feature-parity with the world's top centralised exchanges, at the same time as being more secure, reliable and powerful than any exchange before it. THORChain is the infrastructure that supports the exchange, whilst ASGARDEX is simply a user interface. THORChain can support any number of exchanges, and all liquidity deployed to the protocol is shared by all participants. As such, THORChain adds user, developer and exchange incentives to drive strong network effects around the protocol. A wide variety of exchanges, wallets and payment services will be ultimately built on THORChain by businesses, community members and enterprise users with different features, fees and targeted user groups. Centralised exchanges with fiat on/off rails, decentralised exchanges with crypto-only trading, wallets with instant asset swaps and advanced payment services will all co-exist and be powered by THORChain. 

>ASGARDEX will be deployed to demonstrate the capabilities of THORChain and will be completely fee-free. It is intended to be ultimately forked and run by the community. ASGARDEX will allow any token and coin to be traded and swapped in a completely self-sovereign and trustless environment, with no limits or account control. ASGARDEX will be highly performant, processing trades inside a second, as well as being deeply liquid with on-chain incentivised liquidity pools. Traders will be able to trade securely, coin and token holders will be able to stake in liquidity pools to earn a return, arbitrage agents will be able to earn whilst arbitraging across liquidity pools, and users will be able to swap assets instantly from decentralised applications. 

>ASGARDEX will support limit and market orders with advanced trade types and management, such as leveraged margin trading, lending, indexes, derivatives, asset shorting and assets swaps. ASGARDEX also supports the creation of fixed supply, variable supply, non-fungible tokens and security tokens.

>ASGARDEX is part of the ambitious THORChain project and will be actively developed in accordance with public development milestones. 

### Document Set
The following whitepapers should be read in conjunction:

- [THORChain](https://github.com/thorchain/Resources/blob/master/Whitepapers/THORChain/whitepaper-en.md)
A lightning fast decentralised exchange protocol.

- [Bifröst Protocol](https://github.com/thorchain/Resources/tree/master/Whitepapers/Bifrost-Protocol/whitepaper-en.md)
Secure and fast cross-chain bridges for THORChain.

- [Flash Network](https://github.com/thorchain/Resources/tree/master/Whitepapers/Flash-Network/whitepaper-en.md)
A layer 2 Network for instant asset exchange on THORChain.

- [Yggdrasil Protocol](https://github.com/thorchain/Resources/tree/master/Whitepapers/Yggdrasil-Protocol/whitepaper-en.md)
Dynamic multi-set sharding for THORChain.

- [Æsir Protocol](https://github.com/thorchain/Resources/tree/master/Whitepapers/AEsir-Protocol/whitepaper-en.md)
A self-amending forkless consensus algorithm for THORChain. 

## Overview

[Introduction](#introduction)	
- Exchanges
- Decentralised Exchanges
- ASGARDEX

[Incentivised On-chain Liquidity](#Incentivised-on-chain-liquidity)
- Slip
- Fees
- Arbitrage
- Staking
- Balancing Stake
- Withdrawing

[Advanced Features](#advanced-features)
- Asset Swaps
- Cross-token Pairs
- Market Orders
- Index and Baskets
- Lending
- Leveraged Margin Trading
- Shorting Assets
- Trade Types
- Stablecoins

[Multi-chain and Multi-token Support](#multi-chain-and-multi-token-support)

[Permissionless and Private Access](#permissionless-and-private-access)
- THORChain Accounts
- FIX 4.4 Protocol ABI
- Anonymity

[Conclusion](#conclusion)	

[References](#reference)

## Introduction

### Exchanges
One of the most important aspects of the cryptocurrency economy is the exchange. While digital assets are useful on their own, exchanges are needed so that creators, consumers, investors, and traders can transfer these assets to one other openly and freely. As of late 2018, there are over 200 exchanges supporting a $200bn economy with over 2000 digital assets being actively traded. Whilst there is some question of accuracy, over $10bn in digital assets are reported to be traded every day. 

The current exchanges that support this economy are mostly centralised, comprised of:
- Regulated centralised exchanges that support fiat on/off rails
- Centralised exchanges that only support crypto-crypto trading
- Hybrid decentralised exchanges that marry digital assets with centralised features to pursue performance and useability

The small number of decentralised exchanges that are in use suffer from performance, liquidity and useability, and almost none support cross-chain trading. 

#### Competition
Each exchange competes for users, liquidity and mind-share, going to extra-ordinary efforts to attract traders with trans-fee mining practises, referral schemes and market-making practises to inflate volumes. As a result it becomes a zero-sum game, as there only exists a finite number of traders and their liquidity at any given time. 

#### Volatility
Most assets are held in wallets that do not add to market liquidity. Token holders become speculators as the primary reason for holding these assets simply becomes to hold for a future return. As a result markets are very thinly traded, where large orders cause large movements in the markets and assets are volatile. There is a tendency for most crypto users to accuse large traders of "manipulating" the market, although these large traders are simply executing trades in a thinly traded market. The volatility of the market is thus a symptom of the fragmented infrastructure supporting exchanges.
Over 80% of Bitcoin UTXOs are older than 3 months, and [50% older than a year](https://coinsavage.com/content/2018/08/bitcoin-data-science-pt-2-the-geology-of-lost-coins/). Thus it can be safe to assume that less than 10% of Bitcoin assets contribute to the billions of daily volume in Bitcoin trading alone. 

#### Liquidity
Most digital assets never touch exchanges, and even for assets deposited on exchanges, they are rarely used to contribute to market liquidity. Users simply want to swap assets, and are conditioned to remove their assets from exchanges promptly. Traders attempt to arbitrage markets with the minimum amount of assets needed with the minimum amount of spread necessary. As a result the "book" is normally built by the exchange itself. 
As an example, the Bitfinex Cold wallet contains almost [150k Bitcoin](https://bitinfocharts.com/bitcoin/address/3D2oetdNuZUqQHPJmcMDDHYoqkyNVsFk9r), but these assets cannot be used for market liquidity and are simply held on behalf of users. 

#### Security
Every centralised exchange has either been hacked, or could suffer from a hack at any time. The total value in assets hacked from digital asset exchanges is extremely concerning and there is no simple solution. Each exchange has to build their own security infrastructure and best practises, and the larger they are, the more of a target they become.

#### Fragmented Asset Support
Every centralised exchange suffers a technical and infrastructure burden in supporting new blockchains and tokens. New nodes need to be run, scripts need to be added, wallets need to be supported. As a result, most exchanges only support a minor subset of the market, despite there being over 2000 unique assets (and many more not yet trading due to this reason). 

#### Vulnerable to Oppression
The right to hold and transfer value should never be censored or oppressed. Building gateways and limitations around this creates an environment of low liquidity, low-efficiency markets, poor price discovery and manipulation. It is reasonable to track and limit transfers of value between the real and digital world, but purely digital asset transfers should always be unencumbered. Current exchanges are extremely vulnerable to state-level oppression, leading to asset seizures, loss of privacy and lack of transparency. 

### Solution; An exchange protocol 

The solution to all of these problems is an exchange protocol that can power any number of exchanges, facilitate any asset and support all liquidity. Such an exchange protocol could have the following features:

#### Incentivised Liquidity
Any liquidity added to the protocol adds to the liquidity of the network, improving the experience of users, traders and exchanges. If anyone could add their assets (but retain full self-sovereign control of them at any time), then assets that would typically be held on cold wallets away from the market, would add to the market and earn their holders a return at the same time. 

#### Anti-competition
With less than 5-10% of assets in circulation on exchanges, exchanges would no longer compete for the same users, traders and liquidity. Instead they could target a blue sky of new users, new traders and new liquidity; and as they joined the network, the overall experience for all would dramatically increase. This could be achieved with new trustless incentivisation strategies around using assets in liquidity pools, lending, borrowing and more freedom to move across digital assets at any time or place. 

#### Market Inertia
As new liquidity enters the network to pursue the returns paid out for liquidity, the volatility of the market would quickly decrease. All market movements would need to shift an increasingly larger pool of active, on-market liquidity. It is feasible that almost all available liquidity would flood to this new network, as it would be the first network paying a return for on-market liquidity, then quickly the network paying the highest return. This network would then smooth out the existing volatility of the market and the market would become hyper-efficient and not susceptible to low-liquidity price movements. 

#### Consolidated Assets
Once the network is established, on-chain tokens would be trivial to support, and listing would become user-initiated and requiring no input from the protocol. The burden to adding new blockchains would simply become a one-time decision on the potential cost of supporting a new node, versus the lifetime benefits of adding extra liquidity to the protocol. Once added, all exchanges built on the protocol would have instant access to the new asset. 

#### Security
Each validator on the THORChain protocol alone will be as secure as an entire legacy exchange, and the protocol is built on a super-majority consensus algorithm with many validators participating. In future, when the [Yggdrasil Protocol](https://github.com/thorchain/Resources/tree/master/Whitepapers/Yggdrasil-Protocol/whitepaper-en.md) is supported, each validator would only have the burden of running at most three different blockchains, (typically two). This will rapidly increase decentralisation, improve resilience and reduce attack vectors. 

#### Resilience
THORChain's consensus protocol, the [Æsir Protocol](https://github.com/thorchain/Resources/tree/master/Whitepapers/AEsir-Protocol/whitepaper-en.md), encourages high churn in the validator set which is open for anyone to join. With high churn, the incentives are in place to counter any malicious behaviour from validators, such as censorship, front-running or oppressive behaviour. Additionally, it means that the protocol is resistant to large numbers of validators being shut down at any time (from state-level oppression), to be replaced quickly by new validators in new regions. 

### THORCHAIN
THORChain is a new approach to this problem by building a blockchain itself to be the DEX, rather than building a DEX on an existing protocol. In this way the protocol can be optimised to solving the problems solely limited to asset exchange as opposed to adding unnecessary features such as turing-complete scripting languages. Additionally the DEX is not constrained by the limitations of the underlying protocol, as the protocol can be readily changed with on-chain governance to match the pace of innovation in the industry. 

ASGARDEX will be the first exchange to be built on the protocol. More accurately, ASGARDEX is simply a user interface that is built with THORChain as the decentralised backend. As THORChain is completely open-source, it is imagined that there will be hundreds of exchanges also built on THORChain, contributing to the same liquidity and user-base. 

ASGARDEX is part of much larger picture; that by creating a near-perfect environment for trading, the inevitable flow of liquidity and users will allow the protocol to support a much larger payment network, which will use the underlying liquidity and trustless price feeds of the protocol.

The features that ASGARDEX will bring to life on THORChain will allow it (and any other exchange built on the protocol) to break feature-parity with current centralised exchanges, as well as powering the next generation of wallets and payment services. 

The cornerstone features of ASGARDEX:
- Incentivised On-chain Liquidity
- Advanced Trading & Payments
- Multi-chain and Multi-token support
- Permissionless Access

These features are discussed at length below. 

## Incentivised On-chain Liquidity

Creating the incentives for on-chain liquidity is a cornerstone feature of THORChain. Instead of digital assets being held in accounts that don’t contribute to market liquidity, THORChain encourages users to stake their assets in on-chain continuous liquidity pools that add to market liquidity and earn their holders a return. Once assets are held on-chain, then the ratio between assets now becomes a direct indicator of asset price. Once the protocol becomes self-aware of asset prices, then advanced trustless features can be supported, which is the basis for advanced trades, lending and payment services. 

### Continuous Liquidity Pools

Continuous liquidity pools (CLPs) work by bonding two assets to each other in a pool in terms of their value. Each time an asset is placed in the pool, the opposite asset is emitted in a ratio that matches the corresponding change in value. As such, trading across a pool creates a price slip which serves as the basis for arbitrage, staking incentivisation and price predictability in the pool. The price slip is mathematically defined, and works to ensure four aspects:

1) Value always matches across the pool, no matter how large or small an asset pool is. 
2) The trade price is mathematically defined and predictable ahead of time. 
3) Those staking the underlying liquidity always earn a return on a trade. 
4) Those arbitraging across the pool earn a return on a trade. 

On-chain liquidity pools hold bonded assets at a 1:1 ratio in total value, where `value = price * amount`. If price shifts in the surrounding market then anyone can arbitrage the pool to correct the price imbalance by purchasing cheap assets (or selling expensive assets). As a result, the pool will always hold bonded assets at a price that matches external markets, else an opportunity exists for someone to gain from. As the assets are bonded together, liquidity is termed as “continuous”, as there will always be a sell-side for each buy order, no matter the price.

 <img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-1.png" width="500px" height="250px" />
 
*Figure: Rune bonded to Token at 1:1*

Here 100 Rune are bonded to 100 Tokens at a 1:1 value ratio `1 * 100 : 1 * 100`. If the token value in the wider market increases to 1.20 Rune, then the value of the Token pool is now 120 Rune. Since the assets are bonded, the 120 Tokens are collateralised by 100 Rune, which is at a 20% discount to the wider market. Anyone can now purchase Tokens at a discount by simply placing enough Rune in the pool to correct the pool value ratio back to 1:1. In this case they would place 10 Rune, receive 9 Tokens (at a 10% discount) and the pool value ratio would be back to 1:1, where `1 * 110 = 1.20 * 91`. 

 <img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-2.png" width="500px" height="250px" />
 
*Figure: Rune bonded to Token at 1:0.8 after market movement*
   
>Note: pricing here is in Rune (ᚱ), assuming a constant Rune price, but the CLP functioning as described is irrelevant to the price of Rune, and may in fact be based in $ or BTC, assuming proper $:ᚱ or BTC:ᚱ price discovery is in place. For the rest of the paper, ᚱ will be used interchangeably with $, with the assumption that the $:ᚱ market is an efficient market. 
 
### Slip

Compared to the Bancor Protocol [1], which mints “smart tokens” in a ratio that is bonded to wider market circulating supply, THORChain CLPs do not mint, and instead enforce a price slip on traded assets proportional to the trade size and existing collateral. 

Take the CLP above with 100 Rune `RUNE` and 100 Token `TKN`. If a trade of 10 Rune was made `txRUNE` the corresponding emission of token `txTKN` is defined as follows:

`txTKN / TKN = txRUNE / RUNE`

`txTKN = (txRUNE / RUNE ) * TKN`

However, this bond is purely linear and does not enforce a price slip. As such a 100 Rune trade would simply empty the entire pool of Token, leaving a `1 * 200 : 1 * 0` value ratio, which does not respect the Rule (1) above. As such, we need to price each asset in terms of the price ratio after the trade. This is done by simply adding the incoming transaction to the total Rune collateral. 

`txTKN = (txRUNE) / (RUNE + txRUNE)) * TKN`

### Fees

However, this provides no return to underlying stakers as arbitrage from one side to the other will remove any gains, which does not respect Rule (3). As such, we add a small fee that has the following characteristics:

- Proportional to trade size, where the higher the trade, the higher the fee. 
- Exponentially & inversely proportional to collateral, where the higher the slip the higher the fee.
- Placed on the side where there is buy pressure. This prevents stakers receiving assets that are under sell pressure, and inadvertently adding to the sell pressure when they withdraw assets. 

These characteristics ensure that stakers are incentivised the most where there is high volume and low liquidity, and that if they withdraw their gains they add a price-corrective function to the market. The equation is:

`txFee = tradeSlip * txTKN`

where `tradeSlip = (txRune - (txTKN * (RUNE/TKN))) / txRune`

The final bonding curve is:

`tokensEmitted = txTKN - txFee`

`tokensEmitted = (txRUNE / (RUNE + txRUNE)) * TKN - ((txRune - (txTKN * (RUNE/TKN))) / txRune) * txTKN`

Or visually:

![tokensEmitted = \frac{tx_{R}}{RUNE + tx_{R}} * TKN - ( \frac{ tx_{R} - \frac{RUNE}{TKN}}{tx_{R}}) ^{2} * tx_{TKN}](https://latex.codecogs.com/gif.latex?%5Cdpi%7B120%7D%20%5Cfn_cm%20%5Clarge%20tokensEmitted%20%3D%20%5Cfrac%7Btx_%7BR%7D%7D%7BRUNE%20&plus;%20tx_%7BR%7D%7D%20*%20TKN%20-%20%28%20%5Cfrac%7B%20tx_%7BR%7D%20-%20%5Cfrac%7BRUNE%7D%7BTKN%7D%7D%7Btx_%7BR%7D%7D%29%20*%20tx_%7BTKN%7D)

This bonding curve enforces a predictable price slip and fee on any trade, as well as ensuring that values on both sides of the pool are always adhered to; Rule (2).

The graph below indicates how this bonding curve works. As the amount transacted into the pool increases, the slip + fee increases towards 100% (where the trader receives nothing as it is all consumed by fees). The characteristics above ensure that the trade amount is always deterministic, and that the stakers receive a return. Additionally, there is no upper limit of how much can be transacted into the pool, and that the staked liquidity is protected even with very large transactions. With huge sell pressure on one side of the pool, the stakers on the buy side asset receive both asset appreciation, as well large amounts of fees. If they withdraw these fees they provide a price-corrective function and reduce the sell-side pressure. This protects the pool from a black swan event. 

With low amounts (<10% of the liquidity depth), stakers can earn up to roughly 0.1% on each trade, which matches the typical taker fees on exchanges.

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-3.png" width="500px" height="250px" />

*Figure: The bonding curve for THORChain CLPs*

### Arbitrage

To ensure that the market becomes extremely efficient and price discovery happens immediately, then arbitrage agents must be readily incentivised to arbitrage across markets. This does not refer to time-based arbitrage, where an agent will buy or sell an asset based on what they think it could or should be worth (such as the markets around algorithmic stable-coins). Instead this is purely market-based arbitrage; assets in one market are cheaper than in another, and a race condition exists to be the first to exploit the difference. THORChain CLPs will allow agents to make gains on arbitraging markets, and these gains are always deterministic. As a result, the markets on ASGARDEX will very closely match fair market price. 

As an example, we take the case that 100 Rune and 100 Token are staked. If a trade of 10 Rune was made, the trader would experience a 10% slip, and receive 9 Tokens. Assuming the wider market does not change, an arbitrager will see the opportunity of the 10% discounted Rune, and perform a counter-trade of 9.10 Tokens to receive 9.92 Rune.

This is 8% more Rune than if they had just made an ad-hoc trade across a balanced pool. Once the counter-trade is performed the final ratio has been restored to 100.9 Rune to 100.9 Token, 1:1. The stakers also receive a payout of `slip - arbitrage`, which is 0.08 Token and 0.08 Rune. 

The end result is that both stakers and arbitragers receive a gain from maintaining the price and liquidity in the pool, with a healthy return to the arbitrager for correcting the price, and a passive return for the stakers for maintaining the liquidity. Additionally, assuming the fees are not withdrawn, the liquidity depth in the pool has increased, which is more favourable to traders. 


### Staking
Staking is an inherent and important part of the protocol and provides liquidity to all assets. Due to the way that CLPs are created alongside the instantiation of digital assets on THORChain, there will always be some liquidity depth to assets. By adding incentivisation (liquidity fees), liquidity depth can be vastly increased, increasing the usefulness and value of the protocol. 

When staking, a user can stake symmetrically or asymmetrically in the pool. Despite the method of staking, the user will always end up receiving assets on both sides of the pool. The reasons for this are twofold:

1) By receiving assets on both sides of the pool the staker is hedged against any downside on one side and thus any fees earned presents a net gain in value to the staker. 
2) Staking asymmetrically creates a price imbalance that is corrected by either arbitrage or market forces, and thus results in an accumulation of assets on the unbalanced side for the staker. 

It is in the interest of the user to stake symmetrically in the pool. This is performed by making two staking transactions into the pool (either simultaneously or very immediately) with both assets. 

`stake(bal_RUNE, bal_TKN)`

Where `bal_RUNE / RUNE = bal_TKN / TKN`

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-4.png" width="500px" height="250px" />

*Figure: Symmetrically staking in a CLP*

If the staker performs an asymmetric stake-in they will cause a price imbalance that will immediately be arbitraged out, and will incur slip that is experienced on their own assets. After the arbitrage is finished, the asymmetric staker will have both assets, minus whatever slip they experienced, plus any fees they accumulated during the arbitrage. 

Here shown for the scenarios of staking from 0% to 100% symmetrically (ie 0 Rune and 10 Token, or vice versa). As shown, it is most favourable to stake 100% symmetrically; with an asymmetric stake causing a 2.5% reduction in assets. This is more pronounced at lower liquidity depths.

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-5.png" width="500px" height="250px" />

*Figure: Loss of assets after assymetrically staking and being arbitraged*


### Balancing Stake

An asymmetrical stake is balanced for the staker by the protocol simply accruing assets on their empty balance until the values on both sides match:

`priceRune * RUNE = priceToken * TKN`

Where `priceRune` is always 1, and `priceToken = 1- (TKN / RUNE)`

Incoming assets are accrued by arbitrage or natural market trades. As a result of the ensuring trade volume across the pool caused by the price imbalance, fees accumulate and the pool actually ends up with more assets than a pure symmetrical stake, shown below. Additionally, the arbitrager makes a small return on taking advantage of the price imbalance.

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-6.png" width="500px" height="250px" />
<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-7.png" width="500px" height="250px" />

*Figure: An assymetric stake-in and consequential arbitrage*


### Stake-out (withdrawing)

Assets held in pools are entirely self sovereign at all times. Users can withdraw interest or their principle at any time by signing an on-chain transaction with their private key. They can withdraw symmetrically or asymmetrically; however an asymmetric withdrawal will create a price balance that will naturally be arbitraged out, returning the staker to a symmetrical position. 

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-8.png" width="500px" height="250px" />
<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-9.png" width="500px" height="250px" />

*Figure: An assymetric stake-out and consequential arbitrage*

Here is the case of a staker removing their stake asymmetrically, causing a price imbalance on the pool. Immediately an arbitrager restores the pool balance to earn cheap tokens, and thereby returning the pool ratio to 1. In this case all stakers earn on the liquidity fee, and the asymmetric staker is balanced out. 

### Benefits

The benefits for this are ground-breaking when it comes to a digital asset exchange. 

- With deep on-chain liquidity, any wider market volatility creates arbitrage opportunities which slows down market movements, as each price fluctuation needs to “move” through the pool. The depth of the liquidity pool has a dampening effect on asset volatility and translates to a transparent and observable “market inertia”.
- With liquidity incentivisation strategies, anyone can stake assets in liquidity pools and earn on liquidity fees as the market moves from side to side. This liquidity is normally held on exchange cold wallets or user wallets and never contributes to market liquidity.
- As volume grows across a trading pair, this will translate to increased volume over the pool and a disbursement in fees to liquidity stakers. Receiving a passive return on staked assets will incentivise more liquidity to be staked which will increase the liquidity depth of the pool, improving trading experience. 
- With an observable and deep liquidity depth, large orders can be processed on-market without creating adverse reactions, as staked liquidity can’t be faked, and any price movements can be immediately arbitraged out by anyone.
- With permissionless staking and arbitrage mechanisms, it become very difficult to manipulate asset prices; as any manipulated asset immediately exposes the manipulator. 
- With on-chain liquidity pools, the liquidity pool ratio becomes a fair, open and transparent market price for the asset, which can be processed in on-chain transactions. 
- On-chain trustless price feeds enable the protocol to build a wide array of advanced features not previously possible. 

## Analysis of Incentives
THORChain incentivises every agent in the network to add value and be economically rewarded.
The following are the agents and their incentives:

- Stake liquidity in pools and be rewarded on liquidity fees.
- Arbitrage across markets and earn on price discovery. 
- Build an exchange or wallet and add maker/taker fees.
- Run a Validator and earn on block rewards. 

### Staking Liquidity
The simplest contribution anyone can make is to simply stake liquidity in pools. The value of their liquidity is always protected, they always earn on volume and their assets are always self-sovereign. Staking will be so simple, that it can be performed directly from wallets and a simple on-chain transaction is required to stake-in, stake-out or withdraw earnings.

The following is an analysis of the expected returns for staking from real-world data (missing data is extrapolated based on trade sizes and spreads), sampled in Q3 2018.

| Exchange | 24hr Volume | Number of transactions | Liquidity Depth | Ave Trade Size |
|---|---|---|---|---|
|Shapeshift (All) | $1.3m | 3000 | $15m | ~$430 |
| Bancor (Top 10) | $1.5m | 2500 | $15m | ~$600 | 
| IDEX | $1m | 2500 | $8m | ~$400 |
| EtherDelta | $100k | 300 | $2.7m | ~$330 |
| Total | $3.9m | 8800 | $40m | ~$450 |


The following are assumptions:
- The liquidity depth is staked in both the Asset and Rune, amounting to 10% of assets held on the exchange
- All trades are made at the average trade size

| Comparison | Staked Assets | Daily Earnings | Monthly Return | Annual Return | Ave Slip Size |
|---|---|---|---|---|---|
| Shapeshift Equiv | $1.5m | $720 | 3% | 34% | 0.06% |
| Bancor Equiv | $1.5m | $1200 | 5% | 57% | 0.08% |
| IDEX Equiv | $800k | $100 | 7.5% | 90% |0.1% | 
| EtherDelta Equiv | $270k | $250 | 5% | 65% | 0.25% |
| All | $4m | $890 | 1.5% | 16% | 0.02% |

As can be seen, even with 10% of circulating assets being staked, returns for stakers are very favourable, and average trade slips never exceed 25 basis points. 

If the expected return of 5% annual was the target, then the total assets to be staked would be around $8m, or 20% of circulating. However these are non-zero returns, compared to zero returns if not staking, so the target can be reduced to 1%. At this target, the total staked assets would comprise of 40% of the entire circulating assets. 

To gain an awareness of the size of the opportunity, we can attempt to extrapolate out to the entire market. The largest influence on returns to stakers is transaction size and liquidity depth. To conduct the analysis we adjust both liquidity depth and transaction size to target an annual return of 1% for staked assets.


| Transaction Size | 24hr Volume | Staked Assets | Annual Return | Ave Slip Size |
|---|---|---|---|---|
| $1k | $20bn | $1.6bn | 1% | 0.0% |
| $10k | $20bn | $5.2bn | 1% | 0.0% |
| $100k | $20bn | $16bn | 1% | 0.0% |

On analysis we can see that with even very low transaction sizes, the incentives are always present to encourage more users to stake liquidity. As liquidity depth increases, the market can facilitate even larger trades. The size of these trades are considerable, even with less than 10% of all assets staked. 

| Trade Size | Staked Assets (5%) | Trade Slip Size |
|---|---|---|
| $1m | $10bn | 0.04% |
| $10m | $10bn | 0.4% |
| $100m | $10bn | 4% |

With less than 5% of circulating assets staked, even single trades as large as $100m can be made on-market with very little impact to price. These large trades can be instantly processed by the CLPs, offering large incentives to stakers. 


### Arbitrage Agents

Arbitrage agents work to continually level the market and ensure that CLPs are balanced to fair market price. They make returns by spotting differences in value between different markets and by taking advantage of them. 

As an example, 100 Rune and Tokens are staked. A trader and an arbitrager both start with 10 of each asset. 

| Trade | Rune | Price | Token | Trader Account | Arb Account |
|---|---|---|---|---|---|
| Start | 100 Rune | 1 | 100 Token | 10 Rune | 10 Token |
| Trader in | 10 -> | 1.2 | 9.02 -> | 9.02 Token | 10 Token |
| Arb back | <- 9.92 | 1 | <- 9.1 | 9.02 Token | 0.9 Token, 9.92 Rune |
| Trade back | <- 8.21 | 0.84 | <- 9.02 | 8.21 Rune | 0.9 Token, 9.92 Rune |
| Arb In | 9.92 -> | 1 | 10.53 -> | 8.21 Rune | 11.43 token | 

After two market-slipping trades and the consequential price-correcting arbitrage, the arbitrager ends up with 15% more in assets. The trader experienced a slip, but they were expecting this. 

Using real-world data, we can see the large opportunity at hand. The assumptions in this analysis is that there would be 10 equal-opportunity arbitrage agents, and they all attempt to fully arbitrage any trades. 


| Comparison | Arbitrage Volume | Arb Size | Earning Per Arb | Daily Earnings | ROI on Assets (10%) | 
|---|---|---|---|---|---|
| Shapeshift Equiv | $1.3m | $443 | 24c | $360 | 8.3% |
| Bancor Equiv | $1.5m | $600 | 50c | $600 | 10.0% |
| IDEX Equiv | $1m | $400 | 40c | $500 | 12.4% |
| EtherDelta Equiv |  $100k | $332 | 82c | $122 | 12.2% | 
| All | $3.9m | $443 | 10c | $442 | 10% | 

This shows that arbitrage agents have more than enough incentive to continually correct markets and ensure that the pools always reflect fair market price. 

### Developer Incentives

In order to attract a wide variety of developers and businesses to build on the infrastructure and provide the tools for arbitrage and traders, there are three sources of potential revenue:

1) Protocol-level incentives as maker/taker fees. 
2) Stake assets on behalf of users and earn liquidity fees.
3) Arbitrage across markets using exchange infrastructure and existing liquidity.

Liquidity and arbitrage fees are entirely dependent on the wider market, but the optional maker/taker fees would create a price-competitive environment and would tend to zero. Staffed exchange interfaces would have no liquidity or feature advantage over staff-less exchange interfaces, so they would need to continually improve customer service and user experience to win users. 

### Validator Block Rewards

THORChain proposes a 20m Rune/year block reward, which begins as 2% and smoothly asymptotes to zero. Validators have to stake assets to enter the validator set. The economics on this are covered widely in [THORChain Whitepaper](https://github.com/thorchain/Resources/blob/master/Whitepapers/THORChain/whitepaper-en.md)

Validators host nodes, secure THORChain and are part of the on-chain governance protocol to allow continual upgradeability. 

### Summary 

All agents that contribute to the THORChain ecosystem receive adequate incentivisation. 

## Advanced Features

### Asset Swaps

Continuous liquidity pools allow for fast and predictable asset swaps from Rune to any asset in the THORChain ecosystem. Users simply place one asset in a pool, and immediately receive the other. CLPs can also be linked, allowing any token to be swapped with another via two CLPs. As an example, a user can swap TokenA with TokenB by simply trading from TokenA into Rune and then from Rune into TokenB. In this case, there would be a small slip into Rune, as well as TokenB, but this is known ahead of time. 

Asset swaps can be performed away from the trading environment, such as wallets and marketplaces, allowing users to hold any token they wish, and use just-in-time conversion to support the accepted currency. 

In such a scenario, a user may hold a certain token, TokenA, but a merchant only accepts TokenB. Instead of the user holding TokenB, they simply make a payment through the THORChain ecosystem, which performs the swap from TokenA to TokenB almost instantly and at a market price that is fair, trustless and resistant to manipulation. 

### Cross-Token Pairs

Linking CLPs in this manner also allows an exchange to support any number of trading pairs. For example, Rune is traded with TokenA on the RUNE:TKNA pair. If the user wishes instead to trade on the TKNB:TKNA pair, but does not hold TokenB, their trade makes use of the RUNE:TKNB CLP to trade into and out of TokenA without ever holding TokenB. In this case the user would incur a small liquidity fee in addition to any maker/taker fees added by the exchange.

### Market Orders

Market orders are facilitated by the CLP. On a traditional exchange a market order simply collects a number of limit orders into a single order. Typically, market orders create market slip as they remove orders from the book, and unless they are arbitraged back, the last closed market order now becomes the new price for the asset. 

With the CLPs available to use, THORChain has the unique opportunity to faciliate deterministic market orders - where the price of a trade can be calculated ahead of time thanks to the continuous liquidity present in the pools. 

CLP TokenEmission is given by:

`t = (r * T0) / (R0 + r)`

Where; 
```
t = tokensEmitted
r = Runes Inputted
R0 = Rune Depth
T0 = Token Depth
```

Thus we can process market orders by simply trading across the CLP. Arbitragers will immediately correct any outstanding limit orders. In the future we will use both limit orders and the CLP trades described above to fill market orders in ASGARDEX in cases where filling an order is not possible at the current market price due to substantial slippage. This avoids the situation where a market order is further from the current market price than outstanding limit orders on the orderbook, due to predicted slippage. 

*For this version we omit the Liquidity Fee for simplicity.* 

#### The Book

Exchanges normally include a visual representation of the “book”, which is the current aggregation of all outstanding trades. The “y axis” is the price (scale varies) and the x-axis is the cumulative total of orders moving away from the current price (in both directions).

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-12.png" width="500px" height="250px" />

A trader has an idea of how many tokens they would receive if they performed a market order, since they can see the outstanding orders that their trade would “collect” if they performed the market trade. 

Since CLPs are always available to buy and sell, we would like to visually represent the CLP depth on the book. 

#### Projecting the CLP

We know that market orders are simply CLP orders, and that CLP trade price is deterministic, we attempt to derive a formula to project the CLP on the book, such that it shows a visual representation of orders.

We can see that the input is the “slip” and the output should be the cumulative tokens emitted, such that if a trader were to make a trade at any trade size, they would know how many tokens they would receive on a market order. The larger the trade, (the more the slip), but the more tokens they receive.

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-11.png" width="500px" height="250px" />

Thus we strive to derive a formula that takes an input of slip `S` and outputs the tokens emitted `t`. 

Slip itself is a function of the final price and the starting price, defined as:

`S = P0 - P1`

Where:
```
P0 = T0/R0
P1 = T1/R1
T1 = T0 - t
R1 = R0 + r
```

Combining:
```
S = P0 - T1/R1
S = P0 - (T0 - t)/(R0 + r)
S = P0 - (T0 - ((r * T0) / (R0 + r)))/(R0 + r)
S - P0 + (T0 - ((r * T0) / (R0 + r)))/(R0 + r) = 0
(S - P0)(R0 + r)^2 + T0 * (R0 + r) - r * T0 = 0
```

Recognising the quadratic formula:
```
ax^2 + bx + c = 0
x = (-b +/- sqrt(b^2 - 4ac)) / (2a)

a = (S - T0/R0)
b = -1 * (2 * T0(S - T0/R0) - R0 + T0)
c = (T0^2 * (S - T0/R0) + R0*T0)
```


Thus:

`t = (r * T0) / (R0 + r)`

Where:

![](https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-14.png)

*Note: the subtraction is the correct output in this case.*

This now elegantly solves the solution, by taking an input of the CLP depth and the slip to compute at, and returning the tokens that are expected to be emitted. The only inputs are:

```
R0, CLP Rune Depth
T0, CLP Token Depth
S, Slip to compute at
```

This equation has the following visual output, which is a smooth increasing book. At each price point, it is clear how many tokens will be collected by the trader by performing a market order:

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-13.png" width="500px" height="250px" />

#### Adding Limit Orders

The book should also have limit orders placed on it. They simply add to the cumulative total of tokens emitted. 

### Indexes and Baskets

A powerful feature of the CLP is that multiple assets can be grouped on one side of the pool, and linked as collateral to a third asset, which represents the homogenous collection of all grouped assets. If a user wishes to create a token index of 2 grouped coins, they simply create a new token, but link the token to the CLPs of the two coins of choice. Now, whenever a trade is placed into the CLP Basket, the Rune is swapped into the two grouped assets via the relevant CLPs of those assets. The assets are retained in the pool, and a third token is atomically minted at a 1:1 ratio of the assets, and issued to the user.

If a user wishes to sell their index token against the CLP, they simply send in their tokens, which are immediately destroyed in the pool. The corresponding amount of underlying assets (pro-rata to the index) are then sent via the external CLPs to swap into Rune, which is then issued to the user. 

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/ASGARDEX/images/asgardex-10.png" width="500px" height="250px" />

*Figure: A token Index*


Such a pool would present a number of arbitrage opportunities in order to keep the index re-balanced with respect to the total value of the grouped assets and collateralised Rune. A good example of this is are stablecoins. A basket of stablecoins using assets from different implementations would then be far less risky than any individual stablecoin. The pool would be constantly re-balanced by arbitrage agents, which in itself provide better assurances of a recovery from natural market fluctuations around the assets. 

### Lending

Lending in crypto-currencies is always fully collateralised (often largely over-collateralised) which is used to under-write the asset that is issued to the borrower, typically a stablecoin. If the underlying asset-base decreases in value, then the collateral is liquidated to keep the collateralization ratio constant. THORChain can support such a scheme trustlessly by simply referring to the CLP price feed between the collateralised asset and the lended asset, and making liquidations on behalf of the lender. As the CLPs are actually hyper-efficient markets (there is no spread), the collateralisation ratio can be reduced to 100%. Additionally, low volume coins can also be lended against, by tracking the liquidation price of the asset if it were 100% liquidated in a single trade. 
As an example TokenC is a low volume coin, with 10,000 staked in a pool with 100 Rune. The conversion is 100:1. If a borrower held up 10,000 of TokenC as collateral, then they can be permitted to borrow only as much as if it were liquidated in a single trade, which is deterministic (around 37.5 Rune). If the price of TokenC increases to 120:1, then the collateral is only worth 36 Rune (after liquidation). As such, around 200 TokenC is progressively liquidated on behalf of the borrower in order to reduce the debt down to 36 Rune. 
These automatic liquidations can be performed by validators, but they can also be performed by relayers who scan for bad debt and perform the liquidation transactions in return for a small fee. 

Using the same mechanism, interest payments can also be performed trustlessly on the borrowed asset, by withdrawing from the collateral and converting to Rune. 

Blackswan events may still occur, but the automatic and progressive liquidation of collateral against a CLP with a deterministic liquidity depth far reduces the risk. The main risk comes from stakers in liquidity pools removing their assets which will reduce the liquidity depth sharply, causing large amounts of collateral to be liquidated fast. However liquidation events from TokenC to Rune cause earnings to accrue quickly (in Rune) for any remaining stakers. Due to the design of  CLPs, staking is most favourable in high volume low liquidity pools, so the large liquidation event should encourage more staking, in return restoring the liquidity depth. 


### Leveraged Margin Trading

Leveraged margin trading crypto-currencies involves putting up collateral and receiving assets on a multiple (leverage) that can be traded. As an example, if a trader puts up 1 Bitcoin to trade at 100X leverage, they are lended 100 Bitcoin. If the borrowed asset incurs a loss, the collateral is automatically liquidated to cover the borrower, at the correct ratio. The borrowing, interest payments and automatic liquidation of such assets is the same for Lending above.

Validators or relayers track downstream assets that have been borrowed, and constantly refer to the CLP price in order to determine the asset value. In this way they can deterministically ascertain if a trade has resulted in a loss of value, regardless of the asset itself. If this is the case then they can liquidate part of the asset holdings in order to protect the collateral. 


### Shorting Assets

An asset is shorted by a trader borrowing the asset from a lender, then immediately selling it (for $USD). If the asset decreases in value (in $USD), they can buy it back for much less, and then pay out their debt to the borrower. Any difference between the initial sell price and the final re-purchase price is a net gain for the shorter. 

THORChain’s CLPs permit shorting of any asset by combining the Lending & Liquidation features above, in addition to the functionality of the CLPs. Further, they can also allow shorts to be priced in any currency of value to the trader, not just $USD or BTC. For example, a trader may short TokenD against TokenB. In this case, they borrow TokenD and sell it for TokenB. If TokenD reduces, they can buy it back with their TokenB holdings and pay out their debt. 

Traders can also perform leveraged shorts by trading with a leverage ratio. In this case their gains (or losses) are amplified, but borrowings can be liquidated as required to prevent a loss to the lender. 

### Trade Types

Fill or Kill
All or Nothing
Immediate or Cancel

### StableCoins 

THORChain’s macro vision is to create a highly liquid payment network built on a completely trustless structure. An imperative feature for mainstream adoption are stablecoins that are pegged to existing fiat currencies such as USD, YEN, EURO and AUD. The first way to achieve this is to simply tokenise existing stablecoins, while the second is to support the development of stable coins on the platform. The first will naturally be easy if the bridges in `§ 8` are built. 
THORChain has all the required features to create StableCoins with auditable supply and collateral using a Variable Supply token and its CLP and full Validator Set participation. The following would be the process:
- A tokenChain `tUSD` is created by the Validator Set. A `Rune:tUSD` CLP is created that is variable supply, requiring `2 / 3` signatures from Validators, or by a on-chain smart contract.  
- At each round, Validators (on smart contract) propose a price `$` that the Rune is valued at. They can infer this by any means possible, most likely by reading APIs off a conglomerate of external exchanges of Rune. Validators can also nominate Rune pricing by watching Bitcoin pricing off external exchanges, and converting to Rune price by the `Rune:tBTC` price feed. 
- At each round `n + 1` the median of nominated prices is stored in the block. Outliers may invoke slashing rules to penalise poor price nomination. 
- As Rune price fluctuates, `tUSD` supply in the CLP is negatively changed by the Validators. As an example, Rune price decreases by `2%`, so `tUSD` Supply increases by `4%`. This causes `tUSD` to become inflated and cheap. 
- Self-interested arbitrageurs will then send in Rune to buy cheap `tUSD`, until `tUSD` returns to `1:1` backed in Assets.
- Additionally, the liquidity fee will increase the staked collateral in the CLP to match volume and reduce slip. 

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/THORChain/Images/figure38.png" width="900px" height="246px" />

*Figure: Collateralized on-chain StableCoins.* 

This process can be repeated for any other fiat currency and is very simple. Once an external price of Rune is set (in the fiat currency), then the protocol deliberately creates arbitrage opportunities by influencing money supply to attract third parties to act in a self-interested manner to restore any price imbalance. By requiring full Validator Set participation in the price nomination the price of the StableCoin can be relied upon with the same assurance as the entire protocol itself.  The pricing/supply feedback loop can be modified to reduce damping and price sensitivity. 

### Token Baskets  & Indexes
A THORChain can go further than a single token being represented in a CLP. With a combination of CLP scripts and trustless price feeds, token baskets and indexes can be created and represented by a single asset. This allows users and traders to carry a single token and know that the token’s price trustlessly represents other assets.   
A new tokenChain `TKNIndex` can be created that represents `TKN1`, `TKN2`, and `TKN3`, where the `TokenData` and `CLPData` for `TKNIndex` is linked to the CLPs of the indexed assets. The `TKNIndex` CLP is bonded to include liquidity in all other CLPs so the price of `TKNIndex` is thus representative of the linked assets. 

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/THORChain/Images/figure40.png" width="350px" height="223px" />

*Figure: Token Baskets*

## Multi-chain and Multi-token Support

THORChain will implement the [Bifröst Protocol](https://github.com/thorchain/Resources/blob/master/Whitepapers/Bifrost-Protocol/whitepaper-en.md) to allow support of all tradable assets, no matter the originating chain. The Bifröst Protocol is essentially a trust-minimised bridging protocol that does not require any change to the bridged chain, and uses the security of the THORChain ecosystem to ensure that assets never present a viable honeypot to any adversary. This allows assets to be moved seamlessly on and off the ecosystem.
Bridges to THORChain are supervised by THORChain validators in multi-signature accounts, but by randomly reshuffling the signatories and having multiple bridges with different security and performance metrics, each bridge maintains optimal performance whilst being supervised with full protocol security. If a validator attempts to spend locked assets they are slashed and the seized assets can be used to restore the assets. With the use of CLP price feeds the protocol can become self-aware of the risks of each bridge, and make adjustments to signature requirements. 
Tokens on THORChain gain low fees, on-chain liquidity, and a superior trading environment, and all assets can be used by traders to stake inside CLPs to earn on liquidity fees, so `tCoins` will likely be more valuable than original assets. Tokens created on THORChain can also be easily deployed on multiple other chains but recovered easily. 


## Permissionless and Private Access

### THORChain Accounts

There is no restriction on who can generate a THORChain account and trade from it, and trading has no limits. Indeed, there is no restriction on who can enter the ecosystem via the Bifrost Protocol, and no limits on those assets movements. As there is no restriction on who can become a THORChain validator, and there are correct incentives for a large group of active and standby validators, there are several layers of redundancy to the ecosystem. THORChain is a protocol that simply allows for the transfer and trading of assets, it does not enforce any level of account management, control or censorship.

In order for juridictionally compliant exchanges to be built on THORChain, it is up for the exchange itself to add a KYC/AML layer and an account management system. The exchanges best placed to do this are those with fiat on/off ramps. 

Additionally, in order for Security Tokens to be traded and supported on THORChain, it is up for the exchange layer to add an account whitelisting feature to ensure tokens can only be bought/sold between registered users. 

### FIX 4.4 Protocol ABI

FIX 4.4 is the Foreign Information Exchange protocol built for trading desks to place trades such as indications, orders and executions in a standardised and efficient way across a network. It has been adopted as the standard electronic trading protocol and THORChain intends to build for FIX 4.4 compatibility to allow liquidity and access to institutional traders and investors. 
The following message types are commonly used in FIX 4.4:
- Indication of Interest
- Quote Request
- Quote Response
- Quote
- New Order
- Execution Report
- Allocation Instruction 
- Allocation Report
- Trade Capture Report
- Application Blockchain Interface (ABI) bridges the protocols and allows orders to be generated on Layer 1 or Layer 2 depending on liquidity needs and order types. 

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/THORChain/Images/figure41.png" width="350px" height="400px" />

*Figure: FIX 4.4 implementation proposal.*

### Anonymity

THORChain can implement the [ZeroCoin Protocol](http://zerocoin.org/media/pdf/ZerocoinOakland.pdf) to allow re-spawning of accounts to prevent linkability. Tokens are destroyed in one transaction and then trustlessly spawned in a new coinbase transaction. To prevent temporal analysis tracking identity, Alice can specify a block height delay to the re-spawn of her account. To prevent temporal analysis identifying immediately appearing tokens with immediately disappearing tokens; a variable wait time can be set to increase noise.

<img align="center" src="https://github.com/thorchain/Resources/blob/master/Whitepapers/THORChain/Images/figure39.png" width="350px" height="298px" />

*Figure: Anonymity.*


## Conclusion

ASGARDEX represents a new frontier of exchanges, with permissionless access, on-chain incentivised liquidity and advanced trading features. THORChain, the protocol that it is built on, will power the next generation of exchanges, wallets and payment networks.


## References

[1] Bancor Whitepaper, Eyal Hertzog, Guy Benartzi, Galia Benartzi, 2018,  https://storage.googleapis.com/website-bancor/2018/04/01ba8253-bancor_protocol_whitepaper_en.pdf
