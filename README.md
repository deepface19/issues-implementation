# Contract Issues Implementation

## libraries/StableMath.sol
```sol
pragma solidity ^0.6.12;

import "@openzeppelin/contracts-upgradeable/math/SafeMathUpgradeable.sol";

```
- it's code incorrect, you must change code to like this 
```sol
// SPDX-License-Identifier: MIT

pragma solidity 0.8.5;

import "@openzeppelin/contracts-upgradeable/utils/math/SafeMathUpgradeable.sol";

```
