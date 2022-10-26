# xcm-tools

## Usage

```sh
# calculates the storage key element of a specific EVM address.
ts-node src/calc_address_storagekey.ts -w <ws_endpoint> -a <evm_address>

# calculates the storage key element, XC-20 address and Asset ID of a given asset.
ts-node src/calc_multilocation_info.ts -w <ws_endpoint> -a <asset_multilocation>

# calculates the storage key element, XC-20 address and Asset ID of a given asset
ts-node src/calc_localasset_info.ts -w <ws_endpoint> -a <local_asset_counter>

# calculates the sovereign account of a given parachain Id for the relay chain, and for other parachains.
ts-node src/calc_sovereign_address.ts -r <polkadot|kusama|moonbase> --paraid <parachain-id>

# calculate the units per second to be charged for a given target price (0.02$ per XCM transfer). 
ts-node src/calc_units_per_second.ts -a <coingecko_asset_name kusama/karura/kintsugi> -d <decimals> --xoc <WeighUnitsPerXCMInstruction> --price <asset_price>

# calculate the batched encoded call data to set the units per second for XCM msgs for all supported types.
ts-node src/calc_batch_units_per_second.ts -n <network>

# calculates the multilocaiton-derived address for remote calls through XCM. 
ts-node src/calc_multilocation_derivative.ts -w <target_ws_endpoint> -a <origin_account_address> -p <origin_para_id>

# gets a list of XC-20 assets in the given network. Returns the name, symbol, decimals and token's precompile address.
ts-node src/fetch_xc20_assets.ts -w <ws_endpoint>

# calculates the derivative addres sof a given index
ts-node src/calc_derived_address.ts

# prints the latest finalized block in the provided chain
ts-node src/get_block_finality.ts

# checks if a given Tx Hash has been finalized 
ts-node src/check_tx_finality.ts

# create ECDSA account with Polkadot Keyring
ts-node src/create_ecdsa_acc.ts

# create a number of SR25519 with a given prefix, they are saved into a JSON file
ts-node src/create_sr25519_acc.ts

# show encode and decode functionity for substrate accounts
ts-node src/encode_decode_address.ts

# estimates the transaction fee for a given call
ts-node src/estimate_tx_fee.ts

# prints the private key of a JSON file (DO NOT SHARE YOUR PRIVATE KEY)
ts-node src/get_acc_from_json.ts

# derives the Ethereum address (for a given index) from a mnemonic using the m/44/60/0/0/0 derivation path and logs the associated private key. Also derives the Substrate generic address with the //hard/soft derivation path
ts-node src/get_address_from_mnemonic.ts

# fetches all balance transfer events via the Substrate API
ts-node src/get_balance_events.ts

# gets a substrate block with a given hash
ts-node src/get_block.ts

# retrieve and save in a JSON file all Crowdloan rewards information for a given network
ts-node src/get_crowdloan_cont_address.ts

# shows the Ethereum address associated to a private key
ts-node src/get_eth_address_from_privkey.ts

# fetches all the addresses that are staking and their total in either moonbeam or moonriver (input with yargs like node getStakingAddress.js --network moonbeam)
ts-node src/get_staking_address.ts

# gets staking data from all collators
ts-node src/get_staking_data.ts

# nests as derivative calls to as many levels as desired and provided the encoded call data
ts-node src/nest_as_derivatives.ts

# send a simple tx using the Substrate API, only works with SR25519 accounts (not Moonriver!). You need to provide the origin account mnemonic. Not safe for production!
ts-node src/send_substrate_tx.ts

# verifys a signed message by providing the signers public Address, the message and the signed message
ts-node src/verify_message.ts
```

## Examples

```sh
npm run sovereign -- --paraid 2023 --relay kusama
npm run multilocation -- -n 'moonbeam' -a '{"parents": 1, "interior": {"X2": [{"Parachain": 2007}, {"PalletInstance": 3}]}}'
npm run multilocation -- -n 'moonbeam' -a '{"parents": 1}' # xcDOT
```

## Refs

* <https://github.com/albertov19/PolkaTools>
