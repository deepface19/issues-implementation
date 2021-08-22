# Contract Issues Implementation
## token/USDs.sol
- not found source file  safeMathUpgradeable.sol
- fix to spesific
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.12;

/**
 * @title USDs Token Contract
 * @dev ERC20 compatible contract for USDs
 * @dev Implements an elastic supply
 * @author Origin Protocol Inc
 */

import "@openzeppelin/contracts-upgradeable/proxy/Initializable.sol";
import "@openzeppelin/contracts-upgradeable/access/OwnableUpgradeable.sol";
import "@openzeppelin/contracts-upgradeable/math/SafeMathUpgradeable.sol";
import "@openzeppelin/contracts-upgradeable/utils/AddressUpgradeable.sol";
```
## oracle/Oracle.sol
- not found source file SafeMathUpgradeable.sol
- check and fix to spesific
```solidity
// SPDX-License-Identifier: MIT

//TO-DO: have getUSDsPrice_Average() returns USDs price over longer period;
pragma solidity ^0.6.12;
pragma experimental ABIEncoderV2; //What's this for?


import "@openzeppelin/contracts-upgradeable/proxy/Initializable.sol";
import "@openzeppelin/contracts-upgradeable/access/OwnableUpgradeable.sol";
import "@openzeppelin/contracts-upgradeable/math/SafeMathUpgradeable.sol";
```
## libraries/StableMath.sol
- this code incorrect 
- because line code import ( not spesific ) 
- because Source file SafeMathUpgradeable.sol requires different compiler version builds the released version pragma solidity ^0.8.0;
- so must use pragma solidity 0.8.5 in this file
```solidity
pragma solidity ^0.6.12;

import "@openzeppelin/contracts-upgradeable/math/SafeMathUpgradeable.sol";

```
-  you must change code to like this 
```solidity
// SPDX-License-Identifier: MIT

pragma solidity 0.8.5;

import "@openzeppelin/contracts-upgradeable/utils/math/SafeMathUpgradeable.sol";

```


- and This code in line 33,35 is a error you must fix it ( Explicit type conversion not allowed from "int8" to "uint256" )
```solidity
  if (adjustment > 0) {
            x = x.mul(10**uint256(adjustment));
        } else if (adjustment < 0) {
            x = x.div(10**uint256(adjustment * -1));
        }
        return x;
    }
```
## libraries/UniswapV2OracleLibrary.sol
- error in code line source files let see this
- fix source files IUniswapV2Pair.sol,Babylonian.sol just add spdx licensi
- fix error in code line = 48,53,58,63,68 in file BitMath.sol (Explicit type conversion not allowed from "int_const -1" to "uint16")
- fix error in code line = 81,87,98,100,105,115,117,121,138 in file FixedPoint.sol (Explicit type conversion not allowed from "int_const -1" to "uint144")
- fix error in code line = 8,19,22 in file FullMath.sol ( Unary operator - cannot be applied to type uint256 )
- and add spdx licensi
```solidity
pragma solidity >=0.5.0;

import '../interfaces/IUniswapV2Pair.sol';
import './FixedPoint.sol';

// library with helper methods for oracles that are concerned with computing average prices
library UniswapV2OracleLibrary {
    using FixedPoint for *;

    // helper function that returns the current block timestamp within the range of uint32, i.e. [0, 2**32 - 1]
    function currentBlockTimestamp() internal view returns (uint32) {
        return uint32(block.timestamp % 2 ** 32);
    }

    // produces the cumulative price using counterfactuals to save gas and avoid a call to sync.
    function currentCumulativePrices(
        address pair
    ) internal view returns (uint price0Cumulative, uint price1Cumulative, uint32 blockTimestamp) {
        blockTimestamp = currentBlockTimestamp();
        price0Cumulative = IUniswapV2Pair(pair).price0CumulativeLast();
        price1Cumulative = IUniswapV2Pair(pair).price1CumulativeLast();

        // if time has elapsed since the last update on the pair, mock the accumulated price values
        (uint112 reserve0, uint112 reserve1, uint32 blockTimestampLast) = IUniswapV2Pair(pair).getReserves();
        if (blockTimestampLast != blockTimestamp) {
            // subtraction overflow is desired
            uint32 timeElapsed = blockTimestamp - blockTimestampLast;
            // addition overflow is desired
            // counterfactual
            price0Cumulative += uint(FixedPoint.fraction(reserve1, reserve0)._x) * timeElapsed;
            // counterfactual
            price1Cumulative += uint(FixedPoint.fraction(reserve0, reserve1)._x) * timeElapsed;
        }
    }
}
```
## libraries/InitializableERC20Detail.sol
- fix pragma solidity in this file upgrade to up, because Source file requires different compiler version builds the released version pragma solidity ^0.8.0;
- so use pragma solidity 0.8.5 in this file
- add SPDX Licensi
```solidity
pragma solidity ^0.6.12;

import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";
```
## startegies/InitializableAbstractStrategy.sol
- not found source file SafeERC20Upgradeable.sol";
- check and fix it spesific
```solidity
pragma solidity ^0.6.12;


import "@openzeppelin/contracts-upgradeable/proxy/Initializable.sol";

import "@openzeppelin/contracts-upgradeable/math/SafeMathUpgradeable.sol";
import "@openzeppelin/contracts-upgradeable/token/ERC20/SafeERC20Upgradeable.sol";
import "@openzeppelin/contracts-upgradeable/token/ERC20/ERC20Upgradeable.sol";
```
## vault/VaultStorage.sol
- not found source file Initializable.sol
- check and fix it to spesific
```solidity
pragma solidity ^0.6.12;

import "@openzeppelin/contracts-upgradeable/proxy/Initializable.sol";
import { USDs } from "../token/USDs.sol";
import { BancorFormula } from "../libraries/BancorFormula.sol";
```
## vault/VaultCore.sol
-  not found source file SafeERC20Upgradeable.sol
-  check and fix it to spesific 
```
import "@openzeppelin/contracts-upgradeable/token/ERC20/SafeERC20Upgradeable.sol";
```
