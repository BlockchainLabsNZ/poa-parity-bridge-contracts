# Gas Usage

```
  Contract: SafeMath
	deploying validators
   	 add
	hooking up eternal storage to BridgeValidators
      ✓ adds correctly (1104422 gas)
	deploying home storage on home network
      ✓ throws an error on addition overflow (908565 gas)
    sub
      ✓ subtracts correctly (2573112 gas)
      ✓ throws an error if subtraction result would be negative (1799060 gas)
    mul
	deploying ForeignBridge
      ✓ multiplies correctly (922932 gas)
      ✓ handles a zero product correctly (774052 gas)
      ✓ throws an error on multiplication overflow (3187353 gas)
    div
      ✓ divides correctly (269166 gas)
	all is done
    validators: 0xdf08f82de32b8d460adbe8d72043e3a7e25a3b39
    Owner: 0xdf08f82de32b8d460adbe8d72043e3a7e25a3b39
    Foreign Bridge: 0x5bab00b1582b170dbae7557586a29ba9eea6f55b
    Home Bridge: 0xc61431eb6c69189f844a595234ce331b7c8a7a77
    POA20: 0x9c47796bc1e469a60dcbf680273ff011e45a1327
      ✓ throws an error on zero division (30550 gas)

  Contract: ForeignBridge
    #initialize
      ✓ should initialize (5868522 gas)
    #deposit
      ✓ should allow validator to deposit (155094 gas)
      ✓ test with 2 signatures required (7242173 gas)
      ✓ test with 10 signatures required (7874251 gas)
      ✓ should not allow to double submit (185155 gas)
      ✓ should not allow non-authorities to execute deposit (59307 gas)
    #onTokenTransfer
      ✓ can only be called from token contract (5915348 gas)
      ✓ should not allow to burn more than the limit (6009391 gas)
      ✓ should only let to send within maxPerTx limit (6171563 gas)
      ✓ should not let to withdraw less than minPerTx (6013903 gas)
    #submitSignature
      ✓ allows a validator to submit a signature (285399 gas)
      ✓ when enough requiredSignatures are collected, CollectedSignatures event is emitted (525170 gas)
    #setting limits
      ✓ #setMaxPerTx allows to set only to owner and cannot be more than daily limit (112218 gas)
      ✓ #setMinPerTx allows to set only to owner and cannot be more than daily limit and should be less than maxPerTx (112359 gas)
      ✓ #setGasLimits allows to set gas limit (98075 gas)
      ✓ setForeignDailyLimit allows to set foreignDailyLimit (61749 gas)
    #upgradeable
      ✓ can be upgraded (12067361 gas)
      ✓ can be deployed via upgradeToAndCall (4211509 gas)
    #claimTokens
      ✓ can send erc20 (8476933 gas)
      ✓ also calls claimTokens on tokenAddress (8358587 gas)
      ✓ should transfer eth balance to the owner (5868453 gas)

  Contract: HomeBridge
    #initialize
      ✓ sets variables (1945480 gas)
      ✓ cant set maxPerTx > homeDailyLimit (1847403 gas)
      ✓ can be deployed via upgradeToAndCall (2770063 gas)
    #fallback
      ✓ should accept POA (275388 gas)
      ✓ doesnt let you send more than max amount per tx (353124 gas)
      ✓ should not let to deposit less than minPerTx (306914 gas)
    #withdraw
      ✓ should allow to withdraw (121190 gas)
      ✓ should allow second withdraw with different transactionHash but same recipient and value (197043 gas)
      ✓ should not allow if there are not enough funds in the contract (119529 gas)
      ✓ should not allow second withdraw (replay attack) with same transactionHash but different recipient (167421 gas)
    #withdraw with 2 minimum signatures
      ✓ withdraw should fail if not enough signatures are provided (168950 gas)
      ✓ withdraw should fail if duplicate signature is provided (102590 gas)
    #setting limits
      ✓ #setMaxPerTx allows to set only to owner and cannot be more than daily limit (226602 gas)
      ✓ #setMinPerTx allows to set only to owner and cannot be more than daily limit and should be less than maxPerTx (227298 gas)
      ✓ shoule allow to set gas limit withdraw relay (192357 gas)

  Contract: POA20
    ✓ default values (2349703 gas)
    #mint
      ✓ can mint by owner (2417704 gas)
      ✓ no one can call finishMinting (2371367 gas)
      ✓ cannot mint by non-owner (2373196 gas)
    #transfer
      ✓ sends tokens to recipient (2478135 gas)
    #burn
      ✓ can burn (2457938 gas)
    #transferAndCall
      ✓ calls contractFallback (3003581 gas)
    #claimtokens
      ✓ can take send ERC20 tokens (4922775 gas)

  Contract: EternalStorageProxy
    ✓ can't send ETH to storage proxy if implementation is not set (795491 gas)
    ✓ proxy ownership can be transferred (804393 gas)
    ✓ only the proxy owner can transfer proxy ownership (797374 gas)
    ✓ can't accidentally transfer proxy ownership to null address (796138 gas)
    ✓ can't upgrade the implementation of bridge validator to the current implementation (1902769 gas)
    ✓ upgradeToAndCall function can only be called by the proxy owner (1839452 gas)
    ✓ upgradeToAndCall function calls the fallback function (1994601 gas)
    #initialize
      ✓ version should return as expected (67437 gas)
      ✓ bridgeValidator has owner set correctly should return as expected (67437 gas)
      ✓ bridgeValidator can have ownership transferred (98295 gas)
      ✓ bridgeValidator can't transfer ownership to the null address (89716 gas)
      ✓ bridgeValidator can only have ownership transferred by the owner (90952 gas)

  Contract: BridgeValidators
    #initialize
      ✓ sets values (1276018 gas)
    #addValidator
      ✓ adds validator (237353 gas)
      ✓ cannot add already existing validator (6906741 gas)
    #removeValidator
      ✓ removes validator (237807 gas)
      ✓ cannot remove if it will break requiredSignatures (238668 gas)
      ✓ cannot remove non-existent validator (240633 gas)
    #setRequiredSignatures
      ✓ sets req signatures (242354 gas)
      ✓ cannot set more than validators count (214926 gas)
    #upgradable
      ✓ can be upgraded via upgradeToAndCall (2024345 gas)

·------------------------------------------------------------------------------------------|-----------------------------------·
│                                           Gas                                            ·  Block limit: 17592186044415 gas  │
························································|··································|····································
│  Methods                                              ·           21 gwei/gas            ·          668.49 usd/eth           │
·····························|··························|··········|···········|···········|··················|·················
│  Contract                  ·  Method                  ·  Min     ·  Max      ·  Avg      ·  # calls         ·  usd (avg)     │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  deposit                 ·   60652  ·   124480  ·    93949  ·              15  ·          1.32  │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  initialize              ·  169609  ·   171243  ·   169929  ·              12  ·          2.39  │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  onTokenTransfer         ·       -  ·        -  ·        -  ·               0  ·             -  │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  setForeignDailyLimit    ·       -  ·        -  ·    31135  ·               2  ·          0.44  │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  setGasLimits            ·       -  ·        -  ·    67461  ·               1  ·          0.95  │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  setMaxPerTx             ·   30343  ·    30817  ·    30462  ·               4  ·          0.43  │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  setMinPerTx             ·   30724  ·    31134  ·    30861  ·               3  ·          0.43  │
·····························|··························|··········|···········|···········|··················|·················
│  ForeignBridgeMock         ·  submitSignature         ·  155572  ·   254785  ·   221714  ·               3  ·          3.11  │
·····························|··························|··········|···········|···········|··················|·················
│  Ownable                   ·  transferOwnership       ·   30550  ·    30858  ·    30618  ·              26  ·          0.43  │
·····························|··························|··········|···········|···········|··················|·················
│  OwnedUpgradeabilityProxy  ·  transferProxyOwnership  ·       -  ·        -  ·    30341  ·               1  ·          0.43  │
·····························|··························|··········|···········|···········|··················|·················
│  OwnedUpgradeabilityProxy  ·  upgradeTo               ·   42430  ·    67437  ·    65158  ·              11  ·          0.91  │
·····························|··························|··········|···········|···········|··················|·················
│  OwnedUpgradeabilityProxy  ·  upgradeToAndCall        ·  183564  ·   220294  ·   206882  ·               5  ·          2.90  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  approve                 ·       -  ·        -  ·        -  ·               0  ·             -  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  burn                    ·       -  ·        -  ·    18112  ·               1  ·          0.25  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  claimTokens             ·   31513  ·    65787  ·    48764  ·               7  ·          0.68  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  decreaseApproval        ·       -  ·        -  ·        -  ·               0  ·             -  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  finishMinting           ·       -  ·        -  ·        -  ·               0  ·             -  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  increaseApproval        ·       -  ·        -  ·        -  ·               0  ·             -  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  mint                    ·   68001  ·    68385  ·    68193  ·              11  ·          0.96  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  transfer                ·   36673  ·    51737  ·    39814  ·               5  ·          0.56  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  transferAndCall         ·   56481  ·   166398  ·    87088  ·               8  ·          1.22  │
·····························|··························|··········|···········|···········|··················|·················
│  POA20                     ·  transferFrom            ·       -  ·        -  ·        -  ·               0  ·             -  │
·····························|··························|··········|···········|···········|··················|·················
│  Deployments                                          ·                                  ·  % of limit      ·                │
························································|··········|···········|···········|··················|·················
│  ERC677                                               ·  372032  ·  3302430  ·  1904810  ·             0 %  ·         26.74  │
·-------------------------------------------------------|----------|-----------|-----------|------------------|----------------·

  74 passing (2m)
```