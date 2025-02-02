# Integrating Celo with a mobile application using the Celo Wallet SDK:

## Table of Content:
- [Integrating Celo with a mobile application using the Celo Wallet SDK](#integrating-celo-with-a-mobile-application-using-the-celo-wallet-sdk)
- [Introduction](#introduction)
- [Requirements](#requirements)
- [What is Celo?](#what-is-celo)
- [What is Celo SDK?](#what-is-celo-sdk)
- [Part 1: Setting up the Celo Wallet SDK](#part-1-setting-up-the-celo-wallet-sdk)
- [Step 1: Install the Celo Wallet SDK](#step-1-install-the-celo-wallet-sdk)
- [Step 2: Connect to the Celo Network](#step-2-connect-to-the-celo-network)
-[Step 3: Authenticate the User](#step-3-authenticate-the-user)
- [Part 2: Interacting with the Celo Network](#part-2-interacting-with-the-celo-network)
- [Sending Transactions](#sending-transactions)
- [Checking Account Balances](#checking-account-balances)
- [Reading Smart Contract Data](#reading-smart-contract-data)
- [Part 3: Implementing Celo Functionality in Your Mobile Application](#part-3-implementing-celo-functionality-in-your-mobile-application)
- [Step 1: Integrate the Celo Wallet SDK into Your Mobile Application](#step-1-integrate-the-celo-wallet-sdk-into-your-mobile-application)
- [Step 2: Add Authentication Functionality](#step-2-add-authentication-functionality)
- [Step 3: Add Transaction Sending Functionality](#step-3-add-transaction-sending-functionality)
- [Step 4: Add Account Balance Checking Functionality](#step-4-add-account-balance-checking-functionality)
- [Step 5: Add Smart Contract Interaction Functionality](#step-5-add-smart-contract-interaction-functionality)
- [Conclusion](#conclusion)


## Introduction:

In this article, you will learn about the following concepts:
- The Celo blockchain.
- The [Celo wallet](https://celowallet.app/setup)
- How to create & integrate Celo to a conntract using the Celo Wallet SDK?

## Requirements:
Here are some of the basic system requirements that you have to integrate Celo with a mobile application using the Celo Wallet SDK:

- A compatible development machine: The Celo Wallet SDK is compatible with both Windows, macOS, and Linux-based machines.
- Celo Wallet SDK: You will need to download and install the Celo Wallet SDK on your machine.
- Development environment: You will need a development environment set up on your machine.

Alright, so let's get started.


## What is CELO?-

**Celo** is a decentralized, open-source blockchain network that aims to provide people with accessible and secure financial tools. As it is based on the Ethereum Virtual Machine (EVM) and is compatible with the Ethereum network, developers can use the same smart contract code on both Celo and Ethereum.

Primary goal of Celo blockchain is to create a more inclusive financial system by making financial services available to anyone with a smartphone. The platform's goal is to lower the barriers of entry for individuals and small businesses seeking financial services such as remittances, microlending, and savings while maintaining the highest level of security and transparency.

Celo's approach to inclusivity includes various design elements that sets it apart from other blockchain networks. For ex, it uses an unique phone-based identity system to help individuals without traditional forms of identification to access financial services. It also employs a stablecoin, the Celo Dollar (cUSD), to provide a stable store of value and facilitate low-cost transactions across the platform.

Celo employs a **proof-of-stake** consensus mechanism, allowing users to participate in block validation by securing their cUSD or Celo Gold (cGLD) tokens as collateral. This mechanism ensures that validators have a vested interest in the network's success and that transactions can be processed efficiently and securely.

Overall, the Celo blockchain is intended to provide people with accessible, secure, and transparent financial services. Its use of mobile-first development, a stablecoin, and a unique identity system all help it to achieve its goal of creating a more inclusive financial system. Its compatibility with the Ethereum network, use of proof-of-stake consensus, and emphasis on security and transparency make it an appealing option for both developers and users.


## What is Celo SDK?-

The **Celo SDK** (Software Development Kit) is a collection of developer tools designed to assist developers in creating and integrating financial applications on the Celo blockchain. The SDK includes a comprehensive set of tools and resources that enable developers to build decentralized applications (dApps) that interact with the Celo blockchain and give users access to various financial services. The Celo SDK is intended to make it simple for developers to create and deploy smart contracts on the Celo blockchain. The SDK comes with a collection of pre-built contracts that can be used as templates or customized to fit specific use cases. Stablecoins, lending protocols, and decentralized exchanges can all be created using these contracts.

The SDK also includes a set of development tools that make it simple for developers to write, test, and deploy smart contracts. These tools include a command-line interface (CLI) for interacting with the Celo blockchain, a testing framework for testing smart contracts, and an integrated development environment (IDE) for writing and debugging smart contracts.

In addition to smart contract development tools, the Celo SDK includes a set of APIs that developers can use to integrate their applications with the Celo blockchain. These APIs enable developers to access blockchain data such as transaction history and account balances, as well as interact with smart contracts on the blockchain.

The Celo SDK's emphasis on mobile-first development is one of its distinguishing features. Developers can use the SDK's mobile wallet to integrate financial services directly into their mobile applications. This enables developers to create dApps that are accessible to anyone with a smartphone, increasing the accessibility of financial services to people all over the world.

The Celo SDK also includes a collection of tools and resources to assist developers in developing and deploying decentralized applications on the Celo network. Documentation, sample code, and a developer community where developers can share knowledge and collaborate on projects are among the resources available.

Overall, the **Celo SDK** is a powerful set of tools that gives developers everything they need to build and deploy financial applications on the Celo blockchain. Its emphasis on mobile-first development, comprehensive set of development tools and resources, and pre-built smart contracts make it an excellent choice for developers looking to create decentralized financial applications on the Celo network.

Now that you've learned what **Celo** and **Celo SDK** is all about here's a tutorial on how to integrate the Celo with a mobile application using the **Celo Wallet SDK**

# Part 1: Setting up the Celo Wallet SDK-
  
  The Celo Wallet SDK is a set of tools for easily integrating the Celo blockchain to your mobile application. In this section, we'll go over how to install the Celo Wallet SDK and connect it to your mobile application.

### Step 1: Install the Celo Wallet SDK-

Installing the **Celo Wallet SDK** is the first step in integrating Celo with your mobile application. The SDK is available on NPM as a package that can be installed with the following command:

`npm install @celo/walletkit`

### Step 2: Connect to the Celo Network-

Once you've installed the Celo Wallet SDK, you'll need to connect to the Celo network. This can be done using the following code:

``` javascript
import { CeloWallet } from '@celo/walletkit'; // Import CeloWallet from '@celo/walletkit' library

const celoWallet = new CeloWallet(provider); // Create a new instance of CeloWallet with a provider argument

celoWallet.connect(); // Call the connect() method to connect to the blockchain network
```
This code creates a new CeloWallet instance and connects it to the Celo network.

### Step 3: Authenticate the User-

The user will need to authenticate their identity using the Celo Wallet SDK before they can interact with the Celo network via your mobile application. This can be accomplished with the following code:

```javascript
const auth = await celoWallet.authenticate(); // Call the authenticate() method on the celoWallet instance and await the result

console.log(auth); // Output the result of the authentication to the console

```
This code opens the Celo Wallet app and prompts the user to authenticate their identity. Once the user has authenticated, the code logs an authentication object to the console.

# Part 2: Interacting with the Celo Network-

After you've installed the Celo Wallet SDK and authenticated the user, you can begin interacting with the Celo network via your mobile application. In this section, we'll go over some examples of how to use the Celo Wallet SDK to send transactions, check account balances, and more.

### Sending Transactions:

To send a transaction on the Celo network, you can use the following code:

```javascript
const recipientAddress = '<recipient address>';
const amountToSend = 1; // cGLD

const txObject = {
  from: celoWallet.address, // Specify the sender's address as the 'from' field
  to: recipientAddress, // Specify the recipient's address as the 'to' field
  value: Web3.utils.toWei(amountToSend.toString(), 'ether'), // Convert the amount to send to wei using the web3 object's toWei() method
};

const txHash = await celoWallet.sendTransaction(txObject); // Send the transaction using the celoWallet's sendTransaction() method and await the transaction hash
console.log(txHash); // Output the transaction hash to the console

```
This code sends 1 (one) cGLD to the specified recipient address while also logging the transaction hash to the console.

### Checking Account Balances:

To check the balance of your Celo account, you can use the following code:

```javascript
const balance = await celoWallet.getBalance(); // Call the getBalance() method on the celoWallet instance and await the balance result

console.log(balance); // Output the balance to the console

```
This code retrieves your Celo account balance and logs it to the console.

### Reading Smart Contract Data:

To read data from a Celo network smart contract, use the following code:

```javascript
import { ContractKit } from '@celo/contractkit'; // Import the ContractKit from the '@celo/contractkit' library

const kit = ContractKit.newKit('https://alfajores-forno.celo-testnet.org'); // Create a new ContractKit instance with the specified Celo network URL

const contractAddress = '<contract address>'; // Specify the address of the contract to interact with
const contract = new kit.web3.eth.Contract(contractABI, contractAddress); // Create a new Contract instance using the ContractKit's web3 object, contract ABI, and contract address

const result = await contract.methods.<method name>(<arguments>).call(); // Call a contract method using the contract's methods object, providing the method name and any required arguments, and use the call() method to invoke the contract method and get the result

console.log(result); // Output the result of the contract method call to the console
```

This code creates a new instance of the ContractKit class and retrieves data from the specified smart contract using the contract's ABI and address.

# Part 3: Implementing Celo Functionality in Your Mobile Application-

Now that you have understood the fundamentals of the Celo Wallet SDK and how to interact with the Celo network, it's time to begin incorporating Celo functionality into your mobile application.

### Step 1: Integrate the Celo Wallet SDK into Your Mobile Application:

The first step in integrating Celo with your mobile application is to import the Celo Wallet SDK and set up a connection to the Celo network. This can be done using the following code:

```javascript
import { CeloWallet } from '@celo/walletkit'; // Import the CeloWallet class from the '@celo/walletkit' library

const celoWallet = new CeloWallet(); // Create a new instance of the CeloWallet class

celoWallet.connect(); // Call the connect() method on the celoWallet instance to connect to the Celo network

```

This code creates a new instance of the CeloWallet class and connects it to the Celo network.

### Step 2: Add Authentication Functionality-

The user will need to authenticate their identity using the Celo Wallet SDK before they can interact with the Celo network via your mobile application. This can be accomplished with the following code:

```javascript
const auth = await celoWallet.authenticate(); // Call the authenticate() method on the celoWallet instance to authenticate with the Celo network and obtain an authentication object

console.log(auth); // Output the authentication object to the console

```

This code opens the Celo Wallet app and prompts the user to authenticate their identity. Once the user has authenticated, the code logs an authentication object to the console.

### Step 3: Add Transaction Sending Functionality-

You can add a form or button that triggers the following code to allow users to send transactions on the Celo network via your mobile application:

```javascript
const recipientAddress = '<recipient address>'; // Set the recipient's address to send the transaction to
const amountToSend = 1; // Set the amount to send in cGLD (Celo Gold) currency

const txObject = {
  from: celoWallet.address, // Set the 'from' address for the transaction as the address of the celoWallet instance
  to: recipientAddress, // Set the 'to' address for the transaction as the recipient's address
  value: celoWallet.web3.utils.toWei(amountToSend.toString(), 'ether'), // Convert the amount to send from cGLD to wei using the 'toWei()' method from the web3 object available in celoWallet instance
};

const txHash = await celoWallet.sendTransaction(txObject); // Call the sendTransaction() method on the celoWallet instance, passing the txObject as an argument, to send the transaction and obtain a transaction hash

console.log(txHash); // Output the transaction hash to the console

```

This code sends 1 cGLD to the specified recipient address and logs the transaction hash to the console.

### Step 4: Add Account Balance Checking Functionality-

You can add a button or menu item that triggers the following code to allow users to check the balance of their Celo account through your mobile application:

```javascript
const balance = await celoWallet.getBalance(); // Call the getBalance() method on the celoWallet instance to retrieve the balance of the associated Celo address

console.log(balance); // Output the retrieved balance to the console

```

This code retrieves the balance of the user's Celo account and logs it to the console.

### Step 5: Add Smart Contract Interaction Functionality-

To allow the user to interact with a smart contract on the Celo network via your mobile application, include a form or button that executes the following code:

```javascript
import { ContractKit } from '@celo/contractkit'; // Import the ContractKit module from the '@celo/contractkit' library

const kit = ContractKit.newKit('https://alfajores-forno.celo-testnet.org'); // Create a new ContractKit instance with the specified Alfajores testnet URL

const contractAddress = '<contract address>'; // Replace with the actual address of the smart contract being interacted with
const contract = new kit.web3.eth.Contract(contractABI, contractAddress); // Create a new web3.eth.Contract instance for the smart contract, passing the ABI and contract address as arguments

const result = await contract.methods.<method name>(<arguments>).call(); // Call the specified method on the smart contract using the 'methods' property of the contract instance, passing any required arguments

console.log(result); // Output the result of the method call to the console

```

This code creates a new instance of the ContractKit class and retrieves data from the specified smart contract using the contract's ABI and address.

Congratulations!! You have successfully integrated celo to your mobile app using the `Celo SDK`. Now, you can interact with your app perfectly.  

# Conclusion:

Using the **Celo Wallet SDK** to integrate Celo with a mobile application is a simple process that can add powerful functionality to your application. You will be able to set up the **Celo Wallet SDK**, authenticate users, send transactions, check account balances, and interact with smart contracts on the Celo network by following the steps outlined in this tutorial. You'll be well on your way to developing powerful Celo-powered mobile applications with these tools at your disposal.
