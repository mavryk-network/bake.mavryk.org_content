---
title: "How to Setup with Peak GUI"
weight: 1
type: docs
summary: How to Setup Using MavPay with the TezPeak GUI
---

## Preparation

For this tutorial, you'll need to have already followed the following tutorials:
* [Generate payout soft wallet](/mavpay/tutorials/how-to-setup/#preparation-step-3---payout-wallet-optional)
* [Create MavPay configuration file](https://bake.mavryk.org/mavpay/tutorials/how-to-setup/#setup-step-1a-configuration-file-simple)
  + [Default configuration](https://bake.mavryk.org/mavpay/configuration/examples/default/)
  + [Starter/Minimal configuration](https://bake.mavryk.org/mavpay/configuration/examples/starter/)
  + [All configuration options](https://bake.mavryk.org/mavpay/configuration/examples/sample/)
* [Download MavBake](/mavbake/tutorials/how-to-bake/#download-and-copy-mavbake) _(note: Installing node/baking services not necessary for this tutorial)_
* [Install ami-mavpay service](https://github.com/mavryk-network/ami-mavpay)

Following the guides above will ensure you have the necessary tools and configurations to proceed with this tutorial.

---

## Installation

TezPeak GUI supports using MavBake and MavPay simultaneously or by themselves. To run them at the same time simply combine both configurations in the same file as shown here: [https://github.com/tez-capital/tezpeak](https://github.com/tez-capital/tezpeak)

> Scroll down to the bottom of the page for the full configuration example.

### Download and install TezPeak via MavBake

   ```
   mavbake setup --peak
   ```

> You don't need to install the MavBake node or baker services to use MavPay.

### Setup TezPeak configuration

   ```
   cd /mavpay/peak/ && touch config.hjson
   ```

Open the `config.hjson` file with your favorite text editor. 

##### Sample TezPeak configuration

Here's an example of a minimal TezPeak `config.hjson` file with just MavPay configured:

   ```
{
    listen: 0.0.0.0:8733
    app_root: /mavpay
    modules: {
        mavpay: {
            payout_wallet: mv1HPdQqiQXiTqe6BD52wbPe4mSsCwTqSFdS
        }
    }
}
   ```

##### Full TezPeak configuration examples

Here's the TezPeak configuration with all available MavPay options:

   ```
{
	# Id to show in the header
    id: ""
	# Address to listen on
    listen: 127.0.0.1:8733
    app_root: /mavpay
    modules: {
        mavpay: {
			# can be null to disable mavpay package monitoring
            applications: {
				# path to mavpay ami package, either absolute or relative to parent directory peak
                mavpay: mavpay
            }
            payout_wallet: mv1HPdQqiQXiTqe6BD52wbPe4mSsCwTqSFdS
            payout_wallet_preferences: {
                balance_warning_threshold: 100
                balance_error_threshold: 50
            }
			# forces all operations to be dry run
            force_dry_run: true
        }
    }
	
	# List of reference nodes to connect to
	# The reference nodes are used to get the rights and blocks if the baker's node is not available
    nodes: {
        "Mavryk Dynamics": {
            address: https://rpc.mavryk.network/
            is_rights_provider: true
            is_block_provider: false
        }
    }
	# The mode tezpeak should operate in
	# auto - if bound to localhost, it will operate in private mode if not, it will operate in public mode
	# public - assumes public environment, only readonly operations are allowed
	# private - assumes private environment, all operations are allowed
    mode: auto
}
   ```

## Start TezPeak and connect to it

   ```
   mavbake start --peak
   ```

If you're connecting to the TezPeak GUI from a different computer, you'll need to open a web browser and navigate to `http://<your-baker-ip>:8733`. 

If you're connecting from the same computer, you can use `http://127.0.0.1:8733` or `http://localhost:8733`.

## TezPeak example screenshot

![<TezPeak example screenshot>](/mavbake/tutorial/tezpeakexample.png) 

---

Any questions/comments/concerns? Please contact the Mavryk Dynamics team on
[Telegram](https://t.me/MavrykNetwork) 