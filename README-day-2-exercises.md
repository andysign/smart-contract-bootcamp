<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Day 2 Exercises](#day-2-exercises)
  - [Exercise 1: My First Hardhat Project](#exercise-1-my-first-hardhat-project)
    - [Exercise 1: My First Hardhat Project: Setting Up Hardhat](#exercise-1-my-first-hardhat-project-setting-up-hardhat)
    - [Exercise 1: My First Hardhat Project: Creating The Smart Contract](#exercise-1-my-first-hardhat-project-creating-the-smart-contract)
    - [Exercise 1: My First Hardhat Project: Deploying and Interacting With the Smart Contract](#exercise-1-my-first-hardhat-project-deploying-and-interacting-with-the-smart-contract)
    - [Exercise 1: My First Hardhat Project: Token Bonus Exercise](#exercise-1-my-first-hardhat-project-token-bonus-exercise)
  - [Exercise 2: Deploying to a Local Network](#exercise-2-deploying-to-a-local-network)
    - [Exercise 2: Deploying to a Local Network: Downloading the Hardhat Starter Kit](#exercise-2-deploying-to-a-local-network-downloading-the-hardhat-starter-kit)
    - [Exercise 2: Deploying to a Local Network: Setting up the Local Hardhat Network](#exercise-2-deploying-to-a-local-network-setting-up-the-local-hardhat-network)
    - [Exercise 2: Deploying to a Local Network: Deploying and Interacting With the Smart Contracts](#exercise-2-deploying-to-a-local-network-deploying-and-interacting-with-the-smart-contracts)
    - [Exercise 2: Deploying to a Local Network: Forking Ethereum Mainnet](#exercise-2-deploying-to-a-local-network-forking-ethereum-mainnet)
    - [Exercise 2: Deploying to a Local Network: Bonus Fork Exercise](#exercise-2-deploying-to-a-local-network-bonus-fork-exercise)
  - [Exercise 3: Hardhat Starter Kit Testnet](#exercise-3-hardhat-starter-kit-testnet)
    - [Exercise 3: Hardhat Starter Kit Testnet: Setting Up The Hardhat Starter Kit](#exercise-3-hardhat-starter-kit-testnet-setting-up-the-hardhat-starter-kit)
    - [Exercise 3: Hardhat Starter Kit Testnet: Deploying The Smart Contracts](#exercise-3-hardhat-starter-kit-testnet-deploying-the-smart-contracts)
    - [Exercise 3: Hardhat Starter Kit Testnet: Deploying The Smart Contracts](#exercise-3-hardhat-starter-kit-testnet-deploying-the-smart-contracts-1)
    - [Exercise 3: Hardhat Starter Kit Testnet: Bonus Task Script Exercise](#exercise-3-hardhat-starter-kit-testnet-bonus-task-script-exercise)
  - [Exercise 4: Testing Smart Contracts](#exercise-4-testing-smart-contracts)
    - [Exercise 4: Testing Smart Contracts: Executing the Unit Tests](#exercise-4-testing-smart-contracts-executing-the-unit-tests)
    - [Exercise 4: Testing Smart Contracts: Executing the Staging Tests (Previously Integration)](#exercise-4-testing-smart-contracts-executing-the-staging-tests-previously-integration)
    - [Exercise 4: Testing Smart Contracts: Checking the Solidity Coverage](#exercise-4-testing-smart-contracts-checking-the-solidity-coverage)
    - [Exercise 4: Testing Smart Contracts: Checking in your Project To a Public Code Repository](#exercise-4-testing-smart-contracts-checking-in-your-project-to-a-public-code-repository)
  - [Appendix: Troubleshooting](#appendix-troubleshooting)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Day 2 Exercises

![image](https://user-images.githubusercontent.com/11134288/200854512-63ee4ec7-0a5c-494b-99de-2454764e33a2.png)

---

## Exercise 1: My First Hardhat Project

In this exercise, you’ll use [Hardhat](https://www.google.com/url?q=https://hardhat.org/&sa=D&source=editors&ust=1668004461253715&usg=AOvVaw0ZVRpUhX3BAGi8U4futqsq) to create a new project that contains a simple smart contract that stores and retrieves a value, then you’ll deploy it to the Goerli network and interact with it.

---

### Exercise 1: My First Hardhat Project: Setting Up Hardhat

1. Open Visual Studio Code [https://code.visualstudio.com/](https://www.google.com/url?q=https://code.visualstudio.com/&sa=D&source=editors&ust=1668004461254881&usg=AOvVaw3srqt5dSfnzcwXocQYsoiH)

2. On the top header menu, choose View -> Terminal to bring up the VS Terminal (or press CTRL + `)

3. In your terminal, create a new directory called ‘my-first-hardhat’ using the mkdir command.

```sh
mkdir my-first-hardhat
```

4. Head into the directory by typing ‘cd my-first-hardhat’

```sh
cd my-first-hardhat
```

![image](https://user-images.githubusercontent.com/11134288/200845012-e8a899d7-5526-4845-8efa-14b15499695a.png)

5. In the top VS menu, choose File->Open (or Open Folder), then find your ‘my-first-hardhat’ directory and choose Open. You should now see an explorer menu on the left hand side. Accept any pop-up windows asking you if you trust the content in the directory. If the terminal in VS Code is gone, re-open it by going to View->Terminal

![image](https://user-images.githubusercontent.com/11134288/200845069-57e6b41f-d997-48df-83d5-b8d3f73be3e4.png)

6. We’re now ready to initiate a new Hardhat project. Type the following commands into the terminal to download the hardhat libraries to the current directory, and initiate a new hardhat project. The second one may take a while to complete. You can ignore any warnings about vulnerabilities.

```sh
yarn add hardhat

yarn hardhat
```

7. Using the arrow keys, select the ‘Create an empty hardhat.config.js’ option and hit enter

![image](https://user-images.githubusercontent.com/11134288/200846171-ea5401ba-9567-4019-96b6-f9c20c3ec145.png)

8. You should now see the following folder and file structure in your explorer

![image](https://user-images.githubusercontent.com/11134288/200846247-a88ea859-ff6c-43b9-a76b-0b9e7ce9de19.png)

9. For this exercise we’re going to use the [Ethers.js](https://www.google.com/url?q=https://docs.ethers.io/v5/&sa=D&source=editors&ust=1668004461261628&usg=AOvVaw2A8fDGxUPMQaCV4i4q6bj8) plugin. This will allow us to interact with Ethereum from outside the blockchain, using JavaScript. Run the following command in your terminal to install the ethers.js library, you can ignore any listed vulnerabilities.

```sh
yarn add --dev @nomiclabs/hardhat-ethers 'ethers@^5.0.0'
```

10. Another library we’ll need is the [‘dotenv’](https://www.google.com/url?q=https://github.com/motdotla/dotenv&sa=D&source=editors&ust=1668004461262947&usg=AOvVaw1Afn2hpX1wCKpSTmjNVwHI) library, which facilitates the loading of sensitive configuration data (such as keys) from a config file separate to your code. Install the library using the following command

```sh
yarn add --dev dotenv
```

11. Open the **hardhat.config.js** file in the explorer. This file contains all the configuration for your hardhat project.

12. Replace the contents of the file with the following configuration, then save your changes. This configuration does the following:
    - a. Tells hardhat to use the ethers library, as well as the dotenv library for loading environment variables from a .env config file
    - b. Specifies the networks that can be used for when we deploy smart contracts, in this case we will set the default to the Goerli testnet.
    - c. Specifies a solidity compiler version to use for compiling our smart contracts

```js
require("@nomiclabs/hardhat-ethers");
require('dotenv').config()

/**
* @type import('hardhat/config').HardhatUserConfig
*/
module.exports = {
 defaultNetwork: "goerli",
   networks: {
       hardhat: {
           // // If you want to do some forking, uncomment this
           // forking: {
           //   url: MAINNET_RPC_URL
           // }
       },
       localhost: {
       },
       goerli: {
           url: process.env.GOERLI_RPC_URL,
           accounts: [process.env.PRIVATE_KEY],
           saveDeployments: true,
       }
   },
 solidity: "0.7.3",
};
```

13. Now that we have a config file, we need to set up environment variables for our GOERLI_RPC_URL and PRIVATE_KEY environment variables listed in the config file. So that we don’t include them in our main code, we’re going to put them in a separate .env file that the config can read. This .env file will not be checked into any public code repositories. In the explorer, first click on the blank space under the ‘MY-FIRST-HARDHAT’ folder structure to ensure you’ve selected the top level folder to put your file in. You’ll know the top level is selected if you get a blue outline over your entire folder structure

![image](https://user-images.githubusercontent.com/11134288/200847481-7a219bc4-efa7-4fbd-b3e8-0bc33d103ef1.png)

14. Then directly to the right of your folder name ‘MY-FIRST-HARDHAT’, press the new file button to create a new file, call it **.env**

![image](https://user-images.githubusercontent.com/11134288/200847797-e6287e49-0ca5-4620-88b4-64701d557b89.png)

15. Open your newly created .env file in the editor by double clicking on it in the explorer window. Put the following text in the file

```sh
GOERLI_RPC_URL='abc'
PRIVATE_KEY='123'
```

16. Replace the contents of the GOERLI_RPC_URL string (abc), with the URL that you saved when you signed up for a free Alchemy key as part of the setup steps. It should be something like this: **https://eth-mainnet.g.alchemy.com/v2/k9jZ1Oykh5aOIRh5ZWD9Fs_XVxVO-p4r**

17. Now we need to put our MetaMask wallet account private key in the PRIVATE_KEY environment variable. This will allow Hardhat to use our MetaMask wallet account to deploy and interact with contracts, so you don’t have to manually use MetaMask and approve transactions. Open up MetaMask, press on the three dots to the right of your account name, then select Account Details -> Export private key, enter in your password, then copy your private key string, and paste it into your .env file PRIVATE_KEY string.

    **NOTE: BE CAREFUL WITH COPYING AND PASTING PRIVATE KEYS FOR ACCOUNTS THAT HAVE MAINNET FUNDS IN THEM**

![image](https://user-images.githubusercontent.com/11134288/200851947-14ba5af2-a338-41b3-88ca-ac418d4ff863.png)

18. Your .env file should look something like this (but with different hash values). Save the file. Our hardhat configuration is now ready, and we’re ready to create a smart contract

```
GOERLI_RPC_URL='https://eth-rinkeby.alchemyapi.io/v2/VN0llkGlpo2sQ8VnrsevIZwPBmxbxQ'
PRIVATE_KEY='43905lksjssfd403530LKHdslhs084k3l45hkl34h5kl34hlksmd48543085s'
```

---

### Exercise 1: My First Hardhat Project: Creating The Smart Contract

1. In the explorer window on the left, click on the blank space under the ‘MY-FIRST-HARDHAT’ folder structure to ensure you’ve selected the top level folder. You’ll know the top level is selected if you get a blue outline over your entire folder structure

2. Then select the ‘New Folder’ icon, create a new folder called ‘contracts’. If you already have an empty contracts folder, you can skip this step.

![image](https://user-images.githubusercontent.com/11134288/200855715-6e0c49ad-8027-4375-b60e-7d8741330d5e.png)

3. Select the new contract folder in the explorer to ensure it’s highlighted, then select the ‘New File’ icon, and create a new file, call it ‘MyFirstContract.sol’, and press enter. Ensure it’s been created in the contracts folder.

![image](https://user-images.githubusercontent.com/11134288/200855682-51113380-32c0-43e7-8e1c-9811ea89835b.png)

4. If it isn’t already open, open your new MyFirstContract.sol file by double clicking it in the explorer menu. Paste the following into the smart contract file, then save your changes. This is the same smart contract that you created in the first day of the bootcamp.

```solidity
pragma solidity =0.7.3;
contract MyFirstContract {

   uint256 number;


   function setNumber(uint256 _num) public {
       number = _num;
   }


   function getNumber() public view returns (uint256){
       return number;
   }
}
```

5. Now that you’ve created your smart contract, you can compile it. In the terminal, type in the following command to compile your smart contract using the hardhat compiler.

```sh
yarn hardhat compile
```

![image](https://user-images.githubusercontent.com/11134288/200855541-56b1e0c4-76fa-43fb-8ee4-9ba699eaf5bb.png)

6. You now have our smart contract ready to be deployed! Next you’ll create a script to deploy the smart contract to the Goerli network, and execute the two functions in it

---

### Exercise 1: My First Hardhat Project: Deploying and Interacting With the Smart Contract

Next you will create a script to deploy and then interact with your smart contract.

7. Similar to how you did previously, create a new folder in your project, call it ‘scripts’, ensuring it gets created at your topmost folder level in your project. Then inside the new folder, create a new file called ‘deploy.js’.

![image](https://user-images.githubusercontent.com/11134288/200855965-5d798168-8f8e-4ae5-bd86-ab15ea676907.png)

8. Paste the following code into the newly created file, then save your changes. This script does the following:
    - Deploys your compiled smart contract
    - Obtains the deployed smart contract, and calls the ‘setNumber’ function
    - Calls the ‘getNumber’ function on the deployed contract

```js
async function main() {

   const [deployer] = await ethers.getSigners();

   console.log(
     "Deploying contracts with the account:",
     deployer.address
   );

   console.log("Account balance:", (await deployer.getBalance()).toString());

   const MyFirstContract = await ethers.getContractFactory("MyFirstContract");
   const deployedContract = await MyFirstContract.deploy();
   console.log("Deployed MyFirstContract contract address:", deployedContract.address);


   await deployedContract.setNumber(7)

   let result = BigInt(await deployedContract.getNumber()).toString()
   console.log('Stored value in contract is: ', result)


 }

 main()
   .then(() => process.exit(0))
   .catch(error => {
     console.error(error);
     process.exit(1);
   });
```

9. You’re now ready to deploy your smart contract to the Goerli network, and interact with it. Back in the terminal, enter the following command to deploy your smart contract to the Goerli network, and then execute the functions in the contract. If you don’t specify a network in the command, Hardhat will use the default one in your hardhat.config.js file (which is set to the Goerli network). If you get an error stating you have insufficient funds, ensure your MetaMask account has some ETH in it, as per the [setup instructions](https://www.google.com/url?q=https://chain.link/bootcamp/hardhat-setup-instructions&sa=D&source=editors&ust=1668004461289952&usg=AOvVaw0XDmILjjrpW8v0NmZKI5fX).

```sh
yarn hardhat run scripts/deploy.js
```

10. You should see your contract deployed to a new contract address on the Goerli network, and you should see your function calls successfully set and return a value in the smart contract.

![image](https://user-images.githubusercontent.com/11134288/200856322-d01fa676-f06f-461c-9f8b-c4be671bbc7e.png)

11. Copy the deployed storage contract address specified in the output, and search for it on [https://goerli.etherscan.io/](https://www.google.com/url?q=https://goerli.etherscan.io/&sa=D&source=editors&ust=1668004461292652&usg=AOvVaw2_I5ycoMzj3BaStSsbWBD3). You should see two transactions, the creation of the contract, as well as a transaction to set the number listed in the transactions

![image](https://user-images.githubusercontent.com/11134288/200856362-58295ad7-2731-46f4-8179-4bb858077e3e.png)

12. Congratulations, you’ve successfully created a new smart contract project using the Hardhat Development Environment, deployed it to a public test network, and interacted with your deployed smart contract!

---

### Exercise 1: My First Hardhat Project: Token Bonus Exercise

You can attempt to complete these exercises if you’ve completed the main exercise ahead of schedule:

1. Create a new contract in the contracts folder called ERC-20.sol. Open the file, and enter in the full source code for the ERC20 token contract example on the [Ethereum developer tutorials page](https://www.google.com/url?q=https://ethereum.org/en/developers/tutorials/understand-the-erc-20-token-smart-contract/&sa=D&source=editors&ust=1668004461295730&usg=AOvVaw1MdlYDCoVmyfRrc4sVirat). The only changes you need to make is to update the pragma Solidity version at the top of the contract, and you should also comment out (put // at the beginning of the lines) the two ‘Approval’ and ‘Transfer’ events in the ERC20Basic contract to avoid possible compilation issues around duplicate events in the interface contract and the main contract. In addition to this, you can modify the token Symbol from ERC to whatever you choose. Save your file.

```solidity
pragma solidity =0.7.3;

interface IERC20 {

   function totalSupply() external view returns (uint256);
   function balanceOf(address account) external view returns (uint256);
   function allowance(address owner, address spender) external view returns (uint256);

   function transfer(address recipient, uint256 amount) external returns (bool);
   function approve(address spender, uint256 amount) external returns (bool);
   function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);


   event Transfer(address indexed from, address indexed to, uint256 value);
   event Approval(address indexed owner, address indexed spender, uint256 value);
}


contract ERC20Basic is IERC20 {

   string public constant name = "ERC20Basic";
   string public constant symbol = "ERC";
   uint8 public constant decimals = 18;


   //event Approval(address indexed tokenOwner, address indexed spender, uint tokens);
   //event Transfer(address indexed from, address indexed to, uint tokens);


   mapping(address => uint256) balances;

   mapping(address => mapping (address => uint256)) allowed;

   uint256 totalSupply_;

   using SafeMath for uint256;


  constructor(uint256 total) public {
   totalSupply_ = total;
   balances[msg.sender] = totalSupply_;
   }

   function totalSupply() public override view returns (uint256) {
   return totalSupply_;
   }

   function balanceOf(address tokenOwner) public override view returns (uint256) {
       return balances[tokenOwner];
   }

   function transfer(address receiver, uint256 numTokens) public override returns (bool) {
       require(numTokens <= balances[msg.sender]);
       balances[msg.sender] = balances[msg.sender].sub(numTokens);
       balances[receiver] = balances[receiver].add(numTokens);
       emit Transfer(msg.sender, receiver, numTokens);
       return true;
   }

   function approve(address delegate, uint256 numTokens) public override returns (bool) {
       allowed[msg.sender][delegate] = numTokens;
       emit Approval(msg.sender, delegate, numTokens);
       return true;
   }

   function allowance(address owner, address delegate) public override view returns (uint) {
       return allowed[owner][delegate];
   }

   function transferFrom(address owner, address buyer, uint256 numTokens) public override returns (bool) {
       require(numTokens <= balances[owner]);
       require(numTokens <= allowed[owner][msg.sender]);

       balances[owner] = balances[owner].sub(numTokens);
       allowed[owner][msg.sender] = allowed[owner][msg.sender].sub(numTokens);
       balances[buyer] = balances[buyer].add(numTokens);
       emit Transfer(owner, buyer, numTokens);
       return true;
   }
}

library SafeMath {
   function sub(uint256 a, uint256 b) internal pure returns (uint256) {
     assert(b <= a);
     return a - b;
   }

   function add(uint256 a, uint256 b) internal pure returns (uint256) {
     uint256 c = a + b;
     assert(c >= a);
     return c;
   }
}
```

2. Create a new script in the scripts folder called ‘deploy-erc20.js’. Base the contents of the deploy script on your existing ‘deploy.js’ file.

3. Modify the deploy script so that it deploys your ‘ERC20Basic’ contract instead of the ‘MyFirstContract’ one. You should do the following:
    * a. rename all variables specific to the storage contract to be specific to your new ERC20 one.
    * b. Remove anything after the console.log statement that states which address the contract was deployed to
    * c. Update the console.log statement to say ‘Deployed ERC20 contract address’
    * d. In the .deploy command, pass in an initial total supply into the empty brackets, this will pass in the value to the constructor in the ERC20Basic contract

Spoiler/Solution (highlight to see)<br />

<details>

```js
async function main() {


    const [deployer] = await ethers.getSigners();


    console.log(

      "Deploying contracts with the account:",

      deployer.address

    );


    console.log("Account balance:", (await deployer.getBalance()).toString());

    const erc20Basic = await ethers.getContractFactory("ERC20Basic");

    const deployedContract = await erc20Basic.deploy(100000000);

    console.log("Deployed ERCC20 contract address:", deployedContract.address);


  }


  main()

    .then(() => process.exit(0))

    .catch(error => {

      console.error(error);

      process.exit(1);

    });
```

</details><br />

4. Compile all contracts in your project, then execute your new script

```sh
yarn hardhat compile
```

```sh
yarn hardhat run scripts/deploy-erc20.js
```

5. Look for your deployed contract on [https://goerli.etherscan.io/](https://www.google.com/url?q=https://goerli.etherscan.io/&sa=D&source=editors&ust=1668004461316617&usg=AOvVaw0C9EZ_x04ScRPr5l9QS4Bs).

6. Append to your new script to send yourself some tokens with the deployed contract by calling the required functions, and passing in the parameters. For now you can hardcode your wallet address values, you can obtain them from MetaMask. I.e send tokens from your current account that you have setup in the private key environment variable, and send them to another wallet address in your MetaMask. Check your transaction in Etherscan.

7. Copy the deployed address of your token, and add the token to your MetaMask wallet with the ‘Add Token’ button at the bottom of the Assets section. Paste in your contract address and add the token. You should see the balance of the token in your assets section

![image](https://user-images.githubusercontent.com/11134288/200857351-0a48285b-a5ec-44d8-b475-7f81e8a2163b.png)

---

## Exercise 2: Deploying to a Local Network

In this exercise, you’ll download the Hardhat Starter Kit, and use it to create, deploy and execute smart contracts that use Chainlink Data Feeds, Any-API, and VRF to a local blockchain. This will show you how professionals work with their repos, code, debug, and develop.

---

### Exercise 2: Deploying to a Local Network: Downloading the Hardhat Starter Kit

1. In VS Code, go to your terminal, then go back to your home folder by typing in ‘cd ..’ and pressing enter

```sh
cd ..
```

2. Pull a copy of the Hardhat Starter Kit with the following command:

```sh
git clone https://github.com/smartcontractkit/hardhat-starter-kit
```

![image](https://user-images.githubusercontent.com/11134288/200886011-b0d4c405-0f13-4716-93c9-6b1a788046a0.png)

3. In your terminal, you need to change the directory to your copy of the Hardhat Starter Kit that you downloaded in the previous step. Then you need to install all of the library dependencies that the starter kit requires. Run the following commands. The second one that installs the libraries may take a couple of minutes. You can ignore any listed vulnerabilities.

```sh
cd hardhat-starter-kit
yarn
```

4. Because we now have a new project in a new folder, we need to switch to it in Visual Studio Code. Choose File-> Open, find the ‘hardhat-starter-kit- folder, select it and press Open. If your VS Terminal has disappeared, re-open it by selecting View-> Terminal (or pressing CTRL + `). Your VS Code should look like this:

![image](https://user-images.githubusercontent.com/11134288/200889065-6ebf9142-48c1-4930-96b1-dca916f4818a.png)

---

### Exercise 2: Deploying to a Local Network: Setting up the Local Hardhat Network

1. Open Visual Studio Code, ensure your current project is the ‘hardhat-starter-kit’ workspace from day 2 of the Developer Bootcamp (hint: If it’s not, go File -> Open, and select the ‘hardhat-starter-kit’ folder)

2. If it’s not already open, open the VS Terminal (View -> Terminal or CTRL + `)

3. If you’re not already in it, head into your ‘hardhat-starter-kit’ folder in the terminal

![image](https://user-images.githubusercontent.com/11134288/200889664-c5e6edb1-af09-4112-a1c7-cf8330348691.png)

4. Next, you need to ensure you’ve set the MAINNET_RPC_URL environment variable in the .env file. This will be used to create a fork of the Ethereum mainnet when we deploy to our local Hardhat network later on. Do this by taking the URL you noted from when you signed up to Alchemy in the [bootcamp setup instructions](https://www.google.com/url?q=https://chain.link/bootcamp/hardhat-setup-instructions&sa=D&source=editors&ust=1668004461325358&usg=AOvVaw05bQgcyxWUWEhXPRjIBDhf), and pasting it in an ‘MAINNET_RPC_URL’ variable in your .env file

```sh
MAINNET_RPC_URL='https://eth-mainnet.alchemyapi.io/v2/insert_key_here',
```

Your .env file should look like this:

```sh
MAINNET_RPC_URL='https://eth-mainnet.alchemyapi.io/v2/insert_key_here'
```

5. Before you start the local hardhat network, you need to modify the ‘hardhat.config.js’ file, and tell it to use the local Hardhat network by default. Open it up, and set the ‘defaultNetwork’ config to “hardhat”. In addition to this, ensure you have the PRIVATE_KEY field uncommented out, and the MNEMONIC field commented out. It should match the code below (highlighted in bold):

```js
module.exports = {
    defaultNetwork: "hardhat",
    networks: {
        hardhat: {
           // // If you want to do some forking, uncomment this
           // forking: {
           //   url: MAINNET_RPC_URL
           // }
       },
        localhost: {
       },
        goerli: {
            url: GOERLI_RPC_URL,
             accounts: [PRIVATE_KEY],
           //accounts: {
           //    mnemonic: MNEMONIC,
           //},
            saveDeployments: true,
       },
```

6. Now you can start your local hardhat network. You should run it separately in a terminal window, so it can also be referenced by other applications if needed. You can open a second terminal window by pressing the ‘+’ icon near the bottom right of VS Code, so you can have one open for commands, and one for your hardhat local network. You can easily switch between the two.

![image](https://user-images.githubusercontent.com/11134288/200890046-c0f63755-ee2f-47b6-9340-e39daff40814.png)

Once you have a second terminal open, run the following command in the terminal

**NOTE**: You can use `yarn` and `npx` interchangeably.

```
yarn hardhat node
```

If you get any errors starting the node, please refer to possible solutions in the [Troubleshooting Appendix](https://docs.google.com/document/d/e/2PACX-1vQ8_Jd-XNphvXN3Qb0eS0X-mJ5sJhpiZJPp5eq7aL-7UF4z2quPfl9m2mXVjZ77tflwR7t7QxelBkzs/pub#h.820bgoqlcmfx)

![image](https://user-images.githubusercontent.com/11134288/200890155-ff8c215d-06cc-4c2b-a1f8-426c0064f411.png)

You’re now ready to deploy the starter kit smart contracts to a local hardhat network!

This did two things:

  1. Deployed your smart contracts
  2. Spun up a local blockchain node on the `localhost` network (a special hardhat-like network)

---

### Exercise 2: Deploying to a Local Network: Deploying and Interacting With the Smart Contracts

All of the smart contracts in your project are now deployed to a simulated local Ethereum network running on your computer, and they’re ready for you to start interacting with them. You’ll notice that ‘mock contracts’ were deployed to simulate interacting with the Chainlink oracle network, this is because Chainlink doesn’t know about your local network.

**Price Feed Consumer Contract**

1. To interact with the deployed Price Feed Consumer contract, run the ‘read-price-feed’ task, which will query the deployed smart contract, and return the latest price of the specified price feed. You can do this by running the following command, replacing the contract address with the one specified in your console output for the deployed PriceConsumerV3 contract. Alternatively, the console output during deployment gives you the exact command to run to query the PriceConsumerV3 contract, you can copy and paste the command directly from there

```
yarn hardhat read-price-feed --contract replace-with-your-PriceConsumerV3-address --network localhost
```

As you can see, the value returned isn’t the current price of ETH/USD, because in our '01_Deploy_PriceConsumerV3.js' deploy script, we deployed a mock aggregator contract to mimic an actual aggregator contract, and the value is set to a static amount.

---

### Exercise 2: Deploying to a Local Network: Forking Ethereum Mainnet

1. Now that you’ve got a local Hardhat network working, let's modify it and change its initial state to be a fork of the current Ethereum mainnet. First thing you need to do, is modify the hardhat.config.js file, and uncomment the line in the hardhat network section that mentions the MAINNET_RPC_URL. It should look like this

```js
defaultNetwork: "hardhat",
    networks: {
        hardhat: {
            // If you want to do some forking, uncomment this
             forking: {
               url: MAINNET_RPC_URL
            }
       },
```

    Before you start working with our local forked network, modify the Price Consumer deploy script, and the helper-hardhat-config.js file, so that we can reference the actual ETH/USD price feed contract that’s currently on mainnet.

2. Open the file helper-hardhat-config.js, and add the ‘ethUsdPriceFeed’ config to the 31337 network . This is your locally running forked hardhat network. The value for this config will be ‘0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419’, set to the contract address of the ETH/USD price feed on Ethereum mainnet, taken from The [Chainlink Price Feeds Contract Documentation](https://www.google.com/url?q=https://docs.chain.link/docs/ethereum-addresses/&sa=D&source=editors&ust=1668004461340580&usg=AOvVaw18sCJ0bkOwt9XRnCYAH5pM). Your config for the 31337 network should look like this in the file. Save the changes before continuing.

```js
31337: {
       name: 'localhost',
       fee: '100000000000000000',
       keyHash: '0x6c3699283bda56ad74f6b855546325b68d482e983852a7a82979cc4807b641f4',
       jobId: '29fa9aa13bf1468788b7cc4a500a45b8',
       ethUsdPriceFeed: '0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419'
   },
```

3. Next you need to modify your deployment script for the PriceConsumerV3 contract to use your newly added Price Feed config. Open the ‘01_Deploy_PriceConsumerV3.js’ script from the ‘deploy’ folder. Find the logic in the script that checks to see if the chain ID is 31337, and if so to set the aggregator contract to the deployed mock one, and comment it out (add // at the beginning of the lines). You now want to always look up which aggregator contract to use from our config, even when working with a local network. This part of the script should look like the following. Changes are in bold

```js
//if (chainId == 31337) {
       //const EthUsdAggregator = await deployments.get('EthUsdAggregator')
      // ethUsdPriceFeedAddress = EthUsdAggregator.address
  // } else {
       ethUsdPriceFeedAddress = networkConfig[chainId]['ethUsdPriceFeed']
  // }

let ethUsdPriceFeedAddress = networkConfig[chainId]["ethUsdPriceFeed"]
```

    You’re now ready to deploy your smart contracts to a local forked network!

4. Now you need to go back to your VS Code terminal window, the one that’s running the local hardhat node. You need to ‘kill’ and restart the process, so it can pick up the new config and fork mainnet. You can kill the currently running node by switching to the terminal currently running the hardhat node, and typing CTRL + C

![image](https://user-images.githubusercontent.com/11134288/202930590-5ae84757-6943-45b8-986d-fc0602d2fdf5.png)

![image](https://user-images.githubusercontent.com/11134288/202930597-9dce2fa7-04d4-4ff1-9ffa-f4a86268e93f.png)

    Once the process has been killed, you can restart it using the following command (or press the up key to find it in your command history)

```
yarn hardhat node
```

    If you have issues starting the hardhat node, refer to the [Troubleshooting Appendix](https://docs.google.com/document/d/e/2PACX-1vQ8_Jd-XNphvXN3Qb0eS0X-mJ5sJhpiZJPp5eq7aL-7UF4z2quPfl9m2mXVjZ77tflwR7t7QxelBkzs/pub#h.820bgoqlcmfx) for suggestions

5. To test that we’re actually working with a fork of mainnet, we can execute the ‘block-number’ task that comes included with the hardhat starter kit. This task can be found in the tasks folder (block-number.js), and simply returns the current block number in the blockchain.

```
yarn hardhat block-number --network localhost
```

![image](https://user-images.githubusercontent.com/11134288/202930720-b5b379cb-35b4-4fc3-b64f-c7b37b117e4a.png)

    If it were a normal local hardhat network, the block number would be 0. You can compare the returned block number to the current mainnet block at [https://etherscan.io/](https://etherscan.io/). The one at etherscan may be a few blocks ahead, by the time you deploy and then execute the block-number task etc. Now you’re ready to execute the read-price-feed task to interact with the Price Feed consumer contract.

6. As per the output in the terminal when you deploy the smart contracts, run the command to execute the read-price-feed task, passing in the correct contract address as shown in the deploy output. The result should be that the returned price feed should be the price on the current Ethereum mainnet ETH/USD feed

```
yarn hardhat read-price-feed --contract insert-contract-address-here --network localhost
```

![image](https://user-images.githubusercontent.com/11134288/202930786-1752bc72-b069-414e-bfb5-8c974aa6c45b.png)

If you go to the page for the [ETH/USD feed on Ethereum mainnet](https://www.google.com/url?q=https://data.chain.link/ethereum/mainnet/crypto-usd/eth-usd&sa=D&source=editors&ust=1668004461355297&usg=AOvVaw0mhQyXzPULQt04CwSJ0cWI), you should see a matching result (or similar if a few blocks have passed)

![image](https://user-images.githubusercontent.com/11134288/202930809-e0ed47ed-c98f-4106-8886-b815778aa8ab.png)

Congratulations, you’ve successfully used Hardhat to perform the following:

  1. Deploy smart contracts to a local network
  2. Interacted with deployed smart contracts and mock contracts on a local network
  3. Created a fork of the Ethereum mainnet on a local network, deployed smart contracts to it, and interacted with the mainnet ETH/USD price feed.

---

### Exercise 2: Deploying to a Local Network: Bonus Fork Exercise

You can attempt to complete these exercises if you’ve completed the main exercise ahead of schedule:

Read the [Mainnet Forking](https://www.google.com/url?q=https://hardhat.org/guides/mainnet-forking.html&sa=D&source=editors&ust=1668004461358396&usg=AOvVaw229b9mXJ313zgz7YQ2FGl_) documentation in the hardat documentation, and try to fork mainnet at a specific block back in time, either by adding in the ‘blockNumber’ property into your hardhat.config.js file, or via the ‘fork-block-number’ parameter when you start your forked hardhat node.

```
yarn hardhat node --fork https://eth-mainnet.alchemyapi.io/v2/<key> --fork-block-number 11095000
```

Run the block-number task each time you fork at a different block to ensure the chain has been forked at the right place, then execute the ‘read-price-feed’ task to see what the price of ETH/USD was in the Chainlink ETH/USD price feed at the time.

---

## Exercise 3: Hardhat Starter Kit Testnet

In this exercise, you’ll download the Hardhat Starter Kit, and use it to create, deploy and execute smart contracts that use Chainlink Data Feeds, Any-API and VRF. This will give you some real world experience in using hardhat to deploy and interact with smart contracts using hardhats built in tasks feature.

---

### Exercise 3: Hardhat Starter Kit Testnet: Setting Up The Hardhat Starter Kit

1. Open the **hardhat.config.js** file in the explorer. This file contains all the configuration for your hardhat project.

2. You should ensure the ‘defaultNetwork’ field is set to Goerli, as we will be deploying to the Goerli network. The config file should look like this.

```js
require("@nomicfoundation/hardhat-toolbox")
require("./tasks")
require("dotenv").config()

const MAINNET_RPC_URL =
   process.env.MAINNET_RPC_URL ||
   process.env.ALCHEMY_MAINNET_RPC_URL ||
   "https://eth-mainnet.alchemyapi.io/v2/your-api-key"
const POLYGON_MAINNET_RPC_URL =
   process.env.POLYGON_MAINNET_RPC_URL || "https://polygon-mainnet.alchemyapi.io/v2/your-api-key"
const GOERLI_RPC_URL =
   process.env.GOERLI_RPC_URL || "https://eth-goerli.alchemyapi.io/v2/your-api-key"
const PRIVATE_KEY = process.env.PRIVATE_KEY

// optional
const MNEMONIC = process.env.MNEMONIC || "Your mnemonic"
const FORKING_BLOCK_NUMBER = process.env.FORKING_BLOCK_NUMBER

// Your API key for Etherscan, obtain one at https://etherscan.io/
const ETHERSCAN_API_KEY = process.env.ETHERSCAN_API_KEY || "Your etherscan API key"
const POLYGONSCAN_API_KEY = process.env.POLYGONSCAN_API_KEY || "Your polygonscan API key"
const REPORT_GAS = process.env.REPORT_GAS || false

/** @type import('hardhat/config').HardhatUserConfig */
module.exports = {
   solidity: {
       compilers: [
           {
               version: "0.8.7",
           },
           {
               version: "0.6.6",
           },
           {
               version: "0.4.24",
           },
       ],
   },
   networks: {
       hardhat: {
           hardfork: "merge",
           // If you want to do some forking set `enabled` to true
           forking: {
               url: MAINNET_RPC_URL,
               blockNumber: FORKING_BLOCK_NUMBER,
               enabled: false,
           },
           chainId: 31337,
       },
       localhost: {
           chainId: 31337,
       },
       goerli: {
           url: GOERLI_RPC_URL,
           accounts: PRIVATE_KEY !== undefined ? [PRIVATE_KEY] : [],
           //   accounts: {
           //     mnemonic: MNEMONIC,
           //   },
           chainId: 5,
       },
       mainnet: {
           url: MAINNET_RPC_URL,
           accounts: PRIVATE_KEY !== undefined ? [PRIVATE_KEY] : [],
           //   accounts: {
           //     mnemonic: MNEMONIC,
           //   },
           chainId: 1,
       },
       polygon: {
           url: POLYGON_MAINNET_RPC_URL,
           accounts: PRIVATE_KEY !== undefined ? [PRIVATE_KEY] : [],
           chainId: 137,
       },
   },
   defaultNetwork: "goerli",
   etherscan: {
       // yarn hardhat verify --network <NETWORK> <CONTRACT_ADDRESS> <CONSTRUCTOR_PARAMETERS>
       apiKey: {
           polygon: POLYGONSCAN_API_KEY,
           goerli: ETHERSCAN_API_KEY,
       },
   },
   gasReporter: {
       enabled: REPORT_GAS,
       currency: "USD",
       outputFile: "gas-report.txt",
       noColors: true,
       // coinmarketcap: process.env.COINMARKETCAP_API_KEY,
   },
   contractSizer: {
       runOnCompile: false,
       only: [
           "APIConsumer",
           "AutomationCounter",
           "NFTFloorPriceConsumerV3",
           "PriceConsumerV3",
           "RandomNumberConsumerV2",
       ],
   },
   paths: {
   sources: "./contracts",
   tests: "./test",
   cache: "./build/cache",
   artifacts: "./build/artifacts"
   },
   mocha: {
       timeout: 200000, // 200 seconds max for running tests
   },
}
```

3. Next, you need to set up environment variables for your GOERLI_RPC_URL and PRIVATE_KEY environment variables listed in the config file. Similar to the last exercise, create a new file in the hardhat-starter-kit folder, call it .env. If a file already exists, simply open it and use that as your starting point.

4. Open your .env file in the editor by double clicking on it in the explorer window. Put the following text in the file

```
GOERLI_RPC_URL='https://eth-goerli.alchemyapi.io/v2/insert_key_here'
MAINNET_RPC_URL='https://eth-mainnet.alchemyapi.io/v2/insert_key_here'
```

5. Replace the contents of the GOERLI_RPC_URL string (abc), with the URL that you saved when you signed up for a free Alchemy key as part of the setup steps. It should be something like this: **https://eth-goerli.g.alchemy.com/v2/dqlyaJY43jSetctkshuCQXIAult2Jp48**

6. Now you need to put our MetaMask wallet account private key in the PRIVATE_KEY environment variable. Open up MetaMask, press on the three dots to the right of your account name, then select Account Details -> Export private key, enter in your password, then copy your private key string, and paste it into your .env file PRIVATE_KEY string.

**NOTE: BE CAREFUL WITH COPYING AND PASTING PRIVATE KEYS FOR ACCOUNTS THAT HAVE MAINNET FUNDS IN THEM**

**IF THIS METAMASK HAS MONEY IN IT, USE A DIFFERENT ONE!**

![image](https://user-images.githubusercontent.com/11134288/202933066-bde1c0ad-9fc4-4adb-ac18-1abc75d00291.png)

7. Your .env file should look something like this (but with different hash values). Save the file. Our hardhat starter kit configuration is now ready, and we’re ready to deploy our smart contracts

```
GOERLI_RPC_URL='https://eth-goerli.alchemyapi.io/v2/insert_key_here'
PRIVATE_KEY='private_key_hash_here'
MAINNET_RPC_URL='https://eth-mainnet.alchemyapi.io/v2/insert_key_here'
```

---

### Exercise 3: Hardhat Starter Kit Testnet: Deploying The Smart Contracts

1. Before you deploy the smart contracts in the hardhat starter kit to the Goerli test network, you should compile them first. Run the following command in the terminal.

```sh
npx hardhat compile
# or
yarn hardhat compile
```

2. Go to [http://vrf.chain.link](https://www.google.com/url?q=http://vrf.chain.link&sa=D&source=editors&ust=1668004461424324&usg=AOvVaw1h628bexQVEfzPjUInZpEN), find your previous subscription and copy the subscription ID, then add it to the helper.hardhat.config file in the goerli section, as per instructions [here](https://www.google.com/url?q=https://github.com/smartcontractkit/hardhat-starter-kit%23vrf-get-a-random-number&sa=D&source=editors&ust=1668004461425677&usg=AOvVaw2rVoF_IWnL7AWA26j9P_zw) as a new field ‘subscriptionId’

    It will  look like this:

```
    5: {
        name: "goerli",
        linkToken: "0x326c977e6efc84e512bb9c30f76e30c160ed06fb",
        ethUsdPriceFeed: "0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e",
        keyHash: "0x79d3d8832d904592c0bf9818b621522c988bb8b0c05cdc3b15aea1b6e8db0c15",
        vrfCoordinator: "0x2Ca8E0C643bDe4C2E08ab1fA0da3401AdAD7734D",
        oracle: "0xCC79157eb46F5624204f47AB42b3906cAA40eaB7",
        jobId: "ca98366cc7314957b8c012c72f05aeeb",
        fee: "100000000000000000",
        fundAmount: "100000000000000000", // 0.1
        automationUpdateInterval: "30",
        subscriptionId: "123"
    },
```

3. Now that our contracts are compiled, run the following command to deploy the smart contracts in the hardhat starter kit to the Goerli test network. You should see output similar to the following screenshot

```
npm run deploy
```

![image](https://user-images.githubusercontent.com/11134288/202933235-98a7c64e-3098-487d-99dc-14b280322ad0.png)

4. Your smart contracts that use Chainlink are now deployed to the Goerli network, and we’re ready to start interacting with them!

---

### Exercise 3: Hardhat Starter Kit Testnet: Deploying The Smart Contracts

**Price Feed Consumer Contract**

1. To interact with the deployed Price Feed Consumer contract, run the ‘read-price-feed’ task, which will query the deployed smart contract, and return the latest price of the specified price feed. You can do this by running the following command, replacing the contract address with the one specified in your console output for the deployed PriceConsumerV3 contract. Alternatively, the console output during deployment gives you the exact command to run to query the PriceConsumerV3 contract, you can copy and paste the command directly from there

```sh
yarn hardhat read-price-feed --contract replace-with-your-PriceConsumerV3-address --network goerli
```

![image](https://user-images.githubusercontent.com/11134288/202933272-f8d53c2e-f29a-4fb5-a62b-792f3b040230.png)

**API Consumer Contract**

2. To interact with the deployed API Consumer contract, first run the ‘request-data’ task to execute the getVolumeData function, which will reach out to the crypto-compare API to obtain the current ETH/USD volume. You can do this by running the following command, replacing the contract address with the one specified in your console output for the deployed APIConsumer contract. Alternatively, the console output during deployment gives you the exact command to run to interact with the APIConsumer contract, you can copy and paste the command directly from there

```sh
yarn hardhat request-data --contract replace-with-your-APIConsumer-address --network goerli
```

3. Now that you’ve performed an external data request, you can execute the ‘read-data’ task to call the volume function in the API Consumer smart contract, and see the result of the external data request. If you get a 0 result, wait 30 seconds and try again, sometimes the callback from the Oracle to Ethereum can take a few seconds for the transaction to confirm.

```sh
yarn hardhat read-data --contract replace-with-your-APIConsumer-address --network goerli
```

![image](https://user-images.githubusercontent.com/11134288/202933389-d77e592f-8eb7-47a3-965a-1a0a5a5b2a5a.png)

You have now successfully performed a request for external data, and obtained the result into your smart contract using a Chainlink oracle. You can verify the result by opening a browser window, heading to [https://min-api.cryptocompare.com/data/pricemultifull?fsyms=ETH&tsyms=USD](https://min-api.cryptocompare.com/data/pricemultifull?fsyms=ETH&tsyms=USD) and then searching for the string **"VOLUME24HOUR"**. As per the logic in the smart contract, the result has been multiplied by 10**18 to avoid any floating point numbers.

![image](https://user-images.githubusercontent.com/11134288/202933462-e4e2286b-80c6-4588-ba64-1367a9594726.png)

**Random Number Consumer Contract**

5. You need to go to your subscription page at [vrf.chain.link](https://www.google.com/url?q=https://vrf.chain.link&sa=D&source=editors&ust=1668004461445253&usg=AOvVaw2-kg_9Oo3ehmY2I_0-Kbhd) and add the address of deployed contract as a new consumer, using the ‘Add Consumer’ button

6. To interact with the deployed Random Number Consumer contract, first run the ‘request-random-number’ task to execute the getRandomNumber function, which will reach out to a Chainlink Oracle and make a request for randomness. You can do this by running the following command, replacing the contract address with the one specified in your console output for the deployed RandomNumberConsumer contract. Alternatively, the console output during deployment gives you the exact command to run to interact with the RandomNumberConsumer contract, you can copy and paste the command directly from there

```sh
yarn hardhat request-random-number --contract replace-with-your-RandomNumberConsumer-address --network goerli
```

![image](https://user-images.githubusercontent.com/11134288/202933518-c7fa670c-9722-4549-a770-71fa731389e7.png)

7. Now that you’ve performed a request for randomness, you can execute the ‘read-random-number’ task to call the randomResult function in the RandomNumberConsumer smart contract, and see the result of the random number request. If you get a 0 result, wait 30 seconds and try again, sometimes the callback from the Oracle to Ethereum can take a few seconds for the transaction to confirm.

```sh
yarn hardhat read-random-number --contract replace-with-your-RandomNumberConsumer-address --network goerli
```

![image](https://user-images.githubusercontent.com/11134288/202933574-a6cfd239-9b5c-4f33-a514-40df93a860b9.png)

Congratulations, you’ve successfully used the Hardhat Starter Kit to perform the following:

  - Deploy three smart contracts to the Goerli testnet
  - Interacted with a deployed smart contract to use Chainlink Data Feeds
  - Interacted with a deployed smart contract to perform an API request using a Chainlink Oracle
  - Interacted with a deployed smart contract to perform a request for randomness using Chainlink VRF

---

### Exercise 3: Hardhat Starter Kit Testnet: Bonus Task Script Exercise

Create a new contract in the contracts folder. You can create or put any contract inside it! If you want some examples, check out the [Solidity docs examples](https://www.google.com/url?q=https://docs.soliditylang.org/en/v0.8.17/solidity-by-example.html&sa=D&source=editors&ust=1668004461452944&usg=AOvVaw1E8qV5uDcxxHZshOA9OdZv).

1. Create a new contract in the contracts folder. You can create or put any contract inside it! If you want some examples, check out the Solidity docs examples.

2. Create a script in the deploy folder to deploy your contract

3. Compile and deploy your contracts to the Goerli network. You may need to update your pragma statement in your new contract to match the version defined in the hardhat.config.js file (or update your hardhat.config.js solidity version to match your new contract pragma version).

```
yarn hardhat compile
```

```
yarn hardhat deploy
```

4. Create a new task for your contract in the tasks folder so you can interact with the contract once it’s deployed

5. Add your task to the tasks/index.js file at the top, where all the other tasks are added

```js
exports.randomNumberConsumer = require("./random-number-consumer")
exports.priceConsumer = require("./price-consumer")
// ...
```

6. Execute your task on the command line, passing in any defined parameters so you can interact with your deployed contract. Here is an example of executing a task called 'task-name' that takes a 'param1' parameter

---

## Exercise 4: Testing Smart Contracts

In this exercise, you’ll execute the unit and integration tests that come with the Hardhat Starter Kit, then do a Solidity Coverage test.

---

### Exercise 4: Testing Smart Contracts: Executing the Unit Tests

1. Ensure your Hardhat Starter Kit project is still using your local Hardhat network as the currently running network, and that the local network is currently running in a terminal window. If not, follow steps from the last exercise to [configure Hardhat](https://docs.google.com/document/d/e/2PACX-1vQ8_Jd-XNphvXN3Qb0eS0X-mJ5sJhpiZJPp5eq7aL-7UF4z2quPfl9m2mXVjZ77tflwR7t7QxelBkzs/pub#h.iz2xku7dtbqb) and start the hardhat node

2. Now you're going to execute the unit tests. These will run a few basic tests against the smart contracts. Run the following command in the console to execute the unit tests

```
yarn test
```

![image](https://user-images.githubusercontent.com/11134288/202934302-e016538b-e356-46a7-96f5-46563719e869.png)

You should see all unit tests pass successfully. Next run the integration tests to test the actual integration of our smart contracts to the Chainlink Oracle network, but first you need to switch your hardhat config again to use the public Goerli test network.

---

### Exercise 4: Testing Smart Contracts: Executing the Staging Tests (Previously Integration)

1. Back in the hardhat.config.js file, change the defaultNetwork to be Goerli

```
defaultNetwork: "goerli",
```

2. Next you need to revert the changes you made earlier when deploying the PriceConsumer contract. Open the ‘01_Deploy_PriceConsumerV3.js’, and revert the changes you made earlier (ie, remove the comment slashes in the if/else statement (or you can use the undo command if you still had the code open from earlier). The if/else statement should look like this. Save your work.

```js
    if (chainId == 31337) {
       const EthUsdAggregator = await deployments.get('EthUsdAggregator')
       ethUsdPriceFeedAddress = EthUsdAggregator.address
   } else {
       ethUsdPriceFeedAddress = networkConfig[chainId]['ethUsdPriceFeed']
   }
```

3. Now that you’re back on the Goerli network, you need to deploy your smart contracts again, by running the following command

```
yarn hardhat deploy
```

    Once the deployment is complete, you can now execute the integration tests by running the following command using yarn

```
yarn hardhat test
```

    The integration tests may take a couple minutes to complete, because they have delays specified in them to give the Chainlink nodes enough time to perform the callback transactions.

![image](https://user-images.githubusercontent.com/11134288/202934676-ed79650d-303b-485e-beec-1488c8baa6ae.png)

You can take the contract address from the output of the contract deployment step earlier, and look them up on [https://goerli.etherscan.io/](https://goerli.etherscan.io/) to see the transactions being performed as part of the integration tests

![image](https://user-images.githubusercontent.com/11134288/202934708-ab7eb42b-da1b-4efd-b6a3-5f7419376680.png)

---

### Exercise 4: Testing Smart Contracts: Checking the Solidity Coverage

The last step in our testing is to check what the Solidity coverage is in our tests.

4. In addition to this, also switch the default network back to ‘hardhat’

```
defaultNetwork: "hardhat",
```

    If you previously stopped your local hardhat node, start it again in a terminal in VS Code with the command you previously started it with. If it’s still running, you can leave it.

```
yarn hardhat node
```

5. Now you’re ready to run the solidity coverage. we’ll run it against the unit tests on the local hardhat network. This will check to see how complete the unit tests are

```
yarn hardhat coverage
```

![image](https://user-images.githubusercontent.com/11134288/202934771-b61d2613-a2a4-4e71-8e0f-639450fb432a.png)

![image](https://user-images.githubusercontent.com/11134288/202934787-6638aa2e-c865-449d-b188-72effc9bf6ff.png)

You can see the report for each contract, and see how much of the code is being tested.

Congratulations, you’ve learned how to install and use the Yarn package manager, how to execute unit tests on a local hardhat network, how to execute integration tests on a public network, and how to check the coverage of your unit tests. Now the last step is checking your project into a public GitHub repository so you can share it with the world!

---

### Exercise 4: Testing Smart Contracts: Checking in your Project To a Public Code Repository

Perform the following steps to check in your hardhat project into a public repository for everyone else to see your work

1. **WARNING**! If you directly pasted in your private key inside your hardhat.config.js file from previous exercises due to an issue where you couldn’t deploy your contracts, it will be checked into a public repository. You should remove any references to your private key in your code before proceeding (apart from the .env file). Here is a way to try to get around the issue. If you didn’t have this issue, and only have the private key in your .env file, please proceed to Step 6

2. Open up your hardhat.config.js file, and ensure the Goerli section under networks is as follows:

```js
 goerli: {
            url: GOERLI_RPC_URL,
             accounts: [PRIVATE_KEY],
           //accounts: {
           //    mnemonic: MNEMONIC,
           //},
            saveDeployments: true,
       },
```

3. Go to your .env file, and copy your private key string, then type the following command into your terminal and press enter

```
export PRIVATE_KEY='insert-private-key-string-here'
```

4. You can test if the environment variable has been set by running the following, you should see your private key displayed.

```
echo $PRIVATE_KEY
```

5. Repeat the step with your GOERLI_RPC_URL variable. Export it to the terminal

```
export GOERLI_RPC_URL='https://eth-goerli.alchemyapi.io/v2/insert_key_here’
```

```
echo $GOERLI_RPC_URL
```

    Your project should now be safe to check into GitHub. You can test that the set environment variables work by running a deployment of your Smart Contracts to Goerli

```
yarn hardhat deploy --network goerli
```

6. Head over to [https://github.com/](https://github.com/) and sign-in, or create a new free account if you don’t have one already. Click on your profile on the top-right corner, and goto Settings -> Developer Settings -> Personal access tokens

![image](https://user-images.githubusercontent.com/11134288/202935024-6855db36-a2fb-403e-a6ac-32e92dc83116.png)

7. Generate a personal access token as per the [GitHub instructions](https://www.google.com/url?q=https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token&sa=D&source=editors&ust=1668004461481535&usg=AOvVaw36AfZzL6Me-EVE0Ml8rfR0)

8. Create a new repository on GitHub. Call it ‘dev-bootcamp-hardhat’, and leave the visibility as ‘public’. To avoid errors, do not initialize the new repository with README, license, or gitignore files. Once you get to the ‘setup page’, leave it open, you will come back to it soon.

![image](https://user-images.githubusercontent.com/11134288/202935055-2a071676-3ded-4a5b-8123-f3f56ad9ec95.png)

![image](https://user-images.githubusercontent.com/11134288/202935065-920d90b9-f57a-474f-9f57-315c8c699165.png)

9. Go back to your VS Code terminal for your completed project

10. Initialize the local directory as a Git repository.

```
git init -b main
```

11. Add the files in your new local repository. This stages them for the first commit.

```
git add .
```

12. Next we want to remove the existing remote link to the Hardhat Starter Kit repository on GitHub

```
git remote rm origin
```

13. Commit the files that you've staged in your local repository.

```
git commit -m "Developer Bootcamp".
```

14. Go back to GitHub. At the top of your GitHub repository's Quick Setup page, click the copy button  to copy the remote repository URL.

![image](https://user-images.githubusercontent.com/11134288/202935188-fd1c13fd-10e9-4e64-a853-82d0dccf9808.png)

15. Back in VS code terminal, you need to add the URL for the remote repository where your local repository will be pushed. Enter in the command below, and replace the `<PASTE_REMOTE_URL>` with the value you copied above. If prompted for GitHub authentication details, use your email that you signed up to GitHub with, and your personal access token that you generated earlier as the password. If you don’t get prompted, you can continue.

```
git remote add origin  <PASTE_REMOTE_URL>
```

16. Verify the new remote URL with the following command. You should see it now pointing to your GitHub repository. This means when we push code, we will be pushing it to your GitHub repository.

```
git remote -v
```

![image](https://user-images.githubusercontent.com/11134288/202935272-091da45c-e0f8-4171-8072-331176a26028.png)

17. Push the changes in your local repository up to GitHub. If prompted for GitHub authentication details, use your email that you signed up to GitHub with, and your personal access token that you generated earlier as the password. This will give your local git program access to push code up to your GitHub account.

```
git push -u origin main
```

Your repository should now be live on GitHub! If you still have GitHub open with your new repository, then you can just refresh the page. Otherwise, head to [GitHub](https://www.google.com/url?q=https://github.com/&sa=D&source=editors&ust=1668004461489946&usg=AOvVaw3sYFXfUei8V1iflJ5W_wpG), then in the top right corner open the menu and choose ‘your repositories’, then click on the URL link to your project to open it up and see. Take note of the URL and share it in the Bootcamp chat to share your completed project with everyone!

![image](https://user-images.githubusercontent.com/11134288/202935305-ee7637cf-9cb0-47a7-bcfa-407e6c779e93.png)

If you’ve made it this far, congratulations, you’ve completed the ETHDenver 2022 Smart Contract Developer Bootcamp!

![image](https://user-images.githubusercontent.com/11134288/202935321-32a9fac1-57f5-4d20-b87c-376671c273b2.png)

---

## Appendix: Troubleshooting

**Deploying compiled contracts**

If you get an error similar to the following for one of your environment variables:

```
* Invalid value undefined for HardhatConfig.networks.goerli.url - Expected a value of type string.
```

Try manually exporting your GOERLI_RPC_URL variable via the following command in the terminal. Change the value to match what’s in your .env file. You may need to repeat the step for your PRIVATE_KEY environment variable as well

MacOS and Linux commands:

```
export GOERLI_RPC_URL='https://eth-goerli.alchemyapi.io/v2/insert_key_here’
```

```
export PRIVATE_KEY='insert-key-here'
```

Windows commands:

```
set GOERLI_RPC_URL='https://eth-goerli.alchemyapi.io/v2/insert_key_here’
```

```
set PRIVATE_KEY='insert-key-here'
```

Once this is done, you can check to see if the environment variables are set correctly by trying to echo them:

```
echo $GOERLI_RPC_URL
```

```
echo $PRIVATE_KEY
```

![image](https://user-images.githubusercontent.com/11134288/202935907-08fe58fd-b513-49fb-ba66-873cb1aad6d7.png)

If you still can’t get it working, if you’re using windows, try adding the variable to your windows environment variables (in system settings), then try again

**Starting the Local Hardhat Network**

If you get an error similar to the following

```
Error in plugin hardhat-deploy:
Unsupported network for JSON-RPC server. Only hardhat is currently supported.
hardhat-deploy cannot run on the hardhat provider when defaultNetwork is not hardhat
```

Try and start the hardhat node with the following command

```
yarn hardhat node --network hardhat
```

If you get an error similar to the following while attempting to start a Hardhat network that’s a fork of Mainnet

```
Error HH604: Error running JSON-RPC server: Only absolute URLs are supported
```

This means your fork URL is missing some components. Go to your .env file and ensure your variable is set correctly, and that the end hash string in your URL matches the key you obtained from [Alchemy](https://www.google.com/url?q=https://www.alchemyapi.io/&sa=D&source=editors&ust=1668004461503967&usg=AOvVaw2yfwG6e9jWQgjLK6i6Ke6U) when you signed up during the setup instructions

```
ALCHEMY_MAINNET_RPC_URL='https://eth-mainnet.alchemyapi.io/v2/asdfsda8907s89df798sd7foshdfds9f8s7'
```

If you still have issues starting the mainnet fork hardhat node, try running it passing in the value of your ALCHEMY_MAINNET_RPC_URL on the command line. Ie exactly like this, replacing the ‘insert-your-alchemy-key’ string with the key you obtained from Alchemy

```
yarn hardhat node --fork https://eth-mainnet.alchemyapi.io/v2/insert-your-alchemy-key
```

If you are running Windows as none of the above work, try exiting VS Code and restarting it as Administrator (hold SHIFT, right click, Run As Administrator), then try starting the node again

Finally, if you still can’t get the local node to start, try starting it outside of VS Code. i.e. open your terminal (macOS, linux) or Command Prompt (windows, ensure you start it as Administrator), navigate to your ‘hardhat-starter-kit’ directory and try starting the command to start the Hardhat node there. If successful, you can leave it running there and switch back to VS Code and still run the commands to deploy contracts etc as per normal in VS Code.

**Installing Yarn**

If you get an errors installing yarn:

Windows Users:

- Ensure you’re running VS Code as Administrator (hold shift, right click, run as Administrator)
- Try installing it from the Command Prompt instead, ensuring you run the CMD.exe as Administrator
- Try downloading and installing it via the [msi installer](https://www.google.com/url?q=https://classic.yarnpkg.com/latest.msi&sa=D&source=editors&ust=1668004461508126&usg=AOvVaw3cv5qHb5rI_gKafd3DDtM0)

macOS or Linux users

- Try running it with sudo in front of the command

```
sudo npm install -g yarn
```

If you’re still stuck on installing yarn, check out some other possible installation methods on the [Yarn installation page](https://www.google.com/url?q=https://classic.yarnpkg.com/en/docs/install/&sa=D&source=editors&ust=1668004461509994&usg=AOvVaw2iasKVOHyi3h_BZrIh49s6)

---
