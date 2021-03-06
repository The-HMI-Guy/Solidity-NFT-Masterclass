# This Project Will Upload an NFT Collection Onto Ethereum's Test Network Rinkeby

---

## Table of contents

- [General info](#general-info)
- [Features](#features)
- [Technologies](#technologies)
- [Setup](#setup)
- [To Do List](#to-do-list)

## General info

This project was built from Hashlip's Youtube video/repo.

## Features

- Generating an NFT collection (artwork must be created already)
- Upload the artwork to IPFS or Pinata
- Create smart contract/dapp UI
- Whitelist, pre-sale, and public sales available
  - Can hide metadata/image

## Setup

- Create Masterclass folder
- Grab layers folder from another repo or upload your own NFT collection
- Download or clone Hashlip's art engine from GitHub
- Run

```
npm install
```

- Run

```
npm run generate
```

- This will generate the images and create the build folder structure
- ![Generate-Image](https://user-images.githubusercontent.com/96752508/169027006-03b94691-320a-4fe0-9c8f-a495218b2c2a.png)
- Install IPFS Desktop
  - https://github.com/ipfs/ipfs-desktop/releases
  - Open the application and go to **Files**
    - Click **Import** and select the images folder
    - Purpose of this to get the CID
    - Click ... and **Inspect**
      - Inspect the number of links matches the number of images
    - Click ... and click **Copy CID**
    - Head to pinata.cloud
- Go to https://www.pinata.cloud/ and create an account
  - Click **+ Upload** and **CID**
  - Paste the CID from IPFS and give it a unique name
  - https://gateway.pinata.cloud/ipfs/QmZD66sq4Em1xQKSchg45q2AtTf8qts5LZMPx3kCqPYpQg/hidden.png
  - ![Hidden-Image](https://user-images.githubusercontent.com/96752508/169026800-63c9b8cb-ca07-439e-94fb-ee79c64f518b.png)
  - Once uploaded, copy the CID and go back to the config.js and modify the baseURL
  - Run
  ```
  npm run update_info
  ```
  - This will updated the json files for the new image URL and description
- Delete \_metadata.json
  - Might break things if we execute using the dapp
- Upload metadate using the steps above for the image folder
- Copy the **CIP**
- https://gateway.pinata.cloud/ipfs/QmcmJ1g8kNsiRRKUznLkjcigFk4sw7YZMy8dQ7W9axNNGN/hidden.json
- ![Hidden-Metadata](https://user-images.githubusercontent.com/96752508/169026400-bf33d190-bcaa-4a9b-9b49-dd50ba77d2b7.png)
- ANY CHANGES TO THE IMAGES OR METADATA WILL CHANGE THE CID
- Create folder called **hidden** with two subfolders called **hidden_image** and *h*idden_metadata\*\*
- Create a hidden.image and hidden.json file in their respective folders
- Follow upload steps above for the hidden_IMAGE folder
- Copy the CIP of the hidden_IMAGE and paste it in the hidden.json file
- Follow upload steps above for the hidden_METADATA folder
- Create an account at Etherscan.io
- Click the Profile dropdown and select **API**
- Now at the API screen, click **+ Add**
- Download Hashlip's nft-erc721-collection repo
- https://github.com/hashlips-lab/nft-erc721-collection
- Open project with an IDE
- Run

```
npm i -g truffle
```

- Run

```
truffle dashboard
```

- If truffle dashboard is closed out (termninal closed), you will need to reestablish connection
- This command will bring up the truffle dashboard in your browser
- Once here, connect your Metamask (make sure Metamask is on the proper network before)
- Dashboard will show **Incoming Request** from our program
- Once detected, truffle will display it.
- Run

```
npm i -g corepack
```

- Install Smart Contract Dependencies
- Run

```
cd smart-contract
```

- Run

```
yarn
```

- Copy/paste the file **.env.example** and rename duplicate to **.env**
- Delete content inside the **.env** file besides (no longer need to paste private keys)
  - Collection_URI_Prefix
    - Insert CID from Pinata.cloud for the DragonEye_METADATA
  - Gas_Reporter_Coin_Market_Cap_API_Key
  - Block_Explorer_API_Key
    - Insert API from Etherscan
- Option inside the contract to pay hashlip lab's 5% (optional)
- If you remove, keep the **withdraw() public onlyOwner** function
- Run

```
yarn rename-contract NEW_CONTRACT_NAME
```

- This will update the contract inside the program (files and references)
- Update
  - tokenName:
  - tokenSymbol:
- Update
  - hiddenMetadataUri:
    - Use the hidden_METADATA
- Update
  - maxSupply:
    - Number should reflect the number of images built inside the art_engine
- Update the whitelistSale, preSale, and publicSale price/maxMintAmountPerTx for the NFT project
- Run

```
yarn deploy --network truffle
```

- Check truffle dashboard to see the incoming transactions
  - If you run into yarn issues (warning ../../../package.json: No license field) locate the package.json at this root level and update or remove
  - Also, if the transaction is not approved in a timely manner, an error will be thrown (HeadersTimeoutError: Headers Timeout Error)
- Once you have a deployed contract (from process > confirm), update
  - contractAddress: "WITH THE CONTRACT ADDRESS FROM THE TERMINAL"
- Head to Etherscan and go to the Rinkeby network and paste the contract address
- To see all the cli commands, go to the package.json file
- To verify the contract, run

```
yarn verify CONTRACT_ADDRESS --network truffle
```

- Check terminal for confirmation, once confirmed, check Etherscan to see the contract verified
- Open a new terminal window and cd into the dapp folder
- Once in the dapp folder, run

```
yarn
```

- Run

```
yarn dev-server
```

- If you run into a "Error: listen EADDRINUSE: address already in use XXX.X.X.X" error
- Run

```
netstat -avtn | egrep 'Proto|8080'
```

- After running, grab the PID that is running and run

```
kill PID#
```

- Rerun and verify the address has been killed

```
netstat -avtn | egrep 'Proto|8080'
```

- Grab server address and paste into the browser (contract will be paused)
- Grab MetaMask address for whitelist and paste it in the whitelist.json
- cd into the smart contract folder and run

```
yarn whitelist-open --network truffle
```

- If you run into Error: could not detect network (event="noNetwork", code=NETWORK_ERROR, version=providers/5.6.2)
- Refresh the truffle dashboard and reconnect wallet
- Once reconnected, run the above command
- ![Whitelist-Active](https://user-images.githubusercontent.com/96752508/169289659-7bdc8fca-20f6-4892-9b11-6c7ce6fa72c8.png)
- After clicking **Mint** and confirming, go to https://testnets.opensea.io/assets/rinkeby/0x0755c2795e4da86d34eef8d87233a36c894b4830/1
- Locate the NFT project or use your MetaMask to verify the NFT.
- Now run

```
yarn whitelist-close --network truffle
```

- Now run

```
yarn presale-open --network truffle
```

- And so on
- To reveal the artwork, run

```
yarn reveal --network truffle
```

- Refresh metadata on Opensea
- In the terminal running the dev-server, run

```
control + C
```

- Run (make sure you're in the minting-dapp folder)

```
yarn build
```

- At this point, drop the public folder inside the root folder of the web server

## Technologies

Project is created with:

- Node Version: 14.17.3
- Rest of the dependencies can be found above

## To Do List

- N/A - Project completed
