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


