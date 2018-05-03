# PoA Bridge Functional testing

Tests were conducted on the Kovan test network and PoA Sokol, but they have been verified on Kovan Etherscan only. 

For testing purpose the following accounts were used:

### Home network (Sokol)
- [Storage 1](https://sokol.poaexplorer.com/address/search/0xad3ccd040d968af2fa983413d3c8aadd9a6f1c9a) / [Storage 2](https://sokol.poaexplorer.com/address/search/0x8E854802d695269A6F1f3Fcabb2111d2F5A0E6f9)
- [Implementation 1](https://sokol.poaexplorer.com/address/search/0x370b86ba8c5ad9c9f55644826b6819cb4f720aad) / [Implementation 2](https://sokol-explorer.poa.network/account/0x608707f39c8E487eafEDfB190f14392E6239eF00)
- [Validator contract 1](https://sokol-explorer.poa.network/account/0x5F5fB0A1C6e1c95346Eca1771732Db1fD149525B) / [Validator contract 2](https://sokol-explorer.poa.network/account/0x7A070129e443F2f29A9B6320c16a05bA22b4ac0c)
- [Validator 1](https://sokol-explorer.poa.network/account/0x6b1454ea62aa394c98bb63ed6ec8a491ba144a60) / [Validator 2](https://sokol-explorer.poa.network/account/0x8bcb705c12164ef39d6202cc38059a91603e6872)


### Foreign network (Kovan)

- [Storage 1](https://kovan.etherscan.io/address/0x7Ea07cd462eF0d5B51F85d12f232e6BbF646A016) / [Storage 2](https://kovan.etherscan.io/address/0x4055A80216190861Cee084CA6148A0D3bb2725c1) 
- [Implementation 1](https://kovan.etherscan.io/address/0xE58227ae91b3631e13089e9888BBe5E23d779975) / [Implementation 2](https://kovan.etherscan.io/address/0xeB1598642f52B911AF0192002201b5EF0661CC8E)
- [Validator contract 1](https://kovan.etherscan.io/address/0xad3ccd040d968af2fA983413D3c8aADd9a6F1c9a) / [Validator contract 2](https://kovan.etherscan.io/address/0x431c5b97Ba8387EC5979e06b555aeFcC9080A2b2)
- [Validator 1](https://kovan.etherscan.io/address/0x6b1454ea62aa394c98bb63ed6ec8a491ba144a60) / [Validator 2](https://kovan.etherscan.io/address/0x8bcb705c12164ef39d6202cc38059a91603e6872)

<br>
**N.B.** Different storages and different implementations were used. Hence, following TX hashes are related to different implementations/deployments; still, the same contracts from the same commit were used. 

<br>


## Admin behaviour tests

### Expected behaviour

 - [x] Add validators [Home: 0x6b0123](https://sokol.poaexplorer.com/txid/search/0x6b0123736631c34d0a0b1849284d96e79653015e6d240ea61bbcb39d7654b184) / [Foreign: 0x532290](https://kovan.etherscan.io/tx/0x532290af87e310e96bffc86cfae9530eb0d2bf9a5fdce0594ba2fea3a28bbef5)
 - [x] Remove validators [Home: 0x6b0123](https://sokol.poaexplorer.com/txid/search/0x6b0123736631c34d0a0b1849284d96e79653015e6d240ea61bbcb39d7654b184) / [Foreign: 0xaf03a9](https://kovan.etherscan.io/tx/0xaf03a93221c8f16fd398370a0889f741e979089ebcd7982f2bdf5f8179f91679)
 - [x] Set home daily limits on the home bridges [0xf05674](https://sokol.poaexplorer.com/txid/search/0xf0567473d72489d7f3cc6f33cbd14e65985dbb14ae12d3656d1bc80754f7c176)
 - [x] Set foreign daily limits on the foreign bridges [0xfb3de](https://kovan.etherscan.io/tx/0xfb3de489326d4287685638b32ff9ac9c67dd091bb9f7884df765d673d8268e09)
 - [X] Changing MAX transaction limit [Home: 4761c5](https://sokol.poaexplorer.com/txid/search/4761c5ea1ccd5ecf0297000621421e8d1da841f8844b241a1013c5e0c0d320a4) / [Foreign: 0xe78264](https://kovan.etherscan.io/tx/0xe7826480a1ac9ac907ab68b958cea9e6d4baed8c0157870cf391d3ccfaaa0e44)
 - [x] Change MIN transaction limit [Home: 40d393](https://sokol.poaexplorer.com/txid/search/40d39314ad761a271dbfe2becdae8081ea73c397fe1b7a4b316b5fda587ecc0d) / [Foreign: 0x715c8c](https://kovan.etherscan.io/tx/715c8cb9d7acb8fb463087648b2079cbb55a5763f53f83b74e58c1c40c12c85c)
 - [x] Upgrade contracts in case of vulnerability [Foreign: 0x311cc7](https://kovan.etherscan.io/tx/0x311cc7d251ca8bec5f06551c3033429560444934c87adb19eb6850cd24d17483)
 - [x] Set zero as a minimum required signatures from validators [Foreign: 0x116ab7](https://kovan.etherscan.io/tx/0x116ab76466e2291906793aa343de5e594e2c67c22fe9b4d4ef37e0a25bf21a5d)
 - [x] Adding validators that doesn't have any money on their accounts: [Home: 0x6b0123](https://sokol.poaexplorer.com/txid/search/0x6b0123736631c34d0a0b1849284d96e79653015e6d240ea61bbcb39d7654b184) / [Foreign: 0x532290](https://kovan.etherscan.io/tx/0x532290af87e310e96bffc86cfae9530eb0d2bf9a5fdce0594ba2fea3a28bbef5)
 - [x] Set MAX transaction limit < MIN transaction limit [Foreign: 0xe78264](https://kovan.etherscan.io/address/0xe7826480a1ac9ac907ab68b958cea9e6d4baed8c0157870cf391d3ccfaaa0e44)
 - [x] Set MAX transaction limit to zero [Foreign: 0x18bbfa](https://kovan.etherscan.io/address/18bbfad09962bffa862ee14732d1b1bc91bda0bb0c5adb16b2085ec34d39fe9b)
 - [x] Upgrade contracts in case of vulnerability
 	- to one of the previous implementations [Foreign: 0x0x1d4449](https://kovan.etherscan.io/tx/0x1d44494c37c5368139bb613a36edce34f0dbe0065977e32b873b9ce3256d50a4) 
	- to non-contract addresses [Foreign: 0x0x3f8fe1](https://kovan.etherscan.io/tx/0x3f8fe1ef67d6ab83db93e165b9838d882a4621a74d5465183ba79121267a307c) 

#### Disallowed behaviour

 - [x] Set the number of required signatures greater than a number of validators [Foreign: 0x8e264b](https://kovan.etherscan.io/tx/0x8e264b88a53ce7e6553e5ff0a29691b11cc5d2e9581edb20cf467c89457bee14) / [Home: 0x70a094](https://sokol.poaexplorer.com/txid/search/70a0941cf60557b62faccd87e23391270992a8221a79c19b027c4e11e754d621)
 - [x] Set MAX transaction limit to zero [Home: 0x1c71dc](https://sokol.poaexplorer.com/txid/search/1c71dc00002be0b21861d6c7756945c92308f41d268c191bd765934d5f6a325b) 
 - [x] Set MIN transaction limit > MAX transaction limit [Home: 0x94fc5d](https://sokol.poaexplorer.com/txid/search/94fc5d80d9e6a9d26a1ef274ea609805516f5e51f7a49fd0593ccb797c4cc163) 
 - [x] Removing the validator without decreasing number of required signatures [Foreign: 0xa6ad54](https://kovan.etherscan.io/tx/0xa6ad5424a2affab8ceab500c5ca75421b5f652a2a016a906bc673561bcd7b9dc)
 - [x] Add already enlisted/nonlisted validators [Foreign: 0x3b07c5](https://kovan.etherscan.io/tx/0x3b07c5e51a6f6c2bca231f9a5887a4ad95715705b48f71a365ca090e1e2f31cd)
 - [x] Remove non-listed validators [Foreign: 0x653be4](https://kovan.etherscan.io/tx/0x653be4db726fe200c145f37511ce6c1c03115ec61164b390dc78b0b353e7b94f)
 - [x] Set MAX transaction limit greater then Daily limit [Foreign: 0x7ca9cd](https://kovan.etherscan.io/tx/0x7ca9cdbddfccd4e3c2a0943f3154337c3c6d80752c98b35d84fe794570da914c)
 - [x] Set MIN transaction limit > MAX transaction limit on Foreign network [Foreign: 0x495c5f](https://kovan.etherscan.io/tx/0x495c5fcf5f31d965d1ed93ffa1ca1a774f7bc605eb950269b2c46a429a0f1178)


		

<br>

## User behaviour tests
[Home: 0x40aa34](https://sokol.poaexplorer.com/txid/search/0x40aa34fb35ef0804a41c2b4be7d3e3d65c7f6d5c) 
 / [Foreign: 0x40aa34](https://kovan.etherscan.io/address/0x40aa34fb35ef0804a41c2b4be7d3e3d65c7f6d5c) 

### Expected behaviour

 - [x] Home -> Foreign within the limits [Home: 0x90a267](https://sokol.poaexplorer.com/txid/search/0x90a2670bf44615fcf72eac1100f06d95af24cb73099636112089c4fcddb601db) / [0x4b58c9](https://kovan.etherscan.io/tx/0x4b58c9ab4f9d721a043474e3737b56ffc5850da039e3c10f93efae95962413d9)
 - [x] Home -> Foreign breaking the MIN limit (should be reverted) [Home: c3fd49](https://sokol.poaexplorer.com/txid/search/c3fd49d2163cf87f01024aeaceea7a6b1aec80445b73dee51e7c78a706361afd)
 - 
 - [x] Foreign -> Home within the limits [Home: 0x23fd9b](https://sokol.poaexplorer.com/txid/search/0x23fd9be6ebb432c09c0ca524c189a9b585657188af513f5d1176146ac9850268) / [Foreign: 0x23fd9b](https://kovan.etherscan.io/tx/0x23fd9be6ebb432c09c0ca524c189a9b585657188af513f5d1176146ac9850268)
 - [x] Foreign -> Home breaking the MIN limits (should be reverted) [0x54313d](https://kovan.etherscan.io/tx/0x54313dce905a6622912926553036cde9e8de9a30a41370265e47eab4afcd1f02)
 - [x] Foreign -> Home breaking the MAX limits (should be reverted) [0x33c11](https://kovan.etherscan.io/tx/33c11751b9631d86d11e1251aa336019a13d74a84a7d1d81b4ca389b52590b43)



### Unexpected behaviour

 - [x] sends POA coins to Home bridge in order to receive ERC20 token on Foreign Bridge on the same address [Home: 0x5b627](https://sokol.poaexplorer.com/txid/search/0x5b627ab31d1d517bf41f2ba5ec091c88f4c30fdd742756842d7548a826460561)
<br>*The two bridges had different settings. POA Coins were sent and deposited by HomeBridge contract(deposit was within the HomeBridge limits), but no POA20 tokens were issued on Kovan network (required withdraw was out of the limits).*


<br>
