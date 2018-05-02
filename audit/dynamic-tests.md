# Dynamic Analysis

```
Contract: ForeignBridge
  #initialize
    ✓ should initialize (1162ms)
  #deposit
    ✓ should allow validator to deposit (170ms)
    ✓ test with 2 signatures required (672ms)
    ✓ test with 10 signatures required (846ms)
    ✓ should not allow to double submit (100ms)
    ✓ should not allow non-authorities to execute deposit
  #onTokenTransfer
    ✓ can only be called from token contract (463ms)
    ✓ should not allow to burn more than the limit (528ms)
    ✓ should only let to send within maxPerTx limit (458ms)
    ✓ should not let to withdraw less than minPerTx (347ms)
  #submitSignature
    ✓ allows a validator to submit a signature (184ms)
    ✓ when enough requiredSignatures are collected, CollectedSignatures event is emitted (293ms)
  #setting limits
    ✓ #setMaxPerTx allows to set only to owner and cannot be more than daily limit (81ms)
    ✓ #setMinPerTx allows to set only to owner and cannot be more than daily limit and should be less than maxPerTx (86ms)
    ✓ #setGasLimits allows to set gas limit (52ms)
    ✓ setForeignDailyLimit allows to set foreignDailyLimit (51ms)
  #upgradeable
    ✓ can be upgraded (624ms)
    ✓ can be deployed via upgradeToAndCall (331ms)
  #claimTokens
    ✓ can send erc20 (400ms)
    ✓ also calls claimTokens on tokenAddress (435ms)
    ✓ should transfer eth balance to the owner (827ms)
Contract: SafeMath
  add
    ✓ adds correctly
    ✓ throws an error on addition overflow
  sub
    ✓ subtracts correctly
    ✓ throws an error if subtraction result would be negative
  mul
    ✓ multiplies correctly
    ✓ handles a zero product correctly
    ✓ throws an error on multiplication overflow
  div
    ✓ divides correctly
    ✓ throws an error on zero division
Contract: HomeBridge
  #initialize
    ✓ sets variables (180ms)
    ✓ cant set maxPerTx > homeDailyLimit (68ms)
    ✓ can be deployed via upgradeToAndCall (170ms)
  #fallback
    ✓ should accept POA (167ms)
    ✓ doesnt let you send more than max amount per tx (173ms)
    ✓ should not let to deposit less than minPerTx (141ms)
  #withdraw
    ✓ should allow to withdraw (673ms)
    ✓ should allow second withdraw with different transactionHash but same recipient and value (767ms)
    ✓ should not allow if there are not enough funds in the contract (366ms)
    ✓ should not allow second withdraw (replay attack) with same transactionHash but different recipient (420ms)
  #withdraw with 2 minimum signatures
    ✓ withdraw should fail if not enough signatures are provided (752ms)
    ✓ withdraw should fail if duplicate signature is provided (379ms)
  #setting limits
    ✓ #setMaxPerTx allows to set only to owner and cannot be more than daily limit (75ms)
    ✓ #setMinPerTx allows to set only to owner and cannot be more than daily limit and should be less than maxPerTx (74ms)
    ✓ shoule allow to set gas limit withdraw relay (41ms)
Contract: POA20
  ✓ default values (70ms)
  #mint
    ✓ can mint by owner (75ms)
    ✓ no one can call finishMinting
    ✓ cannot mint by non-owner (51ms)
  #transfer
    ✓ sends tokens to recipient (99ms)
  #burn
    ✓ can burn (106ms)
  #transferAndCall
    ✓ calls contractFallback (262ms)
  #claimtokens
    ✓ can take send ERC20 tokens (888ms)
Contract: EternalStorageProxy
  ✓ can't send ETH to storage proxy if implementation is not set
  ✓ proxy ownership can be transferred (45ms)
  ✓ only the proxy owner can transfer proxy ownership
  ✓ can't accidentally transfer proxy ownership to null address (44ms)
  ✓ can't upgrade the implementation of bridge validator to the current implementation (95ms)
  ✓ upgradeToAndCall function can only be called by the proxy owner (57ms)
  ✓ upgradeToAndCall function calls the fallback function (92ms)
  #initialize
    ✓ version should return as expected
    ✓ bridgeValidator has owner set correctly should return as expected
    ✓ bridgeValidator can have ownership transferred (56ms)
    ✓ bridgeValidator can't transfer ownership to the null address (40ms)
    ✓ bridgeValidator can only have ownership transferred by the owner (50ms)
Contract: BridgeValidators
  #initialize
    ✓ sets values (233ms)
  #addValidator
    ✓ adds validator (99ms)
    ✓ cannot add already existing validator (66ms)
  #removeValidator
    ✓ removes validator (78ms)
    ✓ cannot remove if it will break requiredSignatures (104ms)
    ✓ cannot remove non-existent validator (54ms)
  #setRequiredSignatures
    ✓ sets req signatures (56ms)
    ✓ cannot set more than validators count (139ms)
  #upgradable
    ✓ can be upgraded via upgradeToAndCall (193ms)
74 passing (24s)
```
