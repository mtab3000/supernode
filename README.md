BOP Community Bitcoin Server
============================

This software enables your application to send/receive Bitcoin payments or to data mine the network's transaction history, with ease.

You may run it stand-alone utilizing its own validation engine or as a slave behind the Satoshi client so it accepts exactly what the 'reference client' does. In either case it builds a fully indexed block chain of transactions stored in LevelDB.

The server process handles peer-to-peer communication with the network and serves clients connected to it through a message bus. Wallet(s) are implemented by the client library and transactions are also signed at the client side, therefore it is safe to operate the Server in a remote environment as it does not store or receive private keys.

Bits of Proof offers professionally hosted server instances for commercial use, that share and build on this code base:

* BOP Enterprise Bitcoin Server -  for very high volume multiple and hierarchical wallet support. Don't despair with the 'reference client's geeky RPC calls design and poor performance. Use our intuitive, business friendly, high performance API and spend rather to develop your own business case.

* BopShop - Payment processor to accept Bitcoin on a website or in Person. Available both hosted by BOP or with white label to start your own Bitcoin payment processor business.

* BeBop - Simple but powerful mobile wallet best integrated with BopShop.

_Use our ready to go hosted BOP Server instance! Get an evaluation access, attractive pricing based on resources used or transactions processed from sales@bitsofproof.com_

Build the Community Server
--------------------------
Make sure you have Maven3, JDK 7 (with JCE Unlimited Strength Policy Jurisdiction) and Google protobuf compiler 2.4.1 installed.

   git clone https://github.com/bitsofproof/supernode

   cd supernode
   
   mvn package

Run
---

java -server -Xmx2g -jar target/server/target/bitsofproof-server-1.2.0.jar testnet3 memdb

The final two parameters of the above example command line identify configuration contexts stored under server/src/main/resources/context. You have to choose one of the networks by specifying either testnet3 or production or slave, and a database layer, that could be (examples):
   
   * memdb - in memory database for tests
   * leveldb - LevelDB

To use the API of your local server you need to run a message broker process providing the infrastructure. Since the message bus offers authentication and a wide selection of transports, your installation will likely be unique and need to be reflected in server/src/main/resources/context/BCSAPI-profile.xml. You find example configurations for the message broker Apollo and Active MQ there. The complete command line for a production environment might be:

java -server -Xmx2g -jar target/server/target/bitsofproof-server-1.2.0.jar production leveldb BCSAPI apollo


License
-------
Apache License, Version 2.0. See LICENSE file.

Donations
---------
In case you do not require professional services of Bits of Proof, but would like to honor its contribution to the Bitcoin community, please donate to:

1EuamejAs2Lcz1ZPNrEhLsFTLnEY29BYKU

Donations will finance social events of Bits of Proof developer.
