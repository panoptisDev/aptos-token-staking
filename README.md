Candy machine smart contract for Aptos Blockchain.

# Deploy contract

```
aptos init

```
# Test

``` 
aptos move test 
```
# Publish

```
 aptos move publish --named-addresses mokshyastaking::tokenstaking=your_address
```
Copy the account address and replace in tests/staking.ts
# Set Up
```javascript
import {AptosClient, AptosAccount, FaucetClient, TxnBuilderTypes} from "aptos";

const NODE_URL = "https://fullnode.devnet.aptoslabs.com";
const FAUCET_URL = "https://faucet.devnet.aptoslabs.com";
// Creator Account
const account1 = new AptosAccount();
// Staker Account
const account2 = new AptosAccount();
```
# Create Staking
```javascript
const create_staking_payloads = {
      type: "entry_function_payload",
      function: "0xf40bb98bf343e6c091af235e2e4b1953b38919f266ce10a091dfeae8b06f3f9e::tokenstaking::create_staking",
      type_arguments: ["0x1::aptos_coin::AptosCoin"],
      arguments: [BigInt(1),collection,BigInt(10)
      ],
    };
    let txnRequest = await client.generateTransaction(account1.address(), create_staking_payloads);
    let bcsTxn = AptosClient.generateBCSTransaction(account1, txnRequest);
    await client.submitSignedBCSTransaction(bcsTxn);

```
# Stake Token
```javascript
 const create_staking_payloads = {
      type: "entry_function_payload",
      function: "0xf40bb98bf343e6c091af235e2e4b1953b38919f266ce10a091dfeae8b06f3f9e::tokenstaking::stake_token",
      type_arguments: [],
      arguments: [account1.address(),collection,tokenname,tokenPropertyVersion,BigInt(1)
      ],
    };
    let txnRequest = await client.generateTransaction(account2.address(), create_staking_payloads);
    let bcsTxn = AptosClient.generateBCSTransaction(account2, txnRequest);
    await client.submitSignedBCSTransaction(bcsTxn);
```
# Claim Reward
```javascript
 const create_staking_payloads = {
      type: "entry_function_payload",
      function: "0xf40bb98bf343e6c091af235e2e4b1953b38919f266ce10a091dfeae8b06f3f9e::tokenstaking::claim_reward",
      type_arguments: ["0x1::aptos_coin::AptosCoin"],
      arguments: [collection,tokenname,account1.address()
      ],
    };
    let txnRequest = await client.generateTransaction(account2.address(), create_staking_payloads);
    let bcsTxn = AptosClient.generateBCSTransaction(account2, txnRequest);
    await client.submitSignedBCSTransaction(bcsTxn);
```
# Unstake Token
```javascript
const create_staking_payloads = {
      type: "entry_function_payload",
      function: "0xf40bb98bf343e6c091af235e2e4b1953b38919f266ce10a091dfeae8b06f3f9e::tokenstaking::unstake_token",
      type_arguments: ["0x1::aptos_coin::AptosCoin"],
      arguments: [account1.address(),collection,tokenname,tokenPropertyVersion,1
      ],
    };
    let txnRequest = await client.generateTransaction(account2.address(), create_staking_payloads);
    let bcsTxn = AptosClient.generateBCSTransaction(account2, txnRequest);
    await client.submitSignedBCSTransaction(bcsTxn);

```