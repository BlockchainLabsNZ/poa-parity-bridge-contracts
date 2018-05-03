# POA Bridge Smart Contracts Audit Report

## Preamble
This audit report was undertaken by **BlockchainLabs.nz** for the purpose of providing feedback regarding **POA Bridge Smart Contracts**.

It has subsequently been shared publicly without any express or implied warranty.

Solidity contracts were sourced from the public Github repo [poanetwork/poa-parity-bridge-contracts](https://github.com/poanetwork/poa-parity-bridge-contracts) and the most recent commit we have audited is this [23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/commit/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6) - we would encourage all community members and token holders to make their own assessment of the contracts.

## Scope
The following contracts were subject for static, dynamic and functional analyses:

- Libraries
  - [Helpers.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/libraries/Helpers.sol)
  - [Message.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/libraries/Message.sol)
  - [SafeMath.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/libraries/SafeMath.sol)
- Upgradeability
  - [EternalStorage.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeability/EternalStorage.sol)
  - [EternalStorageProxy.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeability/EternalStorageProxy.sol)
  - [OwnedUpgradeabilityProxy.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeability/OwnedUpgradeabilityProxy.sol)
  - [Proxy.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeability/Proxy.sol)
  - [UpgradeabilityOwnerStorage.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeability/UpgradeabilityOwnerStorage.sol)
  - [UpgradeabilityProxy.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeability/UpgradeabilityProxy.sol)
  - [UpgradeabilityStorage.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeability/UpgradeabilityStorage.sol)
- Upgradeable Contracts
  - [Ownable.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeable_contracts/Ownable.sol)
  - [U_BridgeValidators.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeable_contracts/U_BridgeValidators.sol)
  - [U_ForeignBridge.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeable_contracts/U_ForeignBridge.sol)
  - [U_Validatable.sol](https://github.com/BlockchainLabsNZ/poa-parity-bridge-contracts/blob/23d45d2d0a10d8e38704e7610c302aa3ebbe5dd6/contracts/upgradeable_contracts/U_Validatable.sol)

## Focus areas
The audit report is focused on the following key areas - though this is not an exhaustive list.

### Correctness
- No correctness defects uncovered during static analysis?
- No implemented contract violations uncovered during execution?
- No other generic incorrect behaviour detected during execution?
- Adherence to adopted standards such as ERC20?

### Testability
- Test coverage across all functions and events?
- Test cases for both expected behaviour and failure modes?
- Settings for easy testing of a range of parameters?
- No reliance on nested callback functions or console logs?
- Avoidance of test scenarios calling other test scenarios?

### Security
- No presence of known security weaknesses?
- No funds at risk of malicious attempts to withdraw/transfer?
- No funds at risk of control fraud?
- Prevention of Integer Overflow or Underflow?

### Best Practice
- Explicit labeling for the visibility of functions and state variables?
- Proper management of gas limits and nested execution?
- Latest version of the Solidity compiler?

## Analysis

- [Functional Tests](functional-testing.md)
- [Dynamic Tests](dynamic-tests.md)
- [Gas Usage](dynamic-testing.md)
- [Test Coverage](test-coverage.md)

## Issues

### Severity Description
<table>
<tr>
  <td>Minor</td>
  <td>A defect that does not have a material impact on the contract execution and is likely to be subjective.</td>
</tr>
<tr>
  <td>Moderate</td>
  <td>A defect that could impact the desired outcome of the contract execution in a specific scenario.</td>
</tr>
<tr>
  <td>Major</td>
  <td> A defect that impacts the desired outcome of the contract execution or introduces a weakness that may be exploited.</td>
</tr>
<tr>
  <td>Critical</td>
  <td>A defect that presents a significant security vulnerability or failure of the contract across a range of scenarios.</td>
</tr>
</table>

### Minor

- None found

### Moderate

- None found

### Major

- None found

### Critical

- None found

## Observations

- It is possible to set the minimum number of required signatures from validators to zero: [Foreign: 0x116ab7](https://kovan.etherscan.io/tx/0x116ab76466e2291906793aa343de5e594e2c67c22fe9b4d4ef37e0a25bf21a5d)
- It is possible to add validators that don't have any funds in their accounts: [Home: 0x6b0123](https://sokol.poaexplorer.com/txid/search/0x6b0123736631c34d0a0b1849284d96e79653015e6d240ea61bbcb39d7654b184) / [Foreign: 0x532290](https://kovan.etherscan.io/tx/0x532290af87e310e96bffc86cfae9530eb0d2bf9a5fdce0594ba2fea3a28bbef5)
- You can set the MAX transaction limit to less than the MIN transaction limit [Foreign: 0xe78264](https://kovan.etherscan.io/tx/0xe7826480a1ac9ac907ab68b958cea9e6d4baed8c0157870cf391d3ccfaaa0e44)
- You can set the MAX transaction limit to 0 [Foreign: 0x18bbfa](https://kovan.etherscan.io/tx/18bbfad09962bffa862ee14732d1b1bc91bda0bb0c5adb16b2085ec34d39fe9b)
- When you upgrade the implentation of contracts
  - to a previous implementation [Foreign: 0x01d4449](https://kovan.etherscan.io/tx/0x1d44494c37c5368139bb613a36edce34f0dbe0065977e32b873b9ce3256d50a4)
  - to a non-contract address [Foreign: 0x3f8fe1](https://kovan.etherscan.io/tx/0x3f8fe1ef67d6ab83db93e165b9838d882a4621a74d5465183ba79121267a307c)


## Conclusion

We are statisfied that these Smart Contracts do not exhibit any known security vulnerabilities. Overall the code is well written and the developers have been responsive and active throughout the audit process. The contracts show care taken by the developers to follow best practices and a strong knowledge of Solidity. There is very high test coverage which should increase confidence in the security of these contracts, and their maintainability in the future. As part of our auditting process we added some new tests to improve the coverage.


___

### Disclaimer

Our team uses our current understanding of the best practises for Solidity and Smart Contracts. Development in Solidity and for Blockchain is an emergering area of software engineering which still has a lot of room to grow, hence our current understanding of best practise may not find all of the issues in this code and design.

We have not analysed any of the assembly code generated by the Solidity compiler. We have not verified the deployment process and configurations of the contracts. We have only analysed the code outlined in the scope. We have not verified any of the claims made by any of the organisations behind this code.

Security audits do not warrant bug-free code. We encourge all users interacting with smart contract code to continue to analyse and inform themselves of any risks before interacting with any smart contracts.
