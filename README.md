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
- This will generate 5 images and create the build folder structure
- INSERT IMAGE
- Install IPFS Desktop
  - https://github.com/ipfs/ipfs-desktop/releases
  - Open the application and go to *Files*
    - Click *Import* and select the images folder
    - Purpose of this to get the CID
    - Click ... and *Inspect*
      - Inspect the number of links matches the number of images
    - Click ... and click *Copy CID*
    - Head to pinata.cloud
- Go to https://www.pinata.cloud/ and create an account
  - Click *+ Upload* and *CID*
  - Paste the CID from IPFS and give it a unique name
  - INSERT EXAMPLE OF IMAGE FROM IFPS
  - Once uploaded, copy the CID and go back to the config.js and modify the baseURL
  - Run
  ```
  npm run update_info
  ```
    - This will updated the json files for the new image URL and description
- Delete _metadata.json
    - Might break things if we execute using the dapp
- Upload metadate using the steps above for the image folder
- Copy the *CIP*
- INSERT EXAMPLE OF METADATA FROM IFPS
- ANY CHANGES TO THE IMAGES OR METADATA WILL CHANGE THE CID
- Create folder called *hidden* with two subfolders called *hidden_image* and *hidden_metadata*
- Create a hidden.image and hidden.json file in their respective folders
- Follow upload steps above for the hidden_IMAGE folder
- Copy the CIP of the hidden_IMAGE and paste it in the hidden.json file
- Follow upload steps above for the hidden_METADATA folder


## Technologies

Project is created with:

- Node Version: 14.17.3

## To Do List

- Coming soon!
