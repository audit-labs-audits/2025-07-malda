# Malda contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the **Issues** page in your private contest repo (label issues as **Medium** or **High**)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Q&A

### Q: On what chains are the smart contracts going to be deployed?
Ethereum, Base, Linea, Optimism, Unichain, Arbitrum, + other EVM chains. 
___

### Q: If you are integrating tokens, are you allowing only whitelisted tokens to work with the codebase or any complying with the standard? Are they assumed to have certain properties, e.g. be non-reentrant? Are there any types of [weird tokens](https://github.com/d-xo/weird-erc20) you want to integrate?
Whitelisted listing process, ERC-20 + non-rebase tokens. 
___

### Q: Are there any limitations on values set by admins (or other roles) in the codebase, including restrictions on array lengths?
Owner is trusted
Sequnecer is semi-trusted - It is trusted to maintain volume control and monitor the underlying chains for security. It can only execute UserOps based on zkProofs
Rebalancer is semi-trusted - Rebalancer only has DDOS abilities for the protocol via constant rebalancing. It cannot transfer user funds
Pauser is trusted
___

### Q: Are there any limitations on values set by admins (or other roles) in protocols you integrate with, including restrictions on array lengths?
No
___

### Q: Is the codebase expected to comply with any specific EIPs?
No
___

### Q: Are there any off-chain mechanisms involved in the protocol (e.g., keeper bots, arbitrage bots, etc.)? We assume these mechanisms will not misbehave, delay, or go offline unless otherwise specified.
Liquidators - Expected to liquidate positions like in other lending protocols
Sequencer (Centralized) - Expected to deliver proofs and execute UserOps via those proofs for all multichain interactions
Rebalancer (Centralized) - Expected to maintain liquidity across all deployments by rebalancing liquidity predicted by demand

___

### Q: What properties/invariants do you want to hold even if breaking them has a low/unknown impact?
No
___

### Q: Please discuss any design choices you made.
Sequencer - We chose to implement a centralized sequencer design that executes cross-chain actions without waiting for full L1 finality for rollups. This design choice was implemented to provide the users lower latency, while maintaining additional security checks that are not feasible with current ZK technology to be programmed into a zk-proof. 
___

### Q: Please provide links to previous audits (if any) and all the known issues or acceptable risks.
https://docs.malda.xyz/malda-protocol/audit-reports
___

### Q: Please list any relevant protocol resources.
https://docs.malda.xyz/



# Audit scope

[malda-lending @ ab4fa9b2da94bc7f5b0e6d4c52f61e28b0820a54](https://github.com/malda-protocol/malda-lending/tree/ab4fa9b2da94bc7f5b0e6d4c52f61e28b0820a54)
- [malda-lending/lib/forge-std/.gitattributes](malda-lending/lib/forge-std/.gitattributes)
- [malda-lending/lib/forge-std/.github/workflows/ci.yml](malda-lending/lib/forge-std/.github/workflows/ci.yml)
- [malda-lending/lib/forge-std/.github/workflows/sync.yml](malda-lending/lib/forge-std/.github/workflows/sync.yml)
- [malda-lending/lib/forge-std/.gitignore](malda-lending/lib/forge-std/.gitignore)
- [malda-lending/lib/forge-std/LICENSE-APACHE](malda-lending/lib/forge-std/LICENSE-APACHE)
- [malda-lending/lib/forge-std/LICENSE-MIT](malda-lending/lib/forge-std/LICENSE-MIT)
- [malda-lending/lib/forge-std/README.md](malda-lending/lib/forge-std/README.md)
- [malda-lending/lib/forge-std/foundry.toml](malda-lending/lib/forge-std/foundry.toml)
- [malda-lending/lib/forge-std/package.json](malda-lending/lib/forge-std/package.json)
- [malda-lending/lib/forge-std/scripts/vm.py](malda-lending/lib/forge-std/scripts/vm.py)
- [malda-lending/lib/forge-std/src/Base.sol](malda-lending/lib/forge-std/src/Base.sol)
- [malda-lending/lib/forge-std/src/Script.sol](malda-lending/lib/forge-std/src/Script.sol)
- [malda-lending/lib/forge-std/src/StdAssertions.sol](malda-lending/lib/forge-std/src/StdAssertions.sol)
- [malda-lending/lib/forge-std/src/StdChains.sol](malda-lending/lib/forge-std/src/StdChains.sol)
- [malda-lending/lib/forge-std/src/StdCheats.sol](malda-lending/lib/forge-std/src/StdCheats.sol)
- [malda-lending/lib/forge-std/src/StdError.sol](malda-lending/lib/forge-std/src/StdError.sol)
- [malda-lending/lib/forge-std/src/StdInvariant.sol](malda-lending/lib/forge-std/src/StdInvariant.sol)
- [malda-lending/lib/forge-std/src/StdJson.sol](malda-lending/lib/forge-std/src/StdJson.sol)
- [malda-lending/lib/forge-std/src/StdMath.sol](malda-lending/lib/forge-std/src/StdMath.sol)
- [malda-lending/lib/forge-std/src/StdStorage.sol](malda-lending/lib/forge-std/src/StdStorage.sol)
- [malda-lending/lib/forge-std/src/StdStyle.sol](malda-lending/lib/forge-std/src/StdStyle.sol)
- [malda-lending/lib/forge-std/src/StdToml.sol](malda-lending/lib/forge-std/src/StdToml.sol)
- [malda-lending/lib/forge-std/src/StdUtils.sol](malda-lending/lib/forge-std/src/StdUtils.sol)
- [malda-lending/lib/forge-std/src/Test.sol](malda-lending/lib/forge-std/src/Test.sol)
- [malda-lending/lib/forge-std/src/Vm.sol](malda-lending/lib/forge-std/src/Vm.sol)
- [malda-lending/lib/forge-std/src/console.sol](malda-lending/lib/forge-std/src/console.sol)
- [malda-lending/lib/forge-std/src/console2.sol](malda-lending/lib/forge-std/src/console2.sol)
- [malda-lending/src/Operator/Operator.sol](malda-lending/src/Operator/Operator.sol)
- [malda-lending/src/Operator/OperatorStorage.sol](malda-lending/src/Operator/OperatorStorage.sol)
- [malda-lending/src/Roles.sol](malda-lending/src/Roles.sol)
- [malda-lending/src/blacklister/Blacklister.sol](malda-lending/src/blacklister/Blacklister.sol)
- [malda-lending/src/interest/JumpRateModelV4.sol](malda-lending/src/interest/JumpRateModelV4.sol)
- [malda-lending/src/mToken/BatchSubmitter.sol](malda-lending/src/mToken/BatchSubmitter.sol)
- [malda-lending/src/mToken/extension/mTokenGateway.sol](malda-lending/src/mToken/extension/mTokenGateway.sol)
- [malda-lending/src/mToken/host/mErc20Host.sol](malda-lending/src/mToken/host/mErc20Host.sol)
- [malda-lending/src/mToken/mErc20.sol](malda-lending/src/mToken/mErc20.sol)
- [malda-lending/src/mToken/mErc20Immutable.sol](malda-lending/src/mToken/mErc20Immutable.sol)
- [malda-lending/src/mToken/mErc20Upgradable.sol](malda-lending/src/mToken/mErc20Upgradable.sol)
- [malda-lending/src/mToken/mToken.sol](malda-lending/src/mToken/mToken.sol)
- [malda-lending/src/mToken/mTokenConfiguration.sol](malda-lending/src/mToken/mTokenConfiguration.sol)
- [malda-lending/src/mToken/mTokenStorage.sol](malda-lending/src/mToken/mTokenStorage.sol)
- [malda-lending/src/migration/IMigrator.sol](malda-lending/src/migration/IMigrator.sol)
- [malda-lending/src/migration/Migrator.sol](malda-lending/src/migration/Migrator.sol)
- [malda-lending/src/oracles/MixedPriceOracleV3.sol](malda-lending/src/oracles/MixedPriceOracleV3.sol)
- [malda-lending/src/oracles/MixedPriceOracleV4.sol](malda-lending/src/oracles/MixedPriceOracleV4.sol)
- [malda-lending/src/oracles/gas/DefaultGasHelper.sol](malda-lending/src/oracles/gas/DefaultGasHelper.sol)
- [malda-lending/src/pauser/Pauser.sol](malda-lending/src/pauser/Pauser.sol)
- [malda-lending/src/rebalancer/Rebalancer.sol](malda-lending/src/rebalancer/Rebalancer.sol)
- [malda-lending/src/rebalancer/bridges/AcrossBridge.sol](malda-lending/src/rebalancer/bridges/AcrossBridge.sol)
- [malda-lending/src/rebalancer/bridges/BaseBridge.sol](malda-lending/src/rebalancer/bridges/BaseBridge.sol)
- [malda-lending/src/rebalancer/bridges/EverclearBridge.sol](malda-lending/src/rebalancer/bridges/EverclearBridge.sol)
- [malda-lending/src/utils/WrapAndSupply.sol](malda-lending/src/utils/WrapAndSupply.sol)
- [malda-lending/src/verifier/ZkVerifier.sol](malda-lending/src/verifier/ZkVerifier.sol)

[malda-zk-coprocessor @ 51d3095e7f7e3bb3ffcdb115bc4c7271ffc05594](https://github.com/malda-protocol/malda-zk-coprocessor/tree/51d3095e7f7e3bb3ffcdb115bc4c7271ffc05594)
- [malda-zk-coprocessor/malda_rs/src/constants.rs](malda-zk-coprocessor/malda_rs/src/constants.rs)
- [malda-zk-coprocessor/malda_rs/src/elfs_ids.rs](malda-zk-coprocessor/malda_rs/src/elfs_ids.rs)
- [malda-zk-coprocessor/malda_rs/src/lib.rs](malda-zk-coprocessor/malda_rs/src/lib.rs)
- [malda-zk-coprocessor/malda_rs/src/viewcalls.rs](malda-zk-coprocessor/malda_rs/src/viewcalls.rs)
- [malda-zk-coprocessor/malda_utils/src/constants.rs](malda-zk-coprocessor/malda_utils/src/constants.rs)
- [malda-zk-coprocessor/malda_utils/src/cryptography.rs](malda-zk-coprocessor/malda_utils/src/cryptography.rs)
- [malda-zk-coprocessor/malda_utils/src/lib.rs](malda-zk-coprocessor/malda_utils/src/lib.rs)
- [malda-zk-coprocessor/malda_utils/src/types.rs](malda-zk-coprocessor/malda_utils/src/types.rs)
- [malda-zk-coprocessor/malda_utils/src/validators.rs](malda-zk-coprocessor/malda_utils/src/validators.rs)
- [malda-zk-coprocessor/methods/build.rs](malda-zk-coprocessor/methods/build.rs)
- [malda-zk-coprocessor/methods/guest/src/bin/get_proof_data.rs](malda-zk-coprocessor/methods/guest/src/bin/get_proof_data.rs)
- [malda-zk-coprocessor/methods/src/lib.rs](malda-zk-coprocessor/methods/src/lib.rs)


