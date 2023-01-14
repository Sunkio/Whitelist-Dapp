# Whitelist dApp

A whitelist dApp that gives early supporters access to a whitelist for a new NFT collection. The first 10 requesters get access for free.

You can check out the deployed testnet app here: https://whitelist-dapp-dsmd7zfa7-sunkio.vercel.app/

![Whitelist dApp Screenshot](wl-frontend/public/Whitelist-Dapp-Screenshot.png)

## Details
This whitelist dApp is a simple, decentralized application that allows users to create and manage a whitelist of approved Ethereum addresses. The whitelist can be configured to allow or deny access to certain functions or contracts based on whether an address is included in the whitelist. The application can also be modified to store and share sensitive data among a trusted group of addresses.

## How to interact with the deployed testnet app
The contract has been deployed to Ethereum Sepolia for testing purposes. You can find out more about it [here](https://sepolia.dev/).
You need test funds to interact with the app. There are several faucets you can use to get Sepolia testnet Ether for free. Here’s one example that has worked well for me in the past:
https://sepolia-faucet.pk910.de/

If you’re brand new to web3: To get  started, you first need a wallet such as [Metamask](https://metamask.io/) to receive testnet funds and start interacting with the app.

## Installing / Getting started with the project

To install the Whitelist-Dapp, you will need to install the necessary dependencies for both the “backend” (= the blockchain part) and the frontend. Once all of the dependencies are installed and you're done editing, you can deploy the whitelist smart contract to the Ethereum (test) network and deploy the frontend to a hosting service of your choice, e.g. [Vercel](https://vercel.com/).


### 1.) Fork and clone this repository to your local machine
[Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repo, then clone it to your local machine:
``` shell
git clone https://github.com/YOUR-USERNAME/Whitelist-Dapp 
```

### 2.) Blockchain Part
Run the following commands in your CLI:
``shell
cd Whitelist-Dapp/hardhat-tutorial
npm init --yes
npm install --save-dev hardhat
npx hardhat
npm install dotenv
```

Create an endpoint on [QuickNode](https://www.quicknode.com/), or any other provider of your choice, and copy the HTTP-URL.
Create a .env file and follow the structure of the [.env-example file](hardhat-tutorial/.env-example) to add your QuickNode URL and your private key. DO NOT upload this file to Git Hub! It is already included in .gitignore but better double-check. 🙂

Once you’re done editing, run:
``
npx hardhat compile 
npx hardhat run scripts/deploy.js –network sepolia
```

### 3.) The Frontend Part
The frontend is built with Next.js. You need to have [Node.js]() installed.

Run the following commands to set-up your project and start the development server:
``` shell
cd wl-frontend
rm package-lock.json
npm install
npm run dev
```
You should now be able to open the frontend in your browser on `localhost:3000`.


**Possible errors & fixes**

This project is built with node ^18. If you get an error message, you might have to update Node.js. To check your Node version, run:
``` shell
node -v
```
If you find a yarn-lock.json file, this might cause problems with installing npm in your project. Remove it and install npm again, then start your development server:
``` shell
rm yarn-lock.json
npm install
npm run dev
```

Once you’re done with the above, run:
``` shell
npm install web3modal
npm install ethers
```
Open constants/index.js and change the value of the `WHITELIST_CONTRACT_ADDRESS` variable to the address of the contract you deployed via hardhat earlier.
Then change the value of the `abi` variable to your own ABI array. You can find it here: `hardhat-tutorial/artifacts/contracts/Whitelist.sol/Whitelist.json


## How to Contribute
Contributions are always welcome! Please check the [Code of Conduct](https://github.com/Sunkio/.github/CODE_OF_CONDUCT.md) .

## License
This project is licensed under the [MIT License](./License.md).

## Support
If you have any questions or need help getting started, please open an issue in the repository or contact me on Twitter: @tanja_codes
