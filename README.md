# Solidity Smart Contracts

The task is to build 3 Ethereum-compatible blockchain contracts to distribute profit plans using Solidity smart contracts. The following 3 tools will be used to build the solidity smart contracts: 

| ![Remix](./Images/RemixLogo.png "Remix") | ![MetaMask](./Images/MetaMaskLogo.png "MetaMask")| ![Ganache](./Images/GanacheLogo.png "Ganache") | 
|:---:|:---:|:---:|
| Remix | MetaMask | Ganache|

For this excercise, we will code and test the smart contracts on our local host. Once we've successfully coded and tested our Smart Contracts, we can deploy them to a public and live ETH blockchain Testnet such as Kovan or Ropsten.

There are 3 levels to building smart contracts for profit plan distributions, with each contract increasing in difficulty, complexity and capability. 

# Level One: The Associate Profit Splitter Contract

The **Associate Profit Splitter** will accept Ether into the contract and divide the Ether evenly among the employees. This will allow the Human Resources department to pay employees quickly and efficiently. In this scenario, we will be paying the following employees:
- employee_one or the CEO
- employee_two or the CTO
- employee_three or Bob

## Smart Contract Code in Solidity
![APS .sol file](./Screenshots/AssociateProfitSplitter.png "Associate Profit Splitter")

## Compile the Smart Contract Code in Solidity
Next, we need to compile the code in Solidity to ensure there are no coding issues or errors.

![APS .sol file](./Screenshots/AssociateProfitSplitter_Compile.png "Associate Profit Splitter")

After compiling the code, you can see the green checkmark indicating our code is good. We can now move to the next step to deploy the smart contract. 

## Deploying the Smart Contract Code in Solidity
First, open the Ganache application and choose the workspace you will be using. Be sure you have prefunded ETH accounts in this workspace. Any smart contract deployment will be executed in the blockchain. Although smart contracts are deployed with 0 wei, you will be paying gas (i.e. an ETH Fee) for the deployment. Without ETH prefunded, you cannot deploy the smart contract.

Next, ensure you are logging into Metamask. Ensure that you are connected to the same network as your Ganache workkspace. 

Before deploying your smart contract you will need to enter the ETH wallet addresses for each employee. We will choose 3 addresses from our existing Ganache workspace for testing purposes.

|![Ganache Wallets](./Screenshots/GanacheWalletAddresses.png "Ganache") |![APS .sol file](./Screenshots/AssociateProfitSplitter_PreDeploy_Check.png "Associate Profit Splitter")|
|:---:|:---:|
| Ganache | Remix |

Now we can deploy our smart contract using the "transact" button and then confirming (click the "Confirm" button) the transaction in MetaMask by.

|![APS .sol file](./Screenshots/AssociateProfitSplitter_PreDeploy_Transact.png "Associate Profit Splitter") |![APS .sol file](./Screenshots/AssociateProfitSplitter_DeployConfirmation.png "Associate Profit Splitter")|
|:---:|:---:|
| Remix transact | MetaMask confirmation |

*NOTE: You should see a MetaMask confirmation of the transaction along with the transaction informaton at the bottom of the Remix screen. You can confirm the transaction was also successful via Ganache transaction history.*

|![Ganache Wallets](./Screenshots/Ganache_TransactionHistory.png "Ganache") |![Ganache Wallets](./Screenshots/Ganache_AssociateProfitSplitter_SmartContract.png "Ganache")|
|:---:|:---:|
| Ganache TXN History  | Ganache TXN detail |

Once the contract has been activated, let's test the functionality by transferring 15 and 4 Ether into the employees' accounts. Note that the contract should splt the fractional ETH shares and there should be 1 wei going back to the original wallet address (in this case Human Resources or "HR").

| ![15ETH](./Screenshots/Deposit15ETH.png "15 ETH Deposit") | ![15ETHTXN](./Screenshots/Deposit15ETHtransact.png "15 ETH transact")| ![15ETHconfirm](./Screenshots/Deposit15ETHconfirm.png "15 ETH confirmation") | 
|:---:|:---:|:---:|
| 15 ETH Deposit | 15 ETH Transact| 15 ETH TXN Confirmation|

| ![4ETH](./Screenshots/Deposit4ETH.png "4 ETH Deposit") | ![4ETHTXN](./Screenshots/Deposit4ETHtransact.png "4 ETH transact")| ![4ETHconfirm](./Screenshots/Deposit4ETHconfirm.png "4ETH confirmation") | 
|:---:|:---:|:---:|
| 4 ETH Deposit | 4 ETH Transact | 4 ETH Confirmation|

You'll see that Ganache before and after, shows a total of 19 ETH was taken from the main wallet, i.e. HR, and 6.33 ETH was deposited into each employee's wallets (employee_one, employee_two, and employee_three).

| ![15ETH](./Screenshots/Ganache15ETH.png "15 ETH Deposit") | ![15ETHTXN](./Screenshots/Ganache15ETHTXN.png "15 ETH transact")| ![15ETHconfirm](./Screenshots/Ganache15ETHTXNdetail.png "15 ETH confirmation") | 
|:---:|:---:|:---:|
| 15 ETH Deposit | 15 ETH TXN| 15 ETH TXN Detail|

| ![4ETH](./Screenshots/Ganache4ETH.png "4 ETH Deposit") | ![4ETHTXN](./Screenshots/Ganache4ETHTXN.png "4 ETH transact")| ![4ETHconfirm](./Screenshots/Ganache4ETHTXNdetail.png "4ETH confirmation") | 
|:---:|:---:|:---:|
| 4 ETH Deposit | 4 ETH TXN | 4 ETH TXN Detail|

# Level Two: The Tiered Profit Splitter Smart Contract

The **Tiered Profit Splitter** will distribute different percentages of Ether to employees at different tiers/levels rather than an 1/3 split to each employee. For this example, the CEO will receive 60%, the CTO will receive 25%, and Bob will receive 15%.

|![TPS](./Screenshots/TieredProfitSplitter1.png "Tiered Profit Splitter 1") | ![TPS](./Screenshots/TieredProfitSplitter2.png "Tiered Profit Splitter 2") |
|:---:|:---:|
| Tiered Profit Splitter - Part 1 | Tiered Profit Splitter - Part 2 |

*NOTE: For this coding excercise we are using the += syntax to perform a mathimatical addition function. However, if the wallets have a zero balance, this could cause issues as there is a flaw in Soldity using uint for mathematical operations. As a best practice, for any mathematical functions, it's highly recoomended to use SafeMath when coding in REMIX.*
- import "github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/math/SafeMath.sol";

*This only works in REMIX. Alternatively, you can paste the contents of SafeMath.sol from GitHub into your smart contract code. More information on SafeMath can be found here:*
[Open Zepplin Docs](https://docs.openzeppelin.com/contracts/3.x/)

We follow the same steps as Level One. After writing the Soldity code, then compile the code, to ensure there are no errors, and then deploy the contract with 0 wei, for which there is a ETH fee, or gas, charged to primary wallet (in this case HR).*

|![TPS Compile](./Screenshots/TieredProfitSplitterCompile.png "Tiered Profit Splitter Compile") | ![TPS Add Wallets](./Screenshots/TieredProfitSplitterAddWallet.png "Tiered Profit Splitter Add Wallets") |
|:---:|:---:|
| Tiered Profit Splitter - Compile | Tiered Profit Splitter - Add Employee Wallet Addresses |

|![TPS Deploy](./Screenshots/TieredProfitSplitterDeploy.png "Tiered Profit Splitter Deploy") | ![TPS MM confirm](./Screenshots/TieredProfitSplitterConfirmation.png "Tiered Profit Splitter MetaMask confirm") |
|:---:|:---:|
| Tiered Profit Splitter - Deploy | Tiered Profit Splitter - MetMask Confirmation |

Let's confirm the contract has been successfully activated via Ganache.

|![Ganache TPS TXN History](./Screenshots/GanacheTPSTXNhistory.png "Ganache Tiered Profit Splitter Deploy TXN History") | ![Ganache TPS TXN Detail](./Screenshots/GanacheTPSTXNdetail.png "Ganache Tiered Profit Splitter TXN Detail") |
|:---:|:---:|
| Ganache - Tiered Profit Splitter - TXN History | Ganache - Tiered Profit Splitter - TXN Detail |

Once the contract has been activated we will test the functionality by transferring 10 Ether into the employees' accounts.
|![TPS 10 ETH Deposit](./Screenshots/TPS10ETHdeposit.png " Tiered Profit Splitter 10 ETH Deposit") | ![TPS 10 ETH MM confirm](./Screenshots/TPS10ETHMMconfirm.png "Tiered Profit Splitter 10 ETH MM confirm") | ![TPS 10 ETH MM confirmation](./Screenshots/TPS10ETHMMconfirmation.png "Tiered Profit Splitter 10 ETH MM confirmation") |
|:---:|:---:|:---:|
| 10 ETH Deposit | 10 ETH confirm via MetaMask | 10 ETH MetaMask Confirmation|

You'll see that Ganache wallet balances are now updated. 10 ETH was removed from the first account (i.e. HR) and ETH was deposited into each employee's account as follows: 6 ETH to employee_one (i.e. CEO 60%), 2.5 ETH to employee_two (i.e. CTO 25%), and 1.5 ETH to employee_three (i.e. Bob 15%).

|![Ganache TPS Wallet Balances](./Screenshots/GanacheTPSbalances.png "Ganache TPS Wallet Balances") | ![Ganache TPS TXN History](./Screenshots/GanacheTPSTXNhist.png "Ganache TPS TXN History") | ![Ganache TPS TXN Detail](./Screenshots/GanacheTPS10ETHTXNdetail.png "Ganache TPS TXN Detail") |
|:---:|:---:|:---:|
| Ganache Wallet Balances| Ganache TXN History | Ganache TXN Detail|

# Level Three: The Deferred Equity Plan Smart Contract

The **Deferred Equity Plan** models traditional company deferred compensation plans. For this example, the contract will automatically distribute 1,000 shares of company stock per employee with an annual distribution of 250 shares for each employee over a 4 years time period.

|![DEP1](./Screenshots/DEP1.png "Deferred Equity Plan 1") | ![DEP2](./Screenshots/DEP2.png "Deferred Equity Plan 2") | ![DEP3](./Screenshots/DEP3.png "Deferred Equity Plan 3") |
|:---:|:---:|:---:|
| Deferred Equity Plan - 1 | Deferred Equity Plan - 2 | Deferred Equity Plan - 3 |

Because this contract has a lock period, there was a **DeferredEquityPlan_FastForward** contract created to test the functionality of the contract based on false dates. The original instructions ask to test the contract using a fast forward date of += 100 days. However, the distribution for shares in this contract is on a yearly basis. Therefore, in order to properly test the contract, we will use a fakenow fast forward date of += 365 days.

|![DEPFF1](./Screenshots/DEPFF1.png "Deferred Equity Plan Fast Forward 1") | ![DEPFF2](./Screenshots/DEPFF2.png "Deferred Equity Plan Fast Forward 2") | ![DEPFF3](./Screenshots/DEPFF3.png "Deferred Equity Plan Fast Forward 3") |
|:---:|:---:|:---:|
| Deferred Equity Plan Fast Forward - 1 | Deferred Equity Plan Fast Forward - 2 | Deferred Equity Plan Fast Forward - 3 |

After compiling the Fast Forward code, deploy the contract with 0 wei, for which there is a fee, or gas, charged to main wallet address (i.e. HR).

|![DEPFFcompile](./Screenshots/DEPFFcompile.png "Deferred Equity Plan Fast Forward Compile") | ![DEPFFdeploy](./Screenshots/DEPFFdeploy.png "Deferred Equity Plan Fast Forward Deploy 1") 
|:---:|:---:|
| Deferred Equity Plan Fast Forward Compile | Deferred Equity Plan Fast Forward Deploy |

| ![DEPFFMMconfirm](./Screenshots/DEPFFconfirm.png "Deferred Equity Plan Fast Forward MetaMask confirm") | ![DEPFFMMconfirmation](./Screenshots/DEPFFconfirmation.png "Deferred Equity Plan Fast Forward MetaMask confirmation") |
|:---:|:---:|
| Deferred Equity Plan Fast Forward Deploy MetaMask Confirm | Deferred Equity Plan Fast Forward Deploy MetaMask Confirmation |

|![GanacheDEPFFTXNhist](./Screenshots/GanacheDFFTXNhist.png "Ganache Deferred Equity Plan Fast Forward TXH history") | ![GanacheDEPFFTXNdetail](./Screenshots/GanacheDFFTXNdetail.png "Ganache Deferred Equity Plan Fast Forward TXN Detail") | 
|:---:|:---:|
| Ganache - Deferred Equity Plan Fast Forward TXN History | Ganache - Deferred Equity Plan Fast Forward TXN Detail |

Once deploying the contract sucessfully, we need to test the distribution. First we need to fast forward the contract date from today to 1 year from now by clicking on the fastforward button. Again, we are sending a transaction for 0 wei and a fee, or gas, is incurred. Once the fast forward transaction is successful, we can then click the distrbute button to see if our code works. Again, the distrbute is a transaction for 0 wei and there is a fee, or gas, on this transaction. Once the distribute transaction is successful, you can click the dstributed_shares button. As you can see, the transaction did distribute 250 shares sucessfully.

|![DEPFFfakenowMMconfirm](./Screenshots/DEPfakenowFF.png "Deferred Equity Plan Fast Forward FakeNow MetaMask confirm") | ![DEPFFfakenowMMconfirmation](./Screenshots/DEPfakenowFFconfirm.png "Deferred Equity Plan Fast Forward FakeNow MetaMask confirmation") |
|:---:|:---:|
 Deferred Equity Plan Fast Forward FakeNow MetaMask Confirm | Deferred Equity Plan Fast Forward FakeNow MetaMask Confirmation |

|![DEPFFdistMMconfirm](./Screenshots/DEPFFdistconfirm.png "Deferred Equity Plan Fast Forward Distribute MetaMask confirm") | ![DEPFFdistMMconfirmation](./Screenshots/DEPFFdistconfirmation.png "Deferred Equity Plan Fast Forward Distribute MetaMask confirmation") |
|:---:|:---:|
 Deferred Equity Plan Fast Forward Distribute MetaMask Confirm | Deferred Equity Plan Fast Forward Distribute MetaMask Confirmation |

|![GanacheDEPFFTXNhist](./Screenshots/GanacheDEPFFTXNhist.png "Ganache Deferred Equity Plan Fast Forward Distribute TXH history") | ![GanacheDEPFFTXNdetail](./Screenshots/GanacheDFFfakenowTXNdetail.png "Ganache Deferred Equity Plan Fast Forward FakeNow TXN Detail") | ![GanacheDEPFFTXNdetail](./Screenshots/GanacheDFFdistTXNdetail.png "Ganache Deferred Equity Plan Fast Forward Distribute TXN Detail") | 
|:---:|:---:|:---:|
| Ganache - Deferred Equity Plan Fast Forward FakeNow & Distribute TXN History | Ganache - Deferred Equity Plan Fast Forward FakeNow TXN Detail | Ganache - Deferred Equity Plan Fast Forward Distribute TXN Detail |

**CONGRATULATIONS!!** *We have successfully deployed and tested all 3 smart contracts. Now we can deploy these contracts to a live Testnet.*

# Deploying all 3 smart contracts to a live Testnet

Now that we have sucessfully coded and tested our Smart Contracts on our Local Network, we can now deploy all 3 contracts to a live Testnet. For this example, we will deploy the contracts to the Ropsten Testnet due to limited availability of Testnet ETH on the Kovan Testnet network. The Associate Profit Splitter and the Tiered Profit Splitter will each be transacted on the network wth 2 ETH each

Below are screenshots of deployment for all 3 contracts from Remix along wth confirmation screen prints from MetaMask and MetaMask balances.

# Associate Profit Splitter on Ropsten
|![APSDeploy](./Screenshots/APSRopstenDeploy.png "Associate Profit Splitter Remix Deploy") | ![APSDeployConf](./Screenshots/APSRopstenDeployconf.png "Associate Profit Splitter Remix Deploy Confirmation") | ![MetaMaskBalances](./Screenshots/MMBalances.png "MetaMaskBalances") | 
|:---:|:---:|:---:|
| Associate Profit Splitter Remix Deploy | Associate Profit Splitter Remix Deploy Confirmation | MetaMask Balances |

![APSEtherscan](./Screenshots/APSEtherscan.png "Associate Profit Splitter Etherscan")

|![APSTransact](./Screenshots/APSRopstenDeposit.png "Associate Profit Splitter Remix Transact") | ![APSTransactConf](./Screenshots/APSRopstenDepositConf.png "Associate Profit Splitter Remix Transact Confirmation") | ![APSTransactMetaMaskBalances](./Screenshots/APSRopstenDepositMM.png "Associate Profit Splitter Transact MetaMask Balances") | 
|:---:|:---:|:---:|
| Associate Profit Splitter Remix Transact | Associate Profit Splitter Remix Transact Confirmation | Post Transact MetaMask Balances |

# Tiered Profit Splitter
|![TPSDeploy](./Screenshots/TPSRopstenDeploy.png "Tiered Profit Splitter Remix Deploy") | ![TPSDeployConf](./Screenshots/TPSRopstenDeployconf.png "Tiered Profit Splitter Remix Deploy Confirmation") | 
|:---:|:---:|
| Tiered Profit Splitter Remix Deploy | Tiered Profit Splitter Remix Deploy Confirmation |

![TPSEtherscan](./Screenshots/TPSEtherscan.png "Tiered Profit Splitter Etherscan")

|![TPSTransact](./Screenshots/TPSRopstenDeposit.png "Tiered Profit Splitter Remix Transact") | ![TPSTransactConf](./Screenshots/TPSRopstenDepositConf.png "Tiered Profit Splitter Remix Transact Confirmation") | ![TPSTransactMetaMaskBalances](./Screenshots/TPSRopstenDepositMM.png "TPS Transact MetaMask Balances") | 
|:---:|:---:|:---:|
| TieredProfit Splitter Remix Transact | Tiered Profit Splitter Remix Transact Confirmation | Post Transact MetaMask Balances |

# Deferred Equity Plan
|![DEPDeploy](./Screenshots/DEPRopstenDeploy.png "Deferred Equity Plan Remix Deploy") | ![DEPDeployConf](./Screenshots/DEPRopstenDeployconf.png "Deferred Equity Plan Remix Deploy Confirmation") |
|:---:|:---:|
| Deferred Equity Plan Remix Deploy | Deferred Equity Plan Remix Deploy Confirmation |

![DEPEtherscan](./Screenshots/DEPEtherscan.png "Deferred Equity Plan Etherscan")

**CONGRATULATIONS!!** *We have successfully deployed and tested all 3 smart contracts to Ropsten Testnet!*
