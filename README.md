##  MakerDAO - Arbitrary To Algo 💡


![High level overview](https://cdn-images-1.medium.com/max/1067/1*h9KnYXn-DHZLqknRV3zk5A.png)

MakerDAO's value proposition is stability. There's a few key things that effect stability, I believe the primary contributors are:

- Information - How much does your audience understand about the system they're participating in? A long-term BTC holder is going to have stronger hands during a 30% drop in price, whereas a newer BTC holder may not be as informed, and thus "weak" hands in situations that may be short-term troublesome.

The blackswan risk for MakerDAO's system is not the same if Alice Smith was the only CDP holder compared to Joe Lubin being the only CDP holder.

- Predictability - Any scenario where there's volatility, be it in cryptocurrency markets, or sports, or games carrying mixture of skill & chance. The more information that your opponent has in advance, the more they can attempt to predict a certain number of potential strategies that they may be faced with. Like knowing the lineup that will be played for the superbowl team, a coach will use that to mitigate any potential variance.

- Something else that I've forgotten because I had it on a shitty gist.

#### 🤖Data driven decisions for the following:

* Debt Ceiling (SCD & MCD).
* CDP ownership/accessibility.
* Stability Fee.
* Dai Savings Rate.
* Oracles & Pricing.
* Collater Pool.

#### 🗳Governance driven decisions for the following:

* Exchange venues eligible for price discovery.
* Oracles integrity and transparency.
* Market maker incentives.
* Strategy to introduce new asset classes (native on-chain BTC vs tokenized property/securities)
* Newer assets to be introduced to the the system.

The further evolved a system becomes, the harder it is to make changes. Early decisions have ongoing effects. Imagine what the ecosystem would look like today if we saw Satoshi create irreversible digital currency and go push it weeks later on gambling and adult forums as a payment method. The shortsighted approach would'nt have given us the foundations we've got today. Similarly to MakerDAO being selective in MKR issuance, instead of spraying and praying. Tight foundations are absolutely necessary for a system over the long term.

Below are a series of calculations that I believe construct a more liquid, more scalable & predictable system. Removing the key variables that challenge the core value prop. Stability.

Theoretically hitting the reset button on the system. 0 CDP's open, 0 collateral, 0 collateral pool.

## 💸 CDP's 
- 0 CDP's available in the system. To generate a CDP, a verifiable on-chain trade must be completed between the collateral and the stable asset. DAI/ETH trade.
- 1 CDP is able to be generated for every on-chain trade that is verifiable (e.g. a DAI/ETH trade on Uniswap).
- The person who completed the trade receives an ongoing decaying portion of the stability fee's paid on that specific CDP, or is paid a portion of the Dai savings rate paid out. Similar to a mortgage broker driving leads to a bank branch.
- Maker does a trade, system generates a new CDP that's eligible for use (of which the maker is the owner, but not necessarily the CDP holder) Bank (MakerDAO system) --> Mortgage Broker (the maker, capturing benefits from bringing the collateral to the CDP --> Home buyer (end user looking for leverage on-chain). 

### Q: Why would we not have infinite CDP creation?

A: Remember the scene in the big-short where they found the mortgage brokers who are farming out debt to anyone who will take it. While it's not an over-collateralized system like MakerDAO, it's similar in that the introduction of weaker hands or less-educated market participants can bring down the house. CDP accessibility is critical, but it is not critical today, it's critical long-term. When random bob citizen hears about this crypto thing going up and he buys in, he is more risk to the system than an OG long-term perma bull. To the hodlers reading this, you don't see blackswan events as bad, you see them as a chance to BTMFD (Buy the dip). Your hands are strong, and provide a stronger base to the system wide risk tolerance. More trades on-chain that are 100% verifiable means a healthier more aggressive trust-minimized price discovery mechanic. The stronger the rate is, the harder it is to enduce slippage relative to the liquidity of the system. So throttling CDP accessibility provides an incentive for on-chain broader distribution of price discovery instead of from a handful of trade teams. Healthier and stronger.

### Q: Why pay ongoing reward for these price-discovery/passive traders?

A: Two main reasons
    a) System-wide this carries much broader diversification of participation over TWAP over n blocks. Stronger price             integrity.
    b) Passive contribution *and* income to participants in other. While mitigating risk through diversified price-discovery , it's passive adoption of DAI if they're being rewarded having not felt like they've done anything. In fact, they've done something very meaningful, contribute to price discovery. Provides a stronger adoption for businesses/merchants/etc also... Startups like Uniswap for example could be receiving all this as an additional revenue for liquidity providers. As easy as buy some token on an exchange portal or something so passive. Plus all others built on top of those exchanges.
    

##  📈 Debt ceiling

![Current Example](https://cdn-images-1.medium.com/max/1600/1*dyR8_deTfz1NVwPkqMOivg.png)
The debt ceiling is for mitigating risk. Risk exists through poor price discovery relative to how large the system is. So we're going to compare the miner fees paid on eligible on-chain trades. The proportion of the total block-reward divided by the number of collateral types will help give guidance to the risk levels. 

Debt ceiling is calculated as follows:
```
([Price discovery fees paid per block / Total block reward] x Number of CDP's in the system) / Number of collateral types)
```
Example

```
([0.00042 / 2.16] x 9607) / 1) = 1.868% 

Debt Ceiling = 1.87% of ETH Total Supply.

Debt Ceiling = 1,972,231.91 ETH

```

_Note: Current Debt Ceiling is at 2.2M ETH_


### Q: How do we increase the debt ceiling then?

   A: To increase the debt ceiling, complete more on-chain trades relevant to the total block reward.

### Q: Oracles just disappear? Surely not?
   A: No, they still are pushing their rates on chain, and they'll be utilized in the next section.
   
## 🔮 Oracles Role

Oracles are fundamental parts of the system. Right now, predictability gets effected here. There's a stronger way to do it IMO.

The issue that occurs with a select few oracles presently is that:

1) Largely a "security through obscurity". Do not reveal who they are, which I understand the motivations. Hard to scale to a multi-trillion Dai float without ironing this out. A fantastic start so far, but thinking further ahead it seems like the biggest vulnerability.

2) Exchange selection is not verified or transparent. We all know that CMC is garbage, and only certain exchanges carry enough integrity to truly give an accurate price indication. To mitigate this, most trade venues evaluate this counter-party risk by hitting their books and discovering how much slippage there was. The less slippage, the more honest the numbers that are being claimed.

3) Multi-variant environments. Exchange fee's on one platform, differ to another, and withdraw limits, regulations, etc... All wrap up into oracle pricing. Which is not entirely inaccurate, it's just misleading to a larger dataset that is relying on it. For comparison, it'd be like in 2017, the Kimchi premium 33% arbitrage between South Korea ETH price, and the USA ETH price. _Additional context at the bottom for you.

### Q: So what do oracles do then?

   A: They're piping in the price, from *eligible* exchanges which have been voted in by MKR holders. E.g. Coinbase, Kraken, Gemini, Bitfinex, Binance, whoever. Messari "Real 10" perhaps? Or whatever. The agreeance should be whether it is top of the orderbook, 100 order, 1000 USD order? Etc...

## 🏆 Stability fee

Relatively straight forward. We're going to find the gap between the two price feeds. On-chain price discovery of DAI/ETH and compare against USD/ETH price feeds from oracles.

D*Cp

D = Delta between on-chain price (as above) vs oracle pricing. Always Dai/collateralType va USD/collateralType.

Cp = Collateral pool. Could adjust this to a hard collateral ratio which would most naturally be 225%. 225% global pool is 1.5x of the local collateral requirements.

Current example
*Note: Negative number implies a fee to be paid (E.g. stability fee). Positive number would imply a reward (Dai savings rate, or similar incentives to compress the ratio to be ~1:1)
				
DAI/ETH = 169.854

USD/ETH = 162.935

Delta = -4.07%

Collateral pool = 387.00%

**Result**

Upper (1.5x collateral pool target) = -15.76%

Lower (2.25x collateral pool target= -9.1654%

**Stability Fee = Range -15.76% <> -9.165%**

### Q: What's the collateral pool got to do with it?

   A: The system is not supposed to be excessively collateralized, it's supposed to be over-collateralized to a certain point. Beyond that, it becomes dorment and passive participation in the CDP system, which is not efficient and overtime will become largely problematic. I'd suggest dividing collateral pool requirements for CDP's locally & then MKR systemically.

The change in PETH (# of the underlying asset) has been within 2% over the month (March 13th - April 13th) where we've seen the price of the underlying shift 20%, resulting in the collateral pool ratio growing 305% - 385%.

CDP's are 1.5x, 1.5x system wide over collateralized gives the passive CDP participants motivation to get out of their unused CDP, and avoid fees etc... With finite amount of CDP's, people should be putting the CDP to work and then leaving the system.
   


## 🏘📊Collateral Asset Category 

The whole MakerDAO system is reliant on overcollateralizing to insulate risk. This works if the asset lives on-chain (Digitally native) because we have guarantees for being made whole. Recourse is a dimension of risk. The less certain or predictable it is, the more risk is introduced.

With multi-collateral Dai I believe that before we choose assets we need to specify categories. Solving problems now, means they can be productized if they scale. Done correctly, it will result in multiple price feeds on-chain, which are the most battle tested and create an opportunity for productizing those feeds.

First pass at some categories that I see (in order of priority):

* Digitally native (ETH, REP, REN, ETC, BTC).
// Cryptographic recourse, 100% verifiable. Smart contract shows me getting paid if x scenario happens. 

* Digital representation of non digital currencies (e.g. Fiatcoins, Digix, etc...).
// Part cryptographic recourse - Part legal system. Sure the smart contracts are in place, but also I have regulatory bodies I can speak to if I'm not honored my 1:1 redeeming the Fiatcoin from the vendor.

* Digital representations of assets (Security tokens, property ownership put on chain, etc...
// Under-developed legal system that'll take time to get caught up. Resulting in more risk due to more ambiguity in the legal recourse procedures.

## 💹 Collateral Asset Selection 

Some earlier thoughts on the premise of predictability of incoming collateral, trends, ceilings and volume. Provides the system the ability to forecast and plan accordingly. Can be found [here](https://www.reddit.com/r/MakerDAO/comments/aqxg7p/mcd_pooled_collateral_competition_split_the/?st=jtqwtlik&sh=f90b4da4) if interested



Extra 1:  System Calculator (Thrown together) - https://docs.google.com/spreadsheets/d/1Udo_meYUy_knO3urrbBK8X56vnMpYERLhto2WBxpV7A/edit?usp=sharing


Extra 3: That's because of additional factors like capital restrictions which means if you get the money into the country, you're unable to send it back out. Great if you're offering a remittance service to South Korea, not optimal if you're trying to find the trade, execute, realize profit, reinvest, rinse/repeat. The capital outflows is your choke point so you aren't able to realize the arbitrage. Thus the premium stays for far longer than most would expect it to. Comparatively in the real world, USD to China is done as USD to CNH very frequently. Because the on-shore restrictions that exist in China (like South Korean example). So what they do, they typically don't compare CNH/CNY because it's largely not apples to apples. They compare USD/CNY to USD/CNH and try use that.




