---
title: "How to Update"
weight: 1
type: docs
summary: MavBake Updating Tutorial
---

## MavBake Updating
The MavBake software consists of four components:
1. ami - App management engine: templating and orchestration - https://github.com/alis-is/ami
2. eli - Lua Interpreter & Essential libraries for simple cross platform scripting - https://github.com/alis-is/eli 
3. mavbake - Command line interface for setting and monitoring your baker, using the help of the two tools above
4. Octez binaries - Tezos node binaries published by the Tezos core developers - https://gitlab.com/tezos/tezos/-/releases

We regularly update all parts of the MavBake stack and the Tezos core developers regularly publish new Octez versions and protocols.  All mandatory updates and optional updates are posted across Tez.Capital social media channels.  Updates must be performed manually at this time, to ensure the Tezos node operator is the only person able to control their baking operation.

### Which MavBake upgrade method should I use?

We will sometimes specify which upgrade method to use by referencing its letter.  If a letter recommendation is not specified, use the guidelines below to determine which method to use:
* (A) This upgrade method works in most cases. The only component not updated is the mavbake binary itself.
* (B) This upgrade method is used when you want to update the Octez binaries only. This is useful when old protocol binaries need to be removed from your baker.
* (C) This upgrade method is used when you want to update the entire MavBake stack. If you have the time, this is the recommended method as it makes sure you get the latest version of all components.
* (D) This upgrade method is used when you want to update the mavbake binary only. Sometimes we release new versions of mavbake that have fixes and new features to make your baker setup and operation easier. This upgrade method doesn't take your baker down as the mavbake binary is not used during the baking process.

## (A) Update ami & eli and Octez binaries 
(updates components: #1, #2, #4)

   ```
   mavbake upgrade -a
   ```

## (B) Update Octez binaries only 
(updates components: #4)

   ```
   mavbake upgrade
   ```

## (C) Update the entire MavBake stack 
(updates components: #1, #2, #3, #4)

First update your mavbake binary to the latest version, depending on your computer architecture:

   ```
   wget -q https://github.com/tez-capital/mavbake/raw/main/install.sh -O /tmp/install.sh && sudo sh /tmp/install.sh
   # you may be prompted for sudo password
   ```

Then update the rest of the MavBake software stack:

   ```
   mavbake upgrade -a
   ```

## (D) Update mavbake only 
(updates components: #3)

Update your mavbake binary to the latest version, depending on your computer architecture:

   ```
   wget -q https://github.com/tez-capital/mavbake/raw/main/install.sh -O /tmp/install.sh && sudo sh /tmp/install.sh
   # you may be prompted for sudo password
   ```

## What should I do after updating?
After all updates and changes to your Tezos node, always ensure your baking process continues successfully by monitoring its performance on https://TzStats.com and https://TzKT.io.

Check your MavBake stack versions to ensure they are up to date:

   ```
   mavbake version --all
   ```

You should see the expected Octez version along with the release date of the binaries.

![<mavbake version, Octez versions>](/mavbake/tutorial/mavbakeVersionAll.png)


---

Any questions/comments/concerns? Please contact the Tez Capital team on
[Discord](https://discord.gg/cVGMA4MaNM) or [Telegram](https://t.me/tezcapital) 