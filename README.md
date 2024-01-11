# Simple Storage dApp -- from Creation to Deployment
In this tutorial, we will create, test, and deploy a smart contract called SimpleStorage. This contract will allow your users to create their own sentence and store it on the blockchain. It will also allow users to retrieve the last sentence stored and display it on the page.

## Backend
1. Open the terminal (command line), create two new folders called `simple-storage` and `backend`. Go into the `backend` folder.
```
mkdir simple-storage
cd simple-storage
mkdir backend
cd backend
```

2. Set up a Hardhat project. Install the necessary libraries, by typing in the terminal:
```
npm init --yes
npm install --save-dev --save-exact hardhat@2.14.0
npm install dotenv
```

3. This library might be necessary to install as well, especially if you're a Windows user:
```
npm install --save-dev @nomicfoundation/hardhat-toolbox@2
```

4. Make sure you are still in the `backend` directory. Now, create a sample contract project by typing in the terminal:
```
npx hardhat
```
- Select `Create a Javascript Project`. Don't change anything in the Hardhat project root, just click enter. Yes, add a `.gitignore`. 

5. Open the `backend` folder and remove any present contracts inside the `contracts` folder. Insert your `SimpleStorage` contract.

6. Now, inside the `scripts` folder, replace the contect of the `deploy.js` file with the [deploy.js code from this project](https://github.com/charmingdata/dApp-simple-storage/blob/main/backend/scripts/deploy.js).

7. Create a `.env` file inside the `backend` folder. This will be used to store your wallet key and your Quicknode endpoint. A QuickNode API endpoint gives you quick access to a network of nodes.

- Add these two lines inside the `.env` file, and update the content inside the quotation marks:
```
QUICKNODE_HTTP_URL="your-quicknode-http-provider-goes-here-inside-the-quotation-marks"
PRIVATE_KEY="your-wallet-private-key-goes-here-inside-the-quotation-marks"
```

- [video on setting up your digital wallet](https://youtu.be/kHF70SWFTYU)
- [video on setting up your Quicknode](https://youtu.be/xxkT2qpg4g8)

8. Open the `hardhat.config.js` file inside the `backend` folder and replace its content with the [hardhat.config.js code from this project](https://github.com/charmingdata/dApp-simple-storage/blob/main/backend/hardhat.config.js). 

9. Compile your Contract by going back to your terminal (ensure you are in the `backend` directory). And type:
```
npx hardhat compile
```
- Every time you modify your contract (`SimpleStorage`), you will have to repeat the above compile step.

10. With your contract compiled, now we can deploy it to the sepolia testnet. In your terminal type:
```
npx hardhat run scripts/deploy.js --network sepolia
```

Save the contract address that was printed out.
Go to https://sepolia.etherscan.io/ and insert the contract address into the Explorer input field. Take some time to explore the transaction details of your contract.
- Save this address somewhere. Don't lose it!

## Testing
Every Contract should be tested before deployment. In this case we deployed first becuause it's freaking exciting to see our contract deployed. But we need tests to make sure our contract has no bugs and is secure. 

1. Open the `test` folder and remove any present files inside of it. Create a new file called `testing.js`, and insert the [testing.js code from this project](https://github.com/charmingdata/dApp-simple-storage/blob/main/backend/test/testing.js).

2. Go back to the terminal, make sure you're in the `backend` directory, and type: 
```
npx hardhat test
```

## Frontend
In this section of the tutorial we'll create a dApp (decentralized app) that will connect to your contract and its functions, allowing you to  interact with it. In other words, we're building an interface for the contract. 

1. Open the terminal (command line) and go into the `simple-storage` directory. Create a sample Next app by typing:
```
npx create-next-app@13 frontend
```
- Make sure to choose these settings.

![image](https://github.com/charmingdata/dApp-simple-storage/assets/94773218/28765958-6c47-4eed-a6ad-e1093435cf30)

2. Before running the sample app, you'll need to remove the `.git` file that was automatically created inside the new `frontend` folder. 
To remove the file, open a Windows PowerShell and type this command:
```
# Linux / macOS
cd frontend
rm -rf .git

# Windows
cd frontend
rm -r -fo .git
```

3. Install these packages using your terminal (you should still be in the `frontend` directory).
```
npm install web3modal
npm install ethers@5
```

4. Create a new folder called `constants` within the `frontend` directory. Inside the `constants` folder create a new file called `index.js`. Add the following code inside `index.js`. 
```
export const MY_CONTRACT_ADDRESS = "MY_CONTRACT_ADDRESS";
export const abi = MY_ABI;
```
- Replace the `MY_ABI` with the abi array that can be found in the following file:
`backend/artifacts/contracts/SimpleStorage.sol/SimpleStorage.json`

- Replace the `MY_CONTRACT_ADDRESS` with the address of the contract that you deployed in the Backend section of this tutorial. 

5. Finally, to build the interface of the contract, open the `index.js` file under the `pages` folder (in the `frontend` folder) and replace its content with the [index.js code from this project](https://github.com/charmingdata/dApp-simple-storage/blob/main/frontend/pages/index.js).

6. Add the Charming Data images using the instructions below. Once you understand how to add images to your app, feel free to replace with your own images, in which case you would need to update the path to the images names inside the `pages/index.js` file (lines 143 & 154).
  - Add the [logo-charmingdata-small.ico](https://raw.githubusercontent.com/charmingdata/dApp-simple-storage/main/frontend/public/logo-charmingdata-small.ico) and [logocharmingdata.png](https://github.com/charmingdata/dApp-simple-storage/blob/main/frontend/public/logocharmingdata.png) to the public folder inside the frontend directory. Do not change image names.

7. Go back to your terminal; make sure your in the `frontend` directory and type:
```
npm run dev
```

## Sharing your dApp with others
We will use Vercel to deploy the frontend of our contract. Before starting with Vercel you will need to create a GitHub account if you don't have one and [push your code into a GitHub repository](https://youtu.be/vpRkAoCqX3o).

1. Once your repositoy has been created in Github, go to [Vercel](https://vercel.com/login) and create an account by connecting your GitHub account. 

2. Once your GitHub account is connected, click the button to add a new project in Vercel. 
  - add your repository (you might have to import it as well)

3. Select `Next.js` as the Framework Preset. In the Root Directory click Edit to select `frontend`.

4. Click Deploy, and wait a few minutes. When done, click your domain link to see your dApp.

"# commit" 
"# commit" 
