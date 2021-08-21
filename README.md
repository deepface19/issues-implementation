# Contract Issues Implementation

## libraries/StableMath.sol
- this code incorrect 
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


