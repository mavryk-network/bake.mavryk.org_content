---
title: "How to Bootstrap"
weight: 1
type: docs
summary: MavBake Bootstrapping Tutorial
---

## MavBake Bootstrapping
To bootstrap your MavBake node means to download someone else's snapshot of the blockchain and import it into your node. This is much faster than synchronizing the blockchain from scratch. There is a way to quickly bootstrap your node using a snapshot and a way to bootstrap your node using a snapshot and a block hash. The latter is the most reliable and robust method but it is also the slowest. The former is faster but it assumes you trust the source of the snapshot.

**Please be aware that bootstrapping your node could result in your nonce revelation to fail and for you to forfit your endorsement rights for the cycle.** This is because by default we're using rolling snapshots which don't export full blocks for past cycles by default. If your node baked a special kind of block during the last cycle, it may be asked to provide its nonce to the network. To do so, it needs to have the `.mavryk-client` data intact from the last cycle and it needs to have the full blocks for the last cycle.

To remedy this situation and to never risk forfitting your endorsement rights for a whole cycle, you have to use a snapshot that's at least 5-6 days old (from today), when bootstrapping a node. You also have to not wipe out or to move your `.mavryk-client` directory. This way you'll always have at least 1 cycle+ of full blocks in your node's database as well as the nonce file on disk. The downside of this method is that it will slow down your bootstrap process by the amount of time it takes to download the full blocks for the past 1 cycle+, which can be up to 2 hours on some slow home networks.

### Bootstrap using a snapshot
You can get Mavryk node snapshots in the following place run by Mavryk Dynamics 
* https://snapshots.mavryk.org/

*Before bootstrapping your node, made sure to stop your node as shown below.*

Using the first bootstrap method below ensures that the snapshot is checked for consistency both programmatically and by your checking the blockchain explorer(s) to confirm the block hash. This is the most reliable and robust method but it it also the slowest.

   ```
   mavbake stop
   mavbake bootstrap-node <url> <block_hash>
   mavbake start
   # example:
   mavbake bootstrap-node https://snapshots.mavryk.network/rolling BLVo8bPM1MU2h6dnKkxHkRmXcEigQbtLd9XwNrCHbKEwERSgZDy
   ```

> You can replace `eu` above with `us` or `asia` if you prefer to use a different mirror closer to you.

Get the block hash and block level from the snapshot provider's website:
https://snapshots.mavryk.network/rolling.html

> The `<block_hash>` argument is optional but encouraged. If you don't want to borther with this protection, use the second method below which will also be faster.

Verify the hash/checksum provided by the snapshot provider to ensure the snapshot is valid. You can find the correct hashes for all blocks on Mavryk blockchain explorers such as:
https://tzkt.io/blocks
https://tzstats.com/

Simply search for the block level in the search field and verify the hash of the block matches the hash provided by the snapshot provider.

Using the second bootstrap method below is faster but it assumes you trust the source of the snapshot. Sometimes one doesn't have a choice and must make such trade-offs when time is of the essence.

   ```
   mavbake stop
   mavbake bootstrap-node --no-check <url>
   mavbake start
   # example:
   mavbake bootstrap-node --no-check https://snapshots.mavryk.network/rolling
   ```
> You can replace `eu` above with `us` or `asia` if you prefer to use a different mirror closer to you.

---

Any questions/comments/concerns? Please contact the Mavryk Dynamics team on
[Telegram](https://t.me/MavrykNetwork) 