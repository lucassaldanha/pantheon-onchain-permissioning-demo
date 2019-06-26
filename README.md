# Pantheon Onchain Permissioning Management Dapp

TODO: description of the repo and environment

## Requirements
1. A browser with Metamask installed (Chrome recommended)
1. Pantheon installed (TODO: link to instructions)
1. Permissioning Smart Contracts project checked out and ready to be used (link to instructions)

## Starting up the first node
1. Run the script `node0` to start the first node
1. Wait until the node is up and running

## Configuring Metamask
1. Open Chrome and click on the Metamask button
1. Select the network `Localhost 8545`
1. Click on Metamask account selector and choose **Import account**
1. Copy the private key for account `0xfe3b557e8fb62b89f4916b721be55ceb828dbd73` from the provided genesis file
	```
	8f2a55949038a9610f50fb23b5883af3b4ecb3c3bb792cbcefbd1542c692be63
	```
1. Paste the private key in the designated field on Metamask and click **Import**
1. This account will be your first admin account. It is recommended that you name it `Network Admin` (or anything easy to remember)

## Deploying all permissioning smart contracts
1. Navigate to the Permissioning Smart Contracts project directory
1. If this is the first time you are compiling and deploying the contracts, run `npm install`
1. Create a `.env` file with the following content:
    ```
    PANTHEON_NODE_PERM_ACCOUNT="0xfe3b557e8fb62b89f4916b721be55ceb828dbd73"
    PANTHEON_NODE_PERM_KEY="8f2a55949038a9610f50fb23b5883af3b4ecb3c3bb792cbcefbd1542c692be63"
    PANTHEON_NODE_PERM_ENDPOINT="http://127.0.0.1:8545"
    NODE_INGRESS_CONTRACT_ADDRESS="0x0000000000000000000000000000000000009999"
    ACCOUNT_INGRESS_CONTRACT_ADDRESS="0x0000000000000000000000000000000000008888"
    ```
1. Run `truffle migrate --reset`
1. Wait until truffle finishes deploying all the permissioning contracts

## Starting the Pantheon Permissioning Management Dapp
1. If this is the first time you are running the dapp, run `npm install`
1. Run `npm start`
1. Navigate to `http://localhost:3000/`
1. Double check that your Metamask is connected to your local node (`http://localhost:8545`)
1. You should be able to see the Whitelisted Accounts tab with one account whitelisted (your account `0xfe3b557e8fb62b89f4916b721be55ceb828dbd73`)

## Creating nodes permissioning rules for other nodes
1. Navigate to the **Whitelisted Nodes** tab
1. To create a new node permissioning rule, click on the **Add Whitelisted Node** button
1. Create a new permissioning rule for each one of the nodes. Use the following enodeURLs:
	```
	enode://62f4dcdc43e29e9f9ed9cf2e3899c96fc180679279b3811b81ed38c403295832265d0563c8a0555348bbe9bc978151cb834ff99fed3550ca7de18a0b71ba6454@127.0.0.1:30303
	```
	```
	enode://c783fc2f119bf2c79708b2e5f850bd53ac8d468ff6dfd32b7fcf95a8d7c1f514182030482f800ca9834f59c73a25e8659bf87bdfb8ae3cca6ed29ef1f3c81d91@127.0.0.1:30301
	```
	```
	enode://bc628f93bbd110e69ed48a971c22bfb9e136627de46f446bf78c7eaca2a6493e3fa6c10b774575317f0b39333a083bf662c41d02228483c71978c3e7025fe678@127.0.0.1:30302
	```

## Starting the other two nodes
1. In a new terminal window, navigate to our demo repository and run the script `node1`
1. In a new terminal window, navigate to our demo repository and run the script `node2`
1. Both nodes should be able to join the network