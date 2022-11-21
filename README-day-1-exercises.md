<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Day 1 Exercises](#day-1-exercises)
  - [Exercise 1: My First Smart Contract](#exercise-1-my-first-smart-contract)
    - [Bonus Exercise: Increment](#bonus-exercise-increment)
    - [Bonus Exercises: Arrays and Mappings](#bonus-exercises-arrays-and-mappings)
      - [Adding an Array](#adding-an-array)
      - [Adding a Mapping](#adding-a-mapping)
    - [Bonus Exercises: Length And Others](#bonus-exercises-length-and-others)
  - [Exercise 2: Price Feeds](#exercise-2-price-feeds)
    - [Bonus Exercise: Getting The Timestamp](#bonus-exercise-getting-the-timestamp)
  - [Exercise 3: VRF v2](#exercise-3-vrf-v2)
  - [Exercise 4: Any-API](#exercise-4-any-api)
    - [Bonus Exercise: CryptoCompare Price](#bonus-exercise-cryptocompare-price)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Day 1 Exercises

![image](https://user-images.githubusercontent.com/11134288/199536931-f2968f94-3cc4-471b-8d22-5a77d6e12778.png)

---

## Exercise 1: My First Smart Contract

In this exercise, you’ll create a simple smart contract that stores and retrieves a value, then you’ll deploy it to the Goerli testnet and interact with it using Remix.

1. Open [http://remix.ethereum.org/](https://www.google.com/url?q=http://remix.ethereum.org/&sa=D&source=editors&ust=1667406700450732&usg=AOvVaw25hxyDlvaxE6wNyJYngez3)

2. If prompted, create a new default workspace

3. Expand the contracts folder, and press the new file button. Call the file MyFirstContract.sol

![image](https://user-images.githubusercontent.com/11134288/199534490-dc8da918-e1c5-49f5-8af9-0b27d1f8919f.png)

4. Select which version of the compiler we will be using by entering the following line into the new file:

```solidity
pragma solidity ^0.8.7;
```

5. Underneath, enter in the contract source code. **If you get an SPDX Identifier warning, you can continue. This is a warning and not a critical compiler error**:

```solidity
pragma solidity ^0.8.7;

contract MyFirstContract {

   uint256 number;


   function changeNumber(uint256 _num) public {
       number = _num;
   }


   function getNumber() public view returns (uint256){
       return number;
   }
}
```

6. Your contract is now ready to be compiled. Press on the Solidity Compiler menu option on the left hand side menu, change the compiler version in the compiler dropdown so that it matches the compiler specified in your code, then press on the blue Compile button: If you get an SPDX Identifier warning, you can continue. This is a warning and not a critical compiler error.

![image](https://user-images.githubusercontent.com/11134288/199535477-65430fa5-4a65-4b47-9039-dbe7c6c90ea5.png)

7. Choose the ‘Deploy and Run Transactions’ button on the left hand side menu. Ensure Environment is set to ‘JavaScript VM’, and that the selected contract is ‘MyFirstContract’, then press the Deploy button. You should then see your contract come up under the ‘Deployed Contracts’ section further below

![image](https://user-images.githubusercontent.com/11134288/199535578-509f36e7-4d80-4337-a569-64f049d4c8c3.png)

8. Expand the deployed contract by selecting the > sign next to it. You can now see all of the functions that you can use to interact with the contract.

9. Press the ‘getNumber’ function to read the state of the contract, and return the value of the number variable. Because we haven’t set it yet, it should simply return 0

![image](https://user-images.githubusercontent.com/11134288/199535906-6bcf1715-c2b5-4784-af29-0683a8802a58.png)

10. Enter a value into the ‘changeNumber’ function input parameter, then press the ‘changeNumber’ button to execute the function.

11. Execute the ‘getNumber’ function again. You should now see the contract state has been updated.

![image](https://user-images.githubusercontent.com/11134288/199536052-2a5ec281-7e4c-46e0-a846-090d5784e170.png)

12. Now let's try this again, but instead of working on the local Remix VM network, we’ll deploy our contract to the public Goerli testnet. Change the ‘Environment’ dropdown to ‘Injected Web3’. If you’re not signed into your Metamask wallet, then sign in before continuing, and ensure the selected network is the Goerli Test Network’, and that you have some ETH in your wallet. If you don’t have any ETH, raise your hand for help, and an instructor will help get you some.

![image](https://user-images.githubusercontent.com/11134288/199536185-e2a1f56a-ed1c-4cf6-bf9c-7f521ebd876b.png)

13. Because we already compiled our contract and we haven’t changed it, we don’t need to compile it again. Press the orange Deploy button to deploy your already compiled contract. Metamask will popup asking you to confirm the transaction. Press the blue ‘Confirm’ button to execute the transaction, and deploy your contract to the Goerli network. After a few seconds, you should see your deployed contract in the ‘Deployed Contracts’ section.

14. Press the ‘copy’ contract address button to copy the contracts address to your clipboard, then head to [https://goerli.etherscan.io/](https://www.google.com/url?q=https://goerli.etherscan.io/&sa=D&source=editors&ust=1667406700458631&usg=AOvVaw090hnv7XxlGLqDp9P7hB63), here is where you can find your deployed contract on the Goerli network, and any associated transactions with it. Paste your contract address in the search field, and then press search. You should find your deployed contract, with 1 transaction (contract creation).

![image](https://user-images.githubusercontent.com/11134288/199536337-b2c51988-db7b-49ff-840f-9dbad64c21e5.png)

![image](https://user-images.githubusercontent.com/11134288/199536366-681ce5b5-a993-4fd2-8ec9-6f20a2c26c2c.png)

15. Once again, execute the ‘getNumber’ function and verify that the result returned is 0. Then enter a number into the ‘changeNumber’ function parameter, and execute the ‘changeNumber’ function to update the contract state. Once again, Metamask will pop up and ask you to confirm the transaction.

![image](https://user-images.githubusercontent.com/11134288/199536472-41fbeb07-db7a-4120-a19d-258f1b09d224.png)

18. Give the transaction a few seconds to be included in a block, then once again execute the ‘getNumber’ function. You should now see the contract state has been updated

![image](https://user-images.githubusercontent.com/11134288/199536545-2038c6fa-0b9b-422c-8ff8-de94ff0575f0.png)

19. If you go back to Etherscan and refresh the page with your contract, you should see your new transaction listed. If you press on the ‘Txn Hash’ link, you will see the details of the transaction.

![image](https://user-images.githubusercontent.com/11134288/199536586-0e1cca4f-041b-42dc-84ea-da6940acee1c.png)

![image](https://user-images.githubusercontent.com/11134288/199536615-46596dba-98b8-4401-ab7f-2b16e360f1fe.png)

Congratulations, you’ve successfully written your first smart contract that reads and writes to the blockchain, and deployed it to a live network!

---

### Bonus Exercise: Increment

You can attempt to complete these exercises if you’ve completed the main exercise ahead of schedule:

1. Modify your smart contract so that instead of storing the passed in number, it increments the currently stored number by the passed in _num param. To do this, you should initially set the state of the number variable to be 0

```
uint256 number = 0;
```

2. You can increment the stored number variable with the following syntax

```
number = number + _num;
```

2. Create a new function called ‘getNumberMultiplied’, that takes in a parameter called _num, and then returns an integer of the result of multiplying the _num parameter with the currently stored number parameter. The function should be defined as a view function similar to the getNumber() function, because we are not modifying the state of the contract.

3. Create a new function called ‘addNumbers’ that takes in two uint parameters, _num1 and _num2, and then stores the result of adding the two numbers into the number variable.

---

### Bonus Exercises: Arrays and Mappings

In this exercise, we’re going to modify our MyFirstSmartContract smart contract and we’re going to add an array and a Mapping to it! If you have extra time after completing exercise 1 feel free to complete these as well!

#### Adding an Array

For this part of the exercise, you’ll create a dynamic array of names in your smart contract, stored as strings.

1. Open [Remix](https://www.google.com/url?q=http://remix.ethereum.org/&sa=D&source=editors&ust=1667406700464817&usg=AOvVaw2q5FK3QY8VPG43BnKI-OL-), you should be able to find your completed smart contract from the last session in your explorer

2. Next you need to add the new array to your smart contract. Create a new dynamic array of strings called ‘names’. You can add it under the existing ‘number’ variable.

3. Add a function to ‘push’ new values to the array. It should take in a parameter called _name

```solidity
function addName(string memory _name) public {
       names.push(_name);   
}
```

4. Add another function to get a name stored in the array, given an index parameter passed in. It should return the name in the array at the given index. Because you are reading the contract state, this can be a view function.

```solidity
function getName(uint _index) public view returns (string memory) {
       return names[_index];   
}
```

5. Your completed code should now look like this

```solidity
pragma solidity ^0.8.7;

contract MyFirstContract {

   uint256 number = 0;

   //Dynamic array (variable size)
   string[] names;

   function addName(string memory _name) public {
       names.push(_name);
   }

   function getName(uint _index) public view returns (string memory) {
       return names[_index];
   }

   function changeNumber(uint256 _num) public {
       number = _num;
   }


   function getNumber() public view returns (uint256){
       return number;
   }
}
```

6. You’re now ready to test your contract! Compile and re-deploy it. You can ignore any compile time warnings (text in orange). For this exercise, we’ll work in the local browser based EVM environment, so choose a ‘JavaScript VM’ environment:

![image](https://user-images.githubusercontent.com/11134288/199544063-d30b6f12-e0be-4290-8731-1ef12ecde8af.png)

![image](https://user-images.githubusercontent.com/11134288/199544081-38335474-eca5-4e54-b66d-938583a4170b.png)

7. Once deployed, pass in a parameter to the ‘addName’ function, and execute it to add a name to the names array in the smart contract

![image](https://user-images.githubusercontent.com/11134288/199544127-377e6f1e-ecee-4df4-9301-db1e62885141.png)

8. Add in another name of your choice to append it to the names array

![image](https://user-images.githubusercontent.com/11134288/199544183-dedaabac-cdcd-4599-9643-315c08583a5e.png)

9. Now call the ‘getName’ function, passing in an index of 0 to see the first value stored in the array. Repeat the step after this, passing in an index of 1 to see the second value.

![image](https://user-images.githubusercontent.com/11134288/199544231-8b4d05cd-3c34-47ee-8611-06a0d5182415.png)

![image](https://user-images.githubusercontent.com/11134288/199544248-875bbd24-8e97-4261-8733-1568fa24d5e9.png)

Congratulations, you’ve successfully created a dynamic array in your smart contract, and populated it with data.

#### Adding a Mapping

For this part of the exercise, you’ll create a mapping of names->mobile numbers in your smart contract

1. First you need to add the new mapping to your smart contract. Create a new mapping of names to integers (phone numbers) as follows:

```
mapping (string => uint) public phoneNumbers;
```

2. Create a function to add values to the mapping. It should take in two parameters, called _name and _mobileNumber

```solidity
function addMobileNumber(string memory _name, uint _mobileNumber) public {
    phoneNumbers[_name] = _mobileNumber;
}
```

3. Add another function to get a phone number from the mapping for a given name. It should take a _name parameter, and return a uint

```solidity
function getMobileNumber(string memory _name) public view returns (uint) {
    return phoneNumbers[_name];
}
```

4. Your completed code should now look like this

```solidity
pragma solidity ^0.8.7;

contract MyFirstContract {

   uint256 number = 0;

   //Dynamic array (variable size)
   string[] names;
   mapping (string => uint) public phoneNumbers;


   function addMobileNumber(string memory _name, uint _mobileNumber) public {
       phoneNumbers[_name] = _mobileNumber;
   }

   function getMobileNumber(string memory _name) public view returns (uint) {
       return phoneNumbers[_name];
   }

   function addName(string memory _name) public {
       names.push(_name);
   }

   function getName(uint _index) public view returns (string memory) {
       return names[_index];
   }


   function changeNumber(uint256 _num) public {
       number = _num;
   }


   function getNumber() public view returns (uint256){
       return number;
   }
}
```

10. You’re now ready to test your contract! Compile and re-deploy it. You can ignore any compile time warnings (text in orange). For this exercise, once again we’ll work in the local browser based EVM environment, so choose a ‘JavaScript VM’ environment:

![image](https://user-images.githubusercontent.com/11134288/199545701-1a03f108-0880-4327-9be3-3489e8aefa39.png)

![image](https://user-images.githubusercontent.com/11134288/199545746-ee1a7299-fae6-4e29-bbe4-9bf31a160089.png)

11. Once deployed, expand the ‘addMobileNumber’ dropdown button, so you can see both parameters. Enter in some values and execute the function

![image](https://user-images.githubusercontent.com/11134288/199545783-be665261-60a6-4314-ae61-4aadd6ed3af0.png)

![image](https://user-images.githubusercontent.com/11134288/199545800-160adbcf-5cca-4537-8a66-88b519c26d4b.png)

12. Add in another name and number of your choice, and add it to the mapping

![image](https://user-images.githubusercontent.com/11134288/199545838-50214cc5-9ea0-45f7-b39d-a4283e8138bf.png)

13. Now call the ‘getMobileNumber’ function, passing in one of the names entered into the mapping in the previous steps. You should see it return the stored number against the name. Repeat the step for the other name entered

![image](https://user-images.githubusercontent.com/11134288/199545872-79394b73-81e0-48d4-8b75-1a379c73d7ef.png)

![image](https://user-images.githubusercontent.com/11134288/199545897-f76a9ef0-2163-4170-89eb-b18a769c12a7.png)

Congratulations, you’ve successfully created a mapping in your smart contract, and populated and interacted with it!

---

### Bonus Exercises: Length And Others

You can attempt to complete these exercises if you’ve completed the main exercise ahead of schedule:

1. Create a function in your smart contract that returns the length of the names array, call it getNamesLength(). The return type should be uint, and the way to get the length of an array is with the following syntax

```
return names.length;
```

2. Create a function in your smart contract that returns the entire names array as a string. You’ll need to add the ABIEncoderV2 pragma statement for this at the top of your contract file under your import. ie:

```
pragma solidity ^0.8.7;
```

Call the function getNames. It should be a view function, with a return type of the following:

```
returns (string[] memory)
```

3. Create a new smart contract in Remix (in a new file) called ‘ERC-20.sol’. Paste in the complete code example of a basic ERC-20 contract from the Ethereum developer tutorials page. Modify the name and symbol parameters in the constructor of the ERC20Basic contract, choose any values you wish

4. Deploy the ERC20Basic contract to your local JavaScript VM network. You need to specify the total number of tokens in the contract when you deploy. In this example, we’ve chosen 100 million. Make sure you have the right contract selected to deploy.

![image](https://user-images.githubusercontent.com/11134288/199546666-b2804b7a-d775-4596-a089-dbceaeca5eb5.png)

5. Once deployed, copy your currently selected account in Remix by pressing the copy button next to the value

![image](https://user-images.githubusercontent.com/11134288/199546712-66e30edd-125b-460c-82cc-1d048a95b7e8.png)

6. Call the transfer function in your deployed contract to mint yourself some tokens, passing in your copied wallet address, and a value for the token amount. Then call the ‘balanceOf’ function, once again passing in your copied wallet address, to see your balance

![image](https://user-images.githubusercontent.com/11134288/199546760-ca7809b2-1d00-44ca-824d-f950df87d7f8.png)

![image](https://user-images.githubusercontent.com/11134288/199546788-139a9d62-18b9-4abd-84d1-84262587d05d.png)

7. Continue to play with the token contract and see how the other functions like ‘transferFrom’ etc works. You can switch your currently active wallet address around using the ‘Account’ dropdown in Remix, so you can send token amounts between your wallet accounts

![image](https://user-images.githubusercontent.com/11134288/199546847-3fa81b33-5d32-4098-8514-2aab4942fc5b.png)

Congratulations, you’ve built, deployed and interacted with a token contract.

---

## Exercise 2: Price Feeds

In this exercise, you're going to create a simple smart contract that looks up the current price of Ethereum using Chainlink Price Feeds. Firstly, open http://remix.ethereum.org/

1. Expand the contracts folder, and press the new file button. Call the file PriceConsumer.sol

![image](https://user-images.githubusercontent.com/11134288/199547817-73bad65a-73c0-4313-b494-9b1605c8c31b.png)

2. Select which version of the compiler we will be using by entering the following line into the new file:

```
pragma solidity ^0.8.7;
```

3. Underneath, enter in the contract source code. In our first example we will be using the ETH/USD price feed contract 0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e, which we’ve taken from the Goerli section of the [Ethereum Price Feeds](https://www.google.com/url?q=https://docs.chain.link/docs/ethereum-addresses/&sa=D&source=editors&ust=1667406700486641&usg=AOvVaw3lHfKsAWHWFoUWGTWfKt-R) page of the Chainlink documentation

```solidity
import "@chainlink/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol";

contract PriceConsumerV3 {

   AggregatorV3Interface internal priceFeed;

   /**
    * Network: Goerli
    * Aggregator: ETH/USD
    * Address: 0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e
    */
   constructor() public {
       priceFeed = AggregatorV3Interface(0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e);
   }

   /**
    * Returns the latest price
    */
   function getLatestPrice() public view returns (int) {
       (
           uint80 roundID,
           int price,
           uint startedAt,
           uint timeStamp,
           uint80 answeredInRound
       ) = priceFeed.latestRoundData();
       return price;
   }
}
```

4. Your contract is now ready to be compiled. Press on the Solidity Compiler menu option on the left hand side menu, change the compiler version in the compiler dropdown so that it matches the compiler specified in your code, then press on the blue Compile button:

![image](https://user-images.githubusercontent.com/11134288/199548420-ed3c4d0e-2069-45b5-86ab-f18e7b74721a.png)

5. Choose the ‘Deploy and Run Transactions’ button on the left hand side menu. Because you're going to integrate to the Chainlink Oracle network, we need to connect to the Goerli public testnet. Ensure Environment is set to ‘Injected Web3’, and that the selected contract is ‘PriceConsumer.sol’, then press the Deploy button. Metamask will popup asking you to confirm the transaction. Press the blue ‘Confirm’ button to execute the transaction, and deploy your contract to the Goerli network. After a few seconds, you should see your deployed contract in the ‘Deployed Contracts’ section in Remix.

![image](https://user-images.githubusercontent.com/11134288/199548444-6f3c2905-e675-4a77-8aac-deefd7f5a291.png)

6. Expand the deployed contract by pressing on the “>” icon next to the contract name in the Deployed Contracts section. You should see the available functions that can be executed. Press on the ‘getLatestPrice’ button to lookup the price of ETH from the Goerli ETH/USD price feed.

![image](https://user-images.githubusercontent.com/11134288/199548494-4b0c8e86-383b-4be8-82a1-ad7823b2383e.png)

7. The returned result is the current market price of ETH, multiplied by 10^8. You can compare it to the Mainnet ETH/USD Price Feed by going to [https://data.chain.link/eth-usd](https://www.google.com/url?q=https://data.chain.link/eth-usd&sa=D&source=editors&ust=1667406700490090&usg=AOvVaw2-42x5xE0bptOA-My7byMc) and looking at the current price.

8. Go to the Ethereum Price Feeds page in the Chainlink documentation, and navigate down to the [‘Goerli Testnet’ section](https://www.google.com/url?q=https://docs.chain.link/docs/ethereum-addresses/%23Rinkeby%2520Testnet&sa=D&source=editors&ust=1667406700490448&usg=AOvVaw0xhdu-kmJpQadbs9adLtdy). Pick another pair, and copy the Proxy address. In our example, we’ve chosen the LINK/USD pair
[0x48731cF7e84dc94C5f84577882c14Be11a5B7456](https://www.google.com/url?q=https://goerli.etherscan.io/address/0x48731cF7e84dc94C5f84577882c14Be11a5B7456&sa=D&source=editors&ust=1667406700490739&usg=AOvVaw2o6kTOQ9s4Tl_bFltLu9j1)

9. Go back to your contract, and in the constructor, replace the address of the ETH/USD price feed address, with the one that you copied in the previous step.

```
priceFeed =
AggregatorV3Interface(0x48731cF7e84dc94C5f84577882c14Be11a5B7456);
```

10. Go back to the Solidity Compiler tab on Remix, and press the blue ‘Compile PriceConsumer.sol’ button to re-compile your contract.

11. Go to the ‘Deploy & Run Transactions’ tab and re-deploy your contract, accepting the transaction in Metamask. Once deployed, you should see a second deployed contract under the ‘Deployed Contracts’ section.

![image](https://user-images.githubusercontent.com/11134288/199548778-76eca89f-a2cc-42b9-b8b7-6b1a74636b40.png)

12. Expand the deployed contract once again, and execute the ‘getLatestPrice’ function. You should see the returned current price in the price feed contract that you selected.

![image](https://user-images.githubusercontent.com/11134288/199548811-81dc9267-e39d-40e9-b30e-c7124d402e6f.png)

13. Head to [https://data.chain.link/](https://www.google.com/url?q=https://data.chain.link/&sa=D&source=editors&ust=1667406700492521&usg=AOvVaw3uuXcXxJBl0QUReWoCvPgQ) and look for the equivalent price feed running on Mainnet.

![image](https://user-images.githubusercontent.com/11134288/199548848-f153b7fa-6895-4c94-96c3-763bfedae3ad.png)

Congratulations, you’ve successfully written and deployed a contract that uses Chainlink Price Feeds to obtain external price data!

---

### Bonus Exercise: Getting The Timestamp

You can attempt to complete these exercises if you’ve completed the main exercise ahead of schedule

1. Modify the Price Feed contract to get a different price feed that you pick from the Goerli Price Feed addresses in the [Chainlink Documentation](https://www.google.com/url?q=https://docs.chain.link/docs/reference-contracts/&sa=D&source=editors&ust=1667406700493415&usg=AOvVaw35l49yLg7xOynSAdsVSfH1). Then deploy and test your contract. Compare the value to the mainnet feed value at [https://data.chain.link](https://www.google.com/url?q=https://data.chain.link/&sa=D&source=editors&ust=1667406700493611&usg=AOvVaw2eJ8o_VAGGBqTHgXs5Ce45)

2. Create a new function called ‘getTimestamp’ that returns a uint which is the timeStamp of the current round (hint: it can be accessed via the priceFeed.latestRoundData() call)

---

## Exercise 3: VRF v2

In this exercise, you're going to create a simple smart contract that performs a request for randomness using Chainlink VRF.

This exercise is detailed in the tutorial [get a random number](https://www.google.com/url?q=https://docs.chain.link/docs/get-a-random-number/&sa=D&source=editors&ust=1667406700494495&usg=AOvVaw2vyCBZsF-0O3t45wuno7U0)

---

## Exercise 4: Any-API

In this exercise, you're going to create a simple smart contract that performs a request for external data, using Chainlink Any-API. Firstly, open [http://remix.ethereum.org/](https://www.google.com/url?q=http://remix.ethereum.org/&sa=D&source=editors&ust=1667406700494853&usg=AOvVaw0iNXZgtriBghb0jBFdwW4f). This exercise uses the Goerli network, so make sure you have Goerli ETH and LINK in you

1. Expand the contracts folder, and press the new file button. Call the file APIConsumer.sol

![image](https://user-images.githubusercontent.com/11134288/199549891-e90fdace-ce87-47bf-a66d-d7a6eae7f87f.png)

2. Select which version of the compiler we will be using by entering the following line into the new file:

```
pragma solidity ^0.8.7;
```

3. Go to the following URL in your browser, to see the json output of the API we will be accessing. Search for the term “VOLUME24HOUR” to see the exact value we will be looking to get into our smart contract

```
https://min-api.cryptocompare.com/data/pricemultifull?fsyms=ETH&tsyms=USD
```

4. Back in Remix, underneath your pragma command, enter in the contract source code.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;
import "@chainlink/contracts/src/v0.8/ChainlinkClient.sol";
/**
 * Request testnet LINK and ETH here: https://faucets.chain.link/
 * Find information on LINK Token Contracts and get the latest ETH and LINK faucets here: https://docs.chain.link/docs/link-token-contracts/
 */
/**
 * THIS IS AN EXAMPLE CONTRACT WHICH USES HARDCODED VALUES FOR CLARITY.
 * PLEASE DO NOT USE THIS CODE IN PRODUCTION.
 */
contract APIConsumer is ChainlinkClient {
    using Chainlink for Chainlink.Request;

    uint256 public volume;

    address private oracle;
    bytes32 private jobId;
    uint256 private fee;

    /**
     * Network: Goerli
     * Oracle: 0xc57B33452b4F7BB189bB5AfaE9cc4aBa1f7a4FD8 (Chainlink Devrel)
     * Node)
     * Job ID: d5270d1c311941d0b08bead21fea7747
     * Fee: 0.1 LINK
     */
    constructor() {
        setPublicChainlinkToken();
        oracle = 0xc57B33452b4F7BB189bB5AfaE9cc4aBa1f7a4FD8;
        jobId = "d5270d1c311941d0b08bead21fea7747";
        fee = 0.1 * 10 ** 18; // (Varies by network and job)
    }

    /**
     * Create a Chainlink request to retrieve API response, find the target
     * data, then multiply by 1000000000000000000 (to remove decimal places from data).
     */
    function requestVolumeData() public returns (bytes32 requestId)
    {
        Chainlink.Request memory request = buildChainlinkRequest(jobId, address(this), this.fulfill.selector);

        // Set the URL to perform the GET request on
        request.add("get", "https://min-api.cryptocompare.com/data/pricemultifull?fsyms=ETH&tsyms=USD");

        // Set the path to find the desired data in the API response, where the response format is:
        // {"RAW":
        //   {"ETH":
        //    {"USD":
        //     {
        //      "VOLUME24HOUR": xxx.xxx,
        //     }
        //    }
        //   }
        //  }
        request.add("path", "RAW.ETH.USD.VOLUME24HOUR");

        // Multiply the result by 1000000000000000000 to remove decimals
        int timesAmount = 10**18;
        request.addInt("times", timesAmount);

        // Sends the request
        return sendChainlinkRequestTo(oracle, request, fee);
    }

    /**
     * Receive the response in the form of uint256
     */
    function fulfill(bytes32 _requestId, uint256 _volume) public recordChainlinkFulfillment(_requestId)
    {
        volume = _volume;
    }
    // function withdrawLink() external {} - Implement a withdraw function to avoid locking your LINK in the contract
}
```

5. Your contract is now ready to be compiled. Press on the Solidity Compiler menu option on the left hand side menu, change the compiler version in the compiler dropdown so that it matches the compiler specified in your code, then press on the blue Compile button:

![image](https://user-images.githubusercontent.com/11134288/199550705-7bfe5d98-f098-41ce-8904-679406d5da0f.png)

6. Choose the ‘Deploy and Run Transactions’ button on the left hand side menu. Because you're going to integrate to the Chainlink Oracle network, we need to connect to the Goerli public testnet. Ensure Environment is set to ‘Injected Web3’, and that the selected contract is APIConsumer.sol’, then press the Deploy button. Metamask will popup asking you to confirm the transaction. Press the blue ‘Confirm’ button to execute the transaction, and deploy your contract to the Goerli network. After a few seconds, you should see your deployed contract in the ‘Deployed Contracts’ section in Remix.

![image](https://user-images.githubusercontent.com/11134288/199550735-222669bd-2ac5-4d01-97fe-4976424d3f18.png)

7. [Fund your contract with 1 link](https://www.google.com/url?q=https://docs.chain.link/docs/fund-your-contract/&sa=D&source=editors&ust=1667406700510412&usg=AOvVaw0Syyp_kifEvXJNNTwFQCzE) token. If you don’t have the LINK token added to your MetaMask wallet yet, press the ‘Add Token’ button at the bottom, then enter in the LINK token contract address 0xa36085F69e2889c224210F603D836748e7dC0088, then press save.

8. Once your contract has been funded with LINK, you can now initiate the external data request. Expand the deployed contract by pressing on the “>” icon next to the contract name in the Deployed Contracts section. You should see the available functions that can be executed. Press on the ‘requestVolumeData’ button, then confirm the transaction when MetaMask pops up.

![image](https://user-images.githubusercontent.com/11134288/199550808-4ac0f1ce-a003-4cd6-9c23-2249dd506011.png)

9. After a few seconds, your transaction should be approved. While you wait for the chainlink node to fulfill the request, goto [https://goerli.etherscan.io/](https://www.google.com/url?q=https://goerli.etherscan.io/&sa=D&source=editors&ust=1667406700511176&usg=AOvVaw1ih5SuebYJ3JY-eFZSZe45) and search for your deployed contract address (you copied it to the clipboard when you funded your contract with LINK). Once you find your deployed contract on Etherscan, go-to the ‘ERC-20 Token Txns’ tab. You should see 2 transactions, one incoming transfer of 1 LINK from when you funded your contract, and 0.1 LINK transferred out of the contract for your external data request.

![image](https://user-images.githubusercontent.com/11134288/199550851-583ff04d-53eb-44af-bdad-f7e885d9cb16.png)

10. Go back to your deployed contract in Remix. We will now check to see the returned result from the external data request. Press the ‘volume’ button to execute the function that returns the value of the public ‘volume’ variable. You should now have a result that matches the value that you saw in your web browser in step 19 above. The value has been purposely multiplied by 10**18 to avoid any issues with math operations etc that may be done on the result.

![image](https://user-images.githubusercontent.com/11134288/199550946-994fd3ca-0054-4bb9-a80d-089386245eb5.png)

Congratulations, you’ve successfully performed a request for external data, and pulled in data from a public API into your smart contract!

---

### Bonus Exercise: CryptoCompare Price

You can attempt to complete these exercises if you’ve completed the main exercise ahead of schedule


1. Modify your contract to get the price data from the Cryptocompare API instead of the volume. Rename all variables that mention volume to reflect the change in the data being brought in

2. Change the API being accessed to the following, to get the BTC/USD price. [https://api.cryptowat.ch/markets/kraken/btcusd/price](https://www.google.com/url?q=https://api.cryptowat.ch/markets/kraken/btcusd/price&sa=D&source=editors&ust=1667406700512401&usg=AOvVaw2Xc54_tn7ynDqJs4r9eIsv). You’ll need to modify the ‘path’ parameter sent in the request as well to match the JSON path of the ‘price’ field if you paste the URL above into a browser window

---
