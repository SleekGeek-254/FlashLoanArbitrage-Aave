# FlashLoanArbitrage
This contract allows users to perform arbitrage operations using flash loans on the Aave platform.

# Dependencies
This contract relies on the following dependencies:

* @aave/core-v3/contracts/flashloan/base/FlashLoanSimpleReceiverBase.sol: Provides the base contract for flash loan receiver contracts on the Aave platform.
* @aave/core-v3/contracts/interfaces/IPoolAddressesProvider.sol: Defines the basic interface for a "Pool Addresses Provider". This is used to provide the addresses of various components of the Aave platform that are needed by this contract.
* @aave/core-v3/contracts/dependencies/openzeppelin/contracts/IERC20.sol: Defines the basic interface for ERC-20 token contracts.

# Constructor
The contract is provided with the address of an instance of the "PoolAddressesProvider-Aave" contract as an argument in its constructor. This "PoolAddressesProvider-Aave" contract is used to provide the addresses of various components of the Aave platform that are needed by the "FlashLoanArbitrage" contract. These components might include smart contracts that handle tasks such as loan and deposit management, collateralization, and price oracle services.

In addition to setting the "PoolAddressesProvider-Aave" contract as a dependency, the constructor also does the following:

* Sets the contract's owner to the contract deployer
* Initializes the dai and usdc variables as instances of the ERC-20 token contracts for DAI and USDC,     respectively
* Initializes the dexContract variable as an instance of the contract that implements the IDex interface

# Functions
` executeOperation `
This function is called after the contract has received the flash loaned amount. It contains the logic for the flash loan operation. In this case, it performs an arbitrage operation on the DEX contract, buying and selling DAI to try to profit from price differences between the two tokens.

` requestFlashLoan ` 
This function allows the owner of the contract to request a flash loan of a specified amount of a specified token. It calls the flashLoanSimple function on the Aave POOL contract, passing in the necessary arguments.

` approveUSDC and allowanceUSDC `
These functions allow the contract to approve the DEX contract to spend a certain amount of USDC on its behalf, and check the current allowance for the DEX contract to spend USDC.

` approveDAI and allowanceDAI ` 
These functions allow the contract to approve the DEX contract to spend a certain amount of DAI on its behalf, and check the current allowance for the DEX contract to spend DAI.

` getBalance `
This function allows the contract to check the balance of a specified ERC-20 token contract.

` payBack `
This function allows the contract to pay back the flash loan and any premiums owed to the Aave POOL contract. It calls the repay function on the POOL contract, passing in the necessary arguments.
