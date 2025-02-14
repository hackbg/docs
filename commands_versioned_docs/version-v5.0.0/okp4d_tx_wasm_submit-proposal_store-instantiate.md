## okp4d tx wasm submit-proposal store-instantiate

Submit and instantiate a wasm contract proposal

```
okp4d tx wasm submit-proposal store-instantiate [wasm file] [json_encoded_init_args] --authority [address] --label [text] --title [text] --summary [text]--unpin-code [unpin_code,optional] --source [source,optional] --builder [builder,optional] --code-hash [code_hash,optional] --admin [address,optional] --amount [coins,optional] [flags]
```

### Options

```
  -a, --account-number uint                   The account number of the signing account (offline mode only)
      --admin string                          Address or key name of an admin
      --amount string                         Coins to send to the contract during instantiation
      --authority string                      The address of the governance account. Default is the sdk gov module account (default "okp410d07y265gmmuvt4z0w9aw880jnsr700jh7kd2g")
      --aux                                   Generate aux signer data instead of sending a tx
  -b, --broadcast-mode string                 Transaction broadcasting mode (sync|async) (default "sync")
      --builder string                        Builder is a valid docker image name with tag, such as "cosmwasm/workspace-optimizer:0.12.9"
      --chain-id string                       The network chain ID (default "okp4d")
      --code-hash bytesHex                    CodeHash is the sha256 hash of the wasm code
      --code-source-url string                Code Source URL is a valid absolute HTTPS URI to the contract's source code,
      --deposit string                        Deposit of proposal
      --dry-run                               ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it (when enabled, the local Keybase is not accessible)
      --fee-granter string                    Fee granter grants fees for the transaction
      --fee-payer string                      Fee payer pays fees for the transaction instead of deducting from the signer
      --fees string                           Fees to pay along with transaction; eg: 10uatom
      --from string                           Name or address of private key with which to sign
      --gas string                            gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically. Note: "auto" option doesn't always report accurate results. Set a valid coin value to adjust the result. Can be used instead of "fees". (default 200000)
      --gas-adjustment float                  adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
      --gas-prices string                     Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
      --generate-only                         Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase only accessed when providing a key name)
  -h, --help                                  help for store-instantiate
      --instantiate-anyof-addresses strings   Any of the addresses can instantiate a contract from the code, optional
      --instantiate-everybody string          Everybody can instantiate a contract from the code, optional
      --instantiate-nobody string             Nobody except the governance process can instantiate a contract from the code, optional
      --instantiate-only-address string       Removed: use instantiate-anyof-addresses instead
      --keyring-backend string                Select keyring's backend (os|file|kwallet|pass|test|memory) (default "test")
      --keyring-dir string                    The client Keyring directory; if omitted, the default 'home' directory will be used
      --label string                          A human-readable name for this contract in lists
      --ledger                                Use a connected Ledger device
      --no-admin                              You must set this explicitly if you don't want an admin
      --node string                           &lt;host&gt;:&lt;port&gt; to tendermint rpc interface for this chain (default "tcp://localhost:26657")
      --note string                           Note to add a description to the transaction (previously --memo)
      --offline                               Offline mode (does not allow any online functionality)
  -o, --output string                         Output format (text|json) (default "json")
  -s, --sequence uint                         The sequence number of the signing account (offline mode only)
      --sign-mode string                      Choose sign mode (direct|amino-json|direct-aux), this is an advanced feature
      --summary string                        Summary of proposal
      --timeout-height uint                   Set a block timeout height to prevent the tx from being committed past a certain height
      --tip string                            Tip is the amount that is going to be transferred to the fee payer on the target chain. This flag is only valid when used with --aux, and is ignored if the target chain didn't enable the TipDecorator
      --title string                          Title of proposal
      --unpin-code                            Unpin code on upload, optional
  -y, --yes                                   Skip tx broadcasting prompt confirmation
```

### SEE ALSO

* [okp4d tx wasm submit-proposal](okp4d_tx_wasm_submit-proposal.md)	 - Submit a wasm proposal.
