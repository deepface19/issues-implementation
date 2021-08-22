# Contract Issues Implementation

## libraries/StableMath.sol
- this code incorrect 
- because line code import ( not spesific ) and the the safemathupgradeable.sol use pragma 0.8.0 and SPDX licensi, so we need add it to code so that it can be in the compiler and read 
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


- and This code is a error you must fixxed
- Explicit type conversion not allowed from "int8" to "uint256".
```solidity
  if (adjustment > 0) {
            x = x.mul(10**uint256(adjustment));
        } else if (adjustment < 0) {
            x = x.div(10**uint256(adjustment * -1));
        }
        return x;
    }
```
