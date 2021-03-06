# Udacity Blockchain Capstone - Real Estate NFT Tokens
In this project I minted my own tokens to represent title to the properties I own. Before I mint a token, I provide proof that I own the property. I used zk-SNARKs to create a verification system which can prove I have title to the property without revealing specific information on the property.

Once the token has been verified I placed it on a blockchain market place (OpenSea) for others to purchase.

Once the token has been verified I minted 10 NFT tokens and deployed it on Rinkeby Network. Then I uploaded 5 of these tokens to blockchain market place (OpenSea - Rinkeby) for others to purchase https://rinkeby.opensea.io/. Then I proceeded to sell the tokens. To show that this works I bought these NFT tokens using a different account on OpenSea. 

## Install
This repository contains Smart Contract code in Solidity (using Truffle), tests (also using Truffle) and zk-Snarks generated proofs and verifier contract.

To install, download or clone the repo, then:

npm install

Start Ganache by using

ganache-cli

In a separate terminal window,from inside the directory eth-contracts/ Compile smart contracts:

truffle compile

This will create the smart contract artifacts in folder build\contracts.

Then compile and deploy with truffle.
To deploy to local ganache blockchain use

truffle migrate

To deploy to Rinkeby testnet use

truffle migrate --reset --network rinkeby

## Testing
To run truffle tests from inside the directory eth-contracts/:

truffle test ./test/TestERC721Mintable.js
truffle test ./test/TestSquareVerifier.js
truffle test ./test/TestSolnSquareVerifier.js

## Deployment
1. Create an account in Infura
2. Create a project in Infura and get the Address for deploying in Rinkeby test network
3. Copy the endpoint address and update the Rinkeby network information with the mnemonic and endpoint address in Truffle.js file
4. Fund the metamask wallet by posting a tweet in https://faucet.rinkeby.io. The post should have the address “ Requesting faucet funds into ……. On the Rinkeby Ethereum test network” Then copy the tweet in the above website and click Give me Ether.
5. Then deploy it using: truffle migrate --reset --network rinkeby. 

## Create ZK-Snarks Proof using Zokrates
1. Install Docker Community Edition here (https://docs.docker.com/install/). Virtualization should be enabled for Docker to work.

2. Run Zokrates docker container : docker run -v :/home/zokrates/code -ti zokrates/zokrates:0.3.0 /bin/bash

3. Change directory cd code/zokrates/code/square/

4. Compile the program written in ZoKrates DSL /path/to/zokrates compile -i square.code

5. Generate the Trusted Setup Now take the 'flattened' code, which is a circuit and go through a 'trusted setup' Repeat this process, every-time the program.code changes Two keys are generated - 'proving.key' and 'verification.key'

/path/to/zokrates setup

6. Compute Witness Having gone through the 'trusted setup' let's compute our 'witness' who knows the answer and it generates a witness file with computation steps

/path/to/zokrates compute-witness -a 3 9

7. Generate Proof Next step is to 'generate our proof' based on the above 'witness'. A proof.json file is generated in this step
/path/to/zokrates generate-proof

8. Export Verifier Last but never the least, let's generate our 'verifier' smart contract
path/to/zokrates export-verifier

9. Copy the verifier.sol file to the /eth-contracts/contracts/ folder.

## deployment on rinkeby rest net:
Starting migrations...
======================
> Network name:    'rinkeby'
> Network id:      4
> Block gas limit: 0x989680


1_initial_migration.js
======================

   Replacing 'Migrations'
   ----------------------
   > transaction hash:    0x490035483556fad0bf4cf2001a97e24df2f7217e907789a2d7ad4dc897134953
   > Blocks: 0            Seconds: 5
   > contract address:    0xC2a3EF9cA4B0A53D69625f158c2653bFf6B9937b
   > block number:        6665740
   > block timestamp:     1592141574
   > account:             0x35066cfEc33DD0A4F7eda10532B24eE6B04439d7
   > balance:             0.22042276
   > gas used:            244636
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.00244636 ETH

   Pausing for 2 confirmations...
   ------------------------------
   > confirmation number: 1 (block: 6665741)
   > confirmation number: 2 (block: 6665742)

   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.00244636 ETH


2_deploy_contracts.js
=====================

   Replacing 'SquareVerifier'
   --------------------------
   > transaction hash:    0x9a004f76a654526346331052ffa72517918720755e40dbdb108379e71e4967c5
   > Blocks: 0            Seconds: 9
   > contract address:    0xF4D0CDD6F147803D43a845d08b670b6c4f989B2f
   > block number:        6665744
   > block timestamp:     1592141634
   > account:             0x35066cfEc33DD0A4F7eda10532B24eE6B04439d7
   > balance:             0.20955147
   > gas used:            1044755
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.01044755 ETH

   Pausing for 2 confirmations...
   ------------------------------
   > confirmation number: 1 (block: 6665745)
   > confirmation number: 2 (block: 6665746)

   Replacing 'SolnSquareVerifier'
   ------------------------------
   > transaction hash:    0x5d585e2bf057afd1087e0c34d3e55bb93bb9b1b05361667210ae2f330631a497
   > Blocks: 1            Seconds: 9
   > contract address:    0x6616273feA61a0A8a634Ae431Ec3B265C9526e46
   > block number:        6665747
   > block timestamp:     1592141679
   > account:             0x35066cfEc33DD0A4F7eda10532B24eE6B04439d7
   > balance:             0.17094927
   > gas used:            3860220
   > gas price:           10 gwei
   > value sent:          0 ETH
   > total cost:          0.0386022 ETH

   Pausing for 2 confirmations...
   ------------------------------
   > confirmation number: 1 (block: 6665748)
   > confirmation number: 2 (block: 6665749)

   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.04904975 ETH


Summary
=======
> Total deployments:   3
> Final cost:          0.05149611 ETH

## Minting Tokens

https://rinkeby.etherscan.io/tx/0xaa4b2d0c0f4fdbc3cbcf4ed3a73a1fc68f77b894a3c7fc78b7f510d37b3c9fd8
https://rinkeby.etherscan.io/tx/0xd20ff9065cde11f56aa977cbe5007ebf2e7a4734727915957b4027a12d2239f9
https://rinkeby.etherscan.io/tx/0x68c5016db97361cc189a9377502a634e2ce678bdda30921dabe3964112d27218
https://rinkeby.etherscan.io/tx/0x414c818a47322aabc3a2f91a523b30237c6fc7bc02b09ee2d888afa0a412197e
https://rinkeby.etherscan.io/tx/0xf14390568b902d212007dc9a248a164410eb6b7f8e137d092fc1315c78f19094
https://rinkeby.etherscan.io/tx/0x06b999c346392dbaee799323dc87726f67e7105b307ec58b8a0bfec3e3f13948
https://rinkeby.etherscan.io/tx/0xdcc49f71f0f3c7b13bee7faf00b59c2d64e7658389986d1f62edb87703c9611f


## OpenSea Marketplace 
1. On rinkeby OpenSea market plate create storefront and import token using the "add an existing contract" button using the rinkeby deployed contract address. https://rinkeby.opensea.io/

2. Properties for which tokens are minted can be viewed using e.g to view the property with token 5 
https://rinkeby.opensea.io/account

## Project Contract Addresse and Links

  https://rinkeby.etherscan.io/address/0x6616273feA61a0A8a634Ae431Ec3B265C9526e46

# Project Resources

* [Remix - Solidity IDE](https://remix.ethereum.org/)
* [Visual Studio Code](https://code.visualstudio.com/)
* [Truffle Framework](https://truffleframework.com/)
* [Ganache - One Click Blockchain](https://truffleframework.com/ganache)
* [Open Zeppelin ](https://openzeppelin.org/)
* [Interactive zero knowledge 3-colorability demonstration](http://web.mit.edu/~ezyang/Public/graph/svg.html)
* [Docker](https://docs.docker.com/install/)
* [ZoKrates](https://github.com/Zokrates/ZoKrates)
# capston

