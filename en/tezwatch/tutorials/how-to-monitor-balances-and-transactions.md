---
title: "How to Monitor Mavryk Balances and Transactions"
weight: 1
type: docs
summary: TezWatch Balances & Transactions Tutorial
---

## How to monitor Mavryk balances and transactions with TezWatch

Using TezWatch you can keep an eye on transactions to and from baker wallets or baker payment wallets with flexibility.

You can monitor some of the following aspects:
- Transfers in/out in amounts greater than X but less than Y
- Notify when balance falls below X

> If you want to remain anonymous, you can create a new Discord account and join our Discord server using that account. Then you can DM the TezWatch bot from that account and what with it in private.

To get all "sources" and "events" use the `/events` command

| ![<Slash Events>](/tezwatch/tutorial/tezwatchSlashEvents.png) |
|-|

Here are the descriptions of all the key variables you will need to configure to monitor balances and transactions:
| Variable    | Available Options                          | Description                                                                                                                                                   |
|-------------|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `source`    | `wallet` | The general area of interest. `staking` is related to activities that validate on the chain and `chain` is related to general chain progression               |
| `event`     | `transfer`, `balance-updated` | These are the specific staking events that you're interested in being notified for. Each event has its own unique subscription tier. All `missed*` ones are TIER 0 or FREE |
| `conditions` for transfers | `mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g:in`, `mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g:in>1`, `mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g:50>in>1` | Be nofified for all incoming transactions, all incoming transactions over 1 or all transactions smaller than 1 but larger than 50 |
| `conditions` for balance-updated | `mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g:50>balance` | Be nofidied for all incoming transactions, all incoming transactions over X or all transactions smaller than X but larger than Y |

> Please note that some TezWatch features are considered premium and will in the future require a subscription. The freemium features indicated as TIER 0 will always be available for free to the Mavryk ecosystem.

### Transfers Examples

Here's an example of subscribing to all incoming transactions to the wallet mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g

| ![<Incoming transfer>](/tezwatch/tutorial/tezwatchIncoming.png) |
|-|

Here's an example of subscribing to incoming transactions to the wallet mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g of over 1 mav

| ![<Incoming transfer>](/tezwatch/tutorial/tezwatchIncomingMore1.png) |
|-|

Here's an example of subscribing to incoming transactions to the wallet mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g of over 1 mav but less than 50 mav

| ![<Incoming transfer>](/tezwatch/tutorial/tezwatchIncomingMore1Less50.png) |
|-|

### Balances Example

Here's an example of subscribing to the wallet mv1V4h45W3p4e1sjSBvRkK2uYbvkTnSuHg8g's balance being below 50 mav.

| ![<Incoming transfer>](/tezwatch/tutorial/tezwatchBalance50.png) |
|-|

---

Any questions/comments/concerns? Please contact the Mavryk Dynamics team on
[Telegram](https://t.me/MavrykNetwork) 