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
```

## Examples

```sh
npm run sovereign -- --paraid 2023 --relay kusama
npm run multilocation -- -n 'moonbeam' -a '{"parents": 1, "interior": {"X2": [{"Parachain": 2007}, {"PalletInstance": 3}]}}'
npm run multilocation -- -n 'moonbeam' -a '{"parents": 1}' # xcDOT
```

## Refs

* <https://github.com/albertov19/PolkaTools>
