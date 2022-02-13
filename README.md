
             .   ,  ,.  ,-.      ,     ,.  ,-.             
             |\ /| /  \ |  \     |    /  \ |  \            
             | V | |--| |  | --- |    |--| |  |            
             |   | |  | |  /     |    |  | |  /            
             '   ' '  ' `-'      `--' '  ' `-'             
# The Challenge

This is the submission for the Optiver Challenge of the Hex Cambridge hackathon in January 2021. 
We have developed an automated strategy for dual-listing of a fictional stock "Philips" A and B,
which is traded on two - differently liquid - exchanges.

# Market Arbitrage Dual-Listing Algorithmic Delta (Neutral) 

Market Arbitrage Dual-Listing Algorithmic Delta (Neutral), AKA **MAD-LAD**, is a 
delta-neutral market-making algorithm that trades on the illiquid market and 
instantly hedges on the liquid market.

By continuously holding both a bid and an ask in the illiquid market, making 
sure that the bid-ask spread for `Philips_B` that we set is always wider than the
bid-ask spread for `Philips_A`, we can always immediately hedge our position on 
the more liquid market while making a profit. Thus, this algorithm is characterized
by an extremely low risk, by having a total position close to zero.

In order to decrease the risk even more, the algorithm includes a *"pillow"* 
which ensure a minimum profit for each trade, avoiding low–profit trades.

In the long run, as the market randomly moves, the difference in times our 
bid and our spread are met will tend to zero, essentially cashing in the profit
from the initial position. However, in order to ensure that the positions in the
two instruments do indeed approach zero, *"unwinding"* is performed. This is achieved by
transferring positions from the instrument with negative positions to the other when 
the trade is profitable or neutral. Thus, the profit made by the algorithm is 
always a real profit and not a virtual, by never holding unbalanced positions.

The algorithm showed steady increasing profit, with low–risk and discrete profits. 
