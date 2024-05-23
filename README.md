# Gas config

### Precompile contract address:
- ArbOwner:&emsp;&emsp;&emsp;0x0000000000000000000000000000000000000070
- ArbOwnerPublic: 0x000000000000000000000000000000000000006b
- [More detail](https://github.com/OffchainLabs/nitro-contracts/tree/main/src/precompiles)

### Check address chain owner:
```bash
cast call --rpc-url "<layer3 rpc url>" 0x000000000000000000000000000000000000006b "getAllChainOwners() (address[])"
```

### Config gas ERC20 in range (0.001 ~ 0.01 ERC20)
* Current setting:
  - L1PricingRewardRate: 0
  - L1PricePerUnit: 550000000000 (550 Gwei)
  - MaxTxGasLimit: 250000000000 (250 Gwei)
  - MinimumL2BaseFee: 300000000 (0,3 Gwei)
  - L2BaseFee: 300000000 (0,3 Gwei)
> **Warning**: When setting l1 the price per unit is higher, increase it little by little. If the gas price is greater than 1 Unit ERC20, you may have to abandon that chain. Or you can try to disable configured cap on your orbit node `--execution.rpc.tx-fee-cap=0` [more detail here](https://docs.arbitrum.io/node-running/how-tos/running-an-orbit-node).
* If owner is EOA address:
```bash
# 1. SetL1PricingRewardRate
cast send 0x0000000000000000000000000000000000000070 "setL1PricingRewardRate(uint64)" 0 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 2. SetL1PricePerUnit
cast send 0x0000000000000000000000000000000000000070 "setL1PricePerUnit(uint256)" 550000000000 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 3. SetMaxTxGasLimit
cast send 0x0000000000000000000000000000000000000070 "setMaxTxGasLimit(uint64)" 250000000000 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 4. SetMinimumL2BaseFee
cast send 0x0000000000000000000000000000000000000070 "setMinimumL2BaseFee(uint256)" 300000000 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 5. SetL2BaseFee
cast send 0x0000000000000000000000000000000000000070 "setL2BaseFee(uint256)" 300000000 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
```
* If owner is UpgradeExecutor contract:
```bash
# 1. SetL1PricingRewardRate
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setL1PricingRewardRate(uint64)" 0) --private-key "<private key>"
# 2. SetL1PricePerUnit
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setL1PricePerUnit(uint256)" 550000000000) --private-key "<private key>"
# 3. SetMaxTxGasLimit
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setMaxTxGasLimit(uint64)" 250000000000) --private-key "<private key>"
# 4. SetMinimumL2BaseFee
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setMinimumL2BaseFee(uint256)" 300000000) --private-key "<private key>"
# 5. SetL2BaseFee
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setL2BaseFee(uint256)" 300000000) --private-key "<private key>"
```

### Config gas ETH in range (0.00000034541-0.00005215389 ETH)
* Current setting:
  - L1PricingRewardRate: 0
  - L1PricePerUnit: 0
  - MaxTxGasLimit: 250000000000 (250 Gwei)
  - MinimumL2BaseFee: 10000000 (0,01 Gwei)
  - L2BaseFee: 10000000 (0,01 Gwei)
> **Warning**: When setting l1 the price per unit is higher, increase it little by little. If the gas price is greater than 1 ETH, you may have to abandon that chain. Or you can try to disable configured cap on your orbit node `--execution.rpc.tx-fee-cap=0` [more detail here](https://docs.arbitrum.io/node-running/how-tos/running-an-orbit-node).
* If owner is EOA address:
```bash
# 1. SetL1PricingRewardRate
cast send 0x0000000000000000000000000000000000000070 "setL1PricingRewardRate(uint64)" 0 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 2. SetL1PricePerUnit
cast send 0x0000000000000000000000000000000000000070 "setL1PricePerUnit(uint256)" 0 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 3. SetMaxTxGasLimit
cast send 0x0000000000000000000000000000000000000070 "setMaxTxGasLimit(uint64)" 250000000000 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 4. SetMinimumL2BaseFee
cast send 0x0000000000000000000000000000000000000070 "setMinimumL2BaseFee(uint256)" 10000000 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
# 5. SetL2BaseFee
cast send 0x0000000000000000000000000000000000000070 "setL2BaseFee(uint256)" 10000000 --private-key "<private key>" --rpc-url "<layer3 rpc url>"
```
* If owner is UpgradeExecutor contract:
```bash
# 1. SetL1PricingRewardRate
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setL1PricingRewardRate(uint64)" 0) --private-key "<private key>"
# 2. SetL1PricePerUnit
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setL1PricePerUnit(uint256)" 0) --private-key "<private key>"
# 3. SetMaxTxGasLimit
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setMaxTxGasLimit(uint64)" 250000000000) --private-key "<private key>"
# 4. SetMinimumL2BaseFee
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setMinimumL2BaseFee(uint256)" 10000000) --private-key "<private key>"
# 5. SetL2BaseFee
cast send --rpc-url "<layer3 rpc url>" "<UpgradeExecutor contract address on layer3>" "executeCall(address,bytes)" 0x0000000000000000000000000000000000000070 $(cast calldata "setL2BaseFee(uint256)" 10000000) --private-key "<private key>"
```

### Check gas base fee:
```bash
cast gas-price --rpc-url "<layer3 rpc url>"
```
> **Notice**: If the result does not equal your L2BaseFee or MinimumL2BaseFee, please try setting L2BaseFee and MinimumL2BaseFee a couple of times.
### Errors:
  - (code: -32000, message: execution reverted, data: None): Incorrect type parameter
  - (code: -32000, message: intrinsic gas too low, data: None): Add these options to the failed command `--gas-price <your-gas-price> --gas-limit <your-gas-limit>`
  - (code: -32000, message: max fee per gas less than block base fee: address 0xa97044ced980AFc8d077A5a69F1d50A9e8899548, maxFeePerGas: 30000000 baseFee: 100000000, data: None): Gas price less than base fee
  - (code: -32000, message: tx fee (6.87 ether) exceeds the configured cap (1.00 ether), data: None): Try to disable configured cap on orbit node.
