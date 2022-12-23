# Prop Auction

Auction house applies Last Price Dutch Auction pattern to auction fixed numbers of Props every day.

1. Every day from 00:00(UTC), 10 types of Props are available for biding
2. Props will reduce $Energy price by 2% every 10 blocks (about 2 mins)
3. Players can pay the current price of $Energy to buy Props anytime
4. When there is a deal, the price of that Props stays for another 10 blocks (about 2 mins)
5. When all the Props are sold or 6600 blocks have passed, the auction of the day is over, Props unsold will be burn
6. Bidders who pay higher $Energy will receive a refund

<figure><img src="../../.gitbook/assets/Prop Auction.png" alt=""><figcaption></figcaption></figure>

**LPDA is helpful for easing the biding concerns in order to have a more realistic reflection of the relationship of demending**
