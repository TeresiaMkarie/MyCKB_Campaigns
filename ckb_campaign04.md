# Create a Digital Object Using Spore Protocol

**NAME**: Teresia Mkarie<br>
**DATE**: 24th-August-2026<br>

## Tasks Completed
- **[Create a Digital Object Using Spore Protocol](https://docs.nervos.org/docs/dapp/create-dob#create-digital-object)**: Completed the practical tutorial for building a simple dApp that converts local image files into Spore output cells using the Spore SDK and CCC transaction builders.I also explored the Spore protocol architecture, focusing on how CKB enables fully on-chain digital objects (DOBs) compared to traditional off-chain ERC-721 NFTs. <br>
- **[Render the Content from the Digital Object](https://docs.nervos.org/docs/dapp/create-dob#render-content-from-digital-object)**:Having created the Digital object on-chain;I learnt that to render and show the image on the browser,one  needs to first find the spore cell of the digital object,extract the data from the *Spore Cell* and then decode its data content.<br>
- **Deploy to Testnet**:  I changed the **NETWORK** environment variable to **testnet** for the testnet deployment of the dApp.

## Issues During Building
To Interact with the **dApp** for the *Create-digital-object* i came accross this error![Image upload error](./DOB_Images/rejection_error.png).<br>This was after i tried uploading an image on-chain.

### How I managed to fix this Issue
Apparently the building of the dApp was successful running on *localhost://1234* but my Devnet was not running so it could not register the image uploaded.Fixed it by re-starting the Devnet with the **`offckb node`** command.

## Deployment of the on-chain Digital Object through Spore-SDK
After building and running the dApp,this was the results running locally on host:1234![dApp_running](./DOB_Images/Create_DOB.png)

## Key Findings.
The Create Digital Object accepted two parameters which were visible from the dApp running;**the private key  used to sign and create the digital object** and the **Content to be stored in the Digital object** <br>- **Before Image Upload**-The Create DOB button is inactive meaning no **on-chain asset** was encoded on the blockchain.<br>- **After Image Upload**- The file size will be indicated and the  fil-type.THis is in line with the content-type and content of the data fields of the **SporeCell.** From the **SporeCell** which has a data structure consisting of 3-main fields,the **data field**,**type field** and the **lock field**,The data field which contains the content-type and the content will allow the user to transform any content uploaded to digital object whichis fully stored on-chain.<br>![After Image Upload](./DOB_Images/afterImage_upload.png)
## Render the Image in the Browser
![Rendered_Image](./DOB_Images/DOB_Rendered_image.png)<br>With the **Spore Cell** of the digital object and after decoding its content the image gets to be rendered in the browser as shown.The **cccClient.getCellLive** will enable the getting of the **liveCell** of the digital object decoded to be rendered.If the cell is null, it returns the following alert message<br><br>![cell not found](./DOB_Images/cell_notFound.png)

## Deploying the app to Testnet
Switched to the testnet **NETWORK** and came across this error when i tried to create the Digital Object after i had uploaded an mage locally.![testnet error](./DOB_Images/testnet_error.png)<br>I realised this was caused by insufficient faucets and i had to fund my testnet address for a successful encoding of the image before being stored on-chain.


