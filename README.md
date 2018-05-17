GameChain Web Demo
===================

GameChain Web Demo is a simple web interface for [GameChain](http://tedchain.network) blockchains, written in PHP.

	Copyright (c) 2010-2018 The Bitcoin developers
	Original code was distributed under the MIT software license.
	Copyright (c) 2014-2018 TEDLab Sciences Ltd
	GameChain code distributed under the GPLv3 license, see COPYING file.

Welcome to GameChain Web Demo
==============================

This software uses PHP to provide a web front-end for a [GameChain](http://tedchain.network) blockchain node.

It currently supports the following features:

* Viewing the node's overall status.
* Creating addresses and giving them real names (names are visible to all nodes).
* Changing permissions for addresses.
* Issuing assets, including custom fields and uploading a file.
* Updating assets, including issuing more units and updating custom fields and file.
* Viewing issued assets, including the full history of fields and files.
* Sending assets from one address to another.
* Creating, decoding and accepting offers for exchanges of assets.
* Creating streams.
* Publishing items to streams, either as text or an uploaded file.
* Viewing stream items, including listing by key or publisher and downloading files.

The web demo does not yet support the following important functionality in the GameChain API:

* Multisignature addresses and transactions.
* Adding metadata (or stream items) to permissions or asset transactions.
* Viewing an addresses' transactions.
* Subscribing to assets and viewing their transactions.
* Viewing a list of keys or publishers in a stream.
* Peer-to-peer node management.
* Message signing and verification.

The GameChain Web Demo is still under development, if any of these things are crucial for your needs.


System Requirements
-------------------

* A computer running web server software such as Apache.
* PHP 5.x or later with the `curl` extension.
* GameChain 1.0 alpha 26 or later.

**Note that this Web Demo does not yet support GameChain 2.0 preview releases.**


Create and launch a GameChain Blockchain
-----------------------------------------

If you do not yet have a chain to work with, [Download GameChain](https://github.com/tedchain/gamechain) to install GameChain and create a chain named `chain1` as follows:

    gamechain-util create chain1
    gamechaind chain1 -daemon
    
If your web server is running on the same computer as `gamechaind`, you can skip the rest of this section. Otherwise:

    gamechain-cli chain1 stop

Then add this to `~/.gamechain/chain1/gamechain.conf`:

    rpcallowip=[IP address of your web server]
  
Then start GameChain again:
  
    gamechaind chain1 -daemon



Configure the Web Demo
----------------------

_This section assumes your blockchain is named `chain1` and you are running the node and web server on a Unix variant such as Linux. If not, please substitute accordingly._

Make your life easy for the next step by running these on the node's server:

    cat ~/.gamechain/chain1/gamechain.conf
    grep rpc-port ~/.gamechain/chain1/params.dat
    
In the web demo directory, copy the `config-example.txt` file to `config.txt`:

	cp config-example.txt config.txt
  
In the demo website directory, enter chain details in `config.txt` e.g.:

    default.name=Default                # name to display in the web interface
    default.rpchost=127.0.0.1           # IP address of GameChain node
    default.rpcport=12345               # usually default-rpc-port from params.dat
    default.rpcuser=gamechainrpc       # username for RPC from gamechain.conf
    default.rpcpassword=mnBh8aHp4mun... # password for RPC from gamechain.conf

Multiple chains are supported by the web demo by copying the same section again but with different prefixes before the period, for example:

	another.name=...
	another.rpchost=...
	...

**Note that the `config.txt` file is readable by users of your web demo installation, and contains your GameChain API password, so you should never use this basic setup for a production system.**


Launch the Web Demo
-------------------

No additional configuration or setup is required. Based on where you installed the web demo, open the appropriate address in your web browser, and you are ready to go!
