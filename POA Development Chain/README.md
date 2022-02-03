# Blockchain: Proof of Authority

## Objective
By the end of this project, we will be able to set up a Testnet called sifuzcoin using `Puppeth` to generate Gensis block and `Geth` tool.

## Steps and Procedure
* Using [Go Ethereum](https://geth.ethereum.org/downloads/), we will install `Blockchain-Tools` and create our genesis block and node set up 
* using [MyCrypto](https://mycrypto.com/), we will send test ether and verify the transaction in the block

## Execution
1. First, we need to go to the `Blockchain-Tools` folder and open git bash terminal. Creating accounts for two (or more) nodes for the network with a separate datadir for each using geth.
Using below code we will set up our first node.
`./geth --datadir node1 account new`
![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/1.node1_init.JPG)

Same procedure for second node
`./geth --datadir node2 account new`

2. At this stage, we will create our network and genesis block using the command `./puppeth` and follow the corresponding commands that comes with it. One can easily find what option to choose in the below screenshots. After following each step correctly, a `sifuzcoin.json` file will generate which will use later to initialize the node
![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/2.genesis_block_1.JPG)

![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/2.genesis_block_2.JPG)

![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/2.genesis_block_3.JPG)

3. Now we will initialize each node with new `sifuzcoin.json` using `geth`. 
Code as follows:
`./geth --datadir node1 init sifuzcoin.json`
`./geth --datadir node2 init sifuzcoin.json`

![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/3.init_node1_node2.JPG)

4. Now we will run the first node by unlocking the account, enable mining and RPC. Only node1 RPC needs to be enabled.
`./geth --datadir node1 --unlock "0x5e623234FaAF253dD43478D7F2520e3B9985a596" --mine --rpc --allow-insecure-unlock`

![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/4.run_node1.JPG)

After that we will run node2 for mining using different port and using first node's address as the bootnode flag
`./geth --datadir node2 --unlock "PublicaddressNODE2" --mine --port 30304 --bootnodes "ENODE" --ipcdisable --allow-insecure-unlock`

![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/5.run_node2.JPG)

5. Using the MyCrypto GUI wallet to connect to the node with the exposed RPC port.We used a custom network, and include the chain ID, and use ETH as the currency. In MyCrypto Using KeyStore to open wallet. Check node1 folder for KeyStore. You will need to use a custom network, and include the chain ID, and use ETH as the currency. 

![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/6.connect_myrypto_node1.JPG)

As mining going on in both node, we should be able to some Ether in balance
![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/7.balance_check.png)

Now we will try to send some ether to another wallet to verify if our blockchain is working
![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/8.trx_1.png)

Finally we can see that our transaction has been sent successfully proving our POA network works
![alt=""](https://github.com/Ashfaque-Rahman/blockchain-homework/blob/main/POA%20Development%20Chain/Screenshots/9.success.png)