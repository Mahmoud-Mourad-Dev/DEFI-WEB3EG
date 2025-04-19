# DEFI-WEB3EG
## 1- Create Token WEB3EG Using Openzeppelin 
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract Web3EG is ERC20, Ownable {
    constructor() ERC20("Web3 Egypt", "WEB3EG") {
        _mint(msg.sender, 1000000 ether);
//1_000_000 * 10 ** 18 = 1000000000000000000000000

    }
}
```
## 2- Write Script to Deploy on Sepolia with Foundry FrameWork
```solidity
//SPDX-License-Identifier:UNLICENSED
pragma solidity ^0.8.20;
import "forge-std/Script.sol";
import "forge-std/console.sol";
import "src/Web3eg.sol";

contract DeployWeb3eg is Script {

    function run() external{
        vm.startBroadcast();

        Web3eg web3eg = new Web3eg();
        console.log("web3eg deploy at address:",address(web3eg));

        vm.stopBroadcast();

    }
}
```
Command line to Deploy on Sepolia
```
 forge script script/DeployWeb3eg.s.sol:DeployWeb3eg --rpc-url https://sepolia.infura.io/v3/"YOUR_API_KEY" --private-key "your private key" --broadcast
```
## 3- Deploy on Fork Ethereum mainnet


- Run anvil with fork
```
anvil --fork-url https://eth-mainnet.g.alchemy.com/v2/YOUR_API_KEY
```
- Select block
```
anvil --fork-url https://eth-mainnet.g.alchemy.com/v2/YOUR_API_KEY --fork-block-number 15969633
```
- Script to run
  
```  
forge script script/DeployWeb3eg.s.sol:DeployWeb3eg --fork-url http://127.0.0.1:8545
  --fork-block-number 22269552
 --private-key "your private key" --broadcast
```



