# This Project Will Upload an NFT Collection Onto Ethereum

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

- Coming soon!

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

## Technologies

Project is created with:

- Node Version: 14.17.3

## To Do List

- Coming soon!
