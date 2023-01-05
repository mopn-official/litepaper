# Auction

Auction House applies Last Price Dutch Auction pattern to auction fixed numbers of POM every day.

1. Every day from 00:00(UTC), 10 kinds of POM are available for biding
2. POM will reduce the $ENERGY price by 2% every 10 blocks (about 2 mins)
3. Players can pay the current price of $ENERGY to buy POM anytime
4. When there is a deal, the price of that POM stays for another 10 blocks (about 2 mins)
5. When all the POM are sold or 6600 blocks have passed, the auction of the day is over. POM unsold will be burn
6. Bidders who pay higher $Energy will receive a refund

**Starting Price of POM:**

| **POM**       | **Starting Price ($ENERGY)** |
| ------------- | ---------------------------- |
| Health Gem    | 500                          |
| ATT Gem       | 2,500                        |
| STA Gem       | 1,500                        |
| Venom         | 100,000                      |
| Disarm Field  | 100,000                      |
| Iced Cage     | 200,000                      |
| Pause Capsule | 200,000                      |
| Oscillator    | 200,000                      |
| Purge Laser   | 200,000                      |
| Terminator    | 100,000,000                  |

LPDA is helpful for easing the biding concerns in order to have a more realistic reflection of the relationship of demanding.
