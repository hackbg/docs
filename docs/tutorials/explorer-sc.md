---
sidebar_position: 4
---

# Explorer & smart contracts

![OKP4 with Keplr](/img/content/tutorials/explorer-0.webp)

The ability to interact seamlessly with a blockchain is a crucial skill. Whether tracking transactions or executing smart contract messages, having the right tools at your disposal can make all the difference.

That's where the [OKP4 Explorer](https://explore.okp4.network/OKP4%20testnet) comes in. Are you ready to unpack its capabilities? Let's embark on a journey of exploration and discovery into the OKP4 blockchain **🚀**.

## What is the OKP4 Explorer?

An OKP4 blockchain explorer, such as [the OKP4 Explorer](https://explore.okp4.network/OKP4%20testnet), bridges users and the OKP4 network. It's essentially an intuitive interface that allows users to interact with the blockchain.

Think of an explorer as your personal guide to the OKP4 blockchain. It's more than just a viewing platform; you can send transactions, deploy and interact with CosmWasm smart contracts, and even participate in governance.

Watch out for this [list of OKP4 explorers](https://github.com/okp4/awesome#-block-explorers). Anyone can build his own OKP4 blockchain explorer. This means you can tailor an explorer to your specific needs: from your blockchain node, querying it for information and presenting the result in a user-friendly format.

But while building your own explorer is possible, it requires significant time, resources, and technical expertise. Thus you can use [the explorer from the OKP4 team](https://github.com/okp4/ping-explorer), a robust and user-friendly tool powered by [ping.pub](https://ping.pub/).

## Transaction analysis with the OKP4 Explorer

A transaction on the blockchain is a record of some blockchain state change, like the transfer of tokens from one account to another or the execution of a smart contract.

The [OKP4 Explorer](https://explore.okp4.network/OKP4%20testnet) allows you to view and analyze these transactions in detail.
Several transactions are validated in a block. You can check [the last validated blocks](https://explore.okp4.network/OKP4%20testnet/block) via the “Blocks” menu of the explorer. Click on the “Transactions” tab to get the last transactions.

Before moving on to transactions with smart contracts, let's begin with a basic operation: a transfer of $KNOW tokens.

:::info

You need to [set up a wallet with Keplr and own some $KNOW tokens](https://docs.okp4.network/tutorials/keplr-1).

:::

1. Ensure to use the *testnet*  ([https://explore.okp4.network/OKP4 testnet](https://explore.okp4.network/OKP4%20testnet)) and not the *devnet* ([https://explore.okp4.network/OKP4 devnet](https://explore.okp4.network/OKP4%20devnet)).
Link your OKP4 account to the explorer; click on the wallet button (upper on the right), “Connect wallet”, “Keplr”, “Connect” and then on “Approve”.
You'll see your OKP4 wallet address if you click again on the wallet button. Click on it to copy the address.

2. Click on the “Send” button from the Dashboard, and send a few $KNOW tokens to another OKP4 wallet (`okp41r0pf2d78w8w29sm9a6qm8x6yqshezm0k6vwcrg` as the recipient for example). Click on “Send” and “Approve” to confirm the transfer.

<center><img src="/img/content/tutorials/explorer-1.webp"></img></center>

Once completed, click on “View transaction”.

3. Here are what the OKP4 Explorer shows us for [the `Send` transaction details](https://explore.okp4.network/OKP4%20testnet/tx/F50F300F369A5D2428492A439E167C32D4B4F79E61CC40EF39479AA83169CFD5).

- **Transaction Hash:** `F50F300F369A5D2428492A439E167C32D4B4F79E61CC40EF39479AA83169CFD5` as a unique identifier, like a receipt that proves a transaction has occurred.
- **Height**: `2900719` is the block number in which the transaction has been validated.
- **Gas:** Computational effort limit to execute the transaction. Here the spent gas is `76439`. The transaction would have failed if it needed more than `200000`.
- **Fees:** `0.01 KNOW` paid to compensate for the computational effort. The more complex a transaction, the higher the gas and, consequently, the fee. Fees also help prevent spam transactions on the network.
- **@type:** Each message type corresponds to a specific action on the blockchain. For example, a message with `@type` set to `/cosmos.bank.v1beta1.MsgSend` represents a token transfer operation, while a message with `@type` set to `/cosmos.staking.v1beta1.MsgDelegate` represents a delegation operation in the staking module.
- **From and To Addresses:** Unique identifiers for accounts on the blockchain. Tokens are transferred from the sender's address `okp41cu9wzlcyyxpek20jaqfwzu3llzjgx34cwnv2v5` to the recipient's address `okp41r0pf2d78w8w29sm9a6qm8x6yqshezm0k6vwcrg`.
- **Amount**: `0.02 KNOW` sent
- **JSON:** Two main components (`tx` and `tx_response`) which provide insights into the transaction, its execution status and related metadata.

You can also retrieve a transaction you executed by clicking the “Search” button upper on the right, providing your OKP4 address, and clicking “Confirm”. Click on the hash in the “Transactions” section to get the details.

<center><img src="/img/content/tutorials/explorer-2.webp"></img></center>

If you have the transaction hash, you can also directly get transaction details by providing the hash in the Search modal.

## **Interact with smart contracts via the OKP4 Explorer**

A smart contract is a piece of code that runs on blockchain nodes, enabling automated and decentralized execution of programs. There are three types of smart contract interactions with Cosmos-based blockchains like OKP4. The OKP4 Explorer enables one to deal with all these operations:

- **Instantiate:** This is the process of creating a new instance of a smart contract. It requires you to pay gas fees, as it involves computation and storage on the blockchain.
- **Execute:** This is the process of running a smart contract function that changes the state. This could involve transferring tokens, updating variables, or triggering other contracts. Executing a function requires you to pay gas fees.
- **Query:** This is the process of getting data from a smart contract. As it only reads the state, you don't have to pay gas fees when you query a smart contract.

Consider the following smart contracts with the OKP4 blockchain:

- `objectarium`, used to store unstructured data like Prolog programs
- `law-stone`, used to manipulate rules (Prolog programs)
- `cognitarium`, used to store structured data (ontology)

To get all available methods and parameters, you can check the *msg.rs* file of each smart contract from the [OKP4 contracts GitHub repository](https://github.com/okp4/contracts).  For example, you can retrieve [how to instantiate a `cognitarium`](https://github.com/okp4/contracts/blob/572a420d5414a86f31920e420861d0991656230d/contracts/okp4-cognitarium/src/msg.rs#L8C4-L8C4) and its [possible `Execute` messages](https://github.com/okp4/contracts/blob/572a420d5414a86f31920e420861d0991656230d/contracts/okp4-cognitarium/src/msg.rs#L16C1-L17C1).

Below are examples of using a `cognitarium` smart contract. The approach is the same for other smart contracts.

### Instantiate OKP4 smart contracts

Anyone can deploy a new instance. Each smart contract is linked to a specific `CODE_ID`.

|CODE_ID|Smart contract|Description|
|-|-|-|
|4|[`objectarium`](https://github.com/okp4/contracts/tree/main/contracts/okp4-objectarium)|Unstructured object storage|
|5|[`law-stone`](https://github.com/okp4/contracts/tree/main/contracts/okp4-law-stone)|Source of rules|
|7|[`cognitarium`](https://github.com/okp4/contracts/tree/main/contracts/okp4-cognitarium)|Structured object storage, ontology|

Let's create a new database to populate the ontology, with a `cognitarium` smart contract instantiation (`CODE_ID = 7`).

1. Click on the “Cosmwasm” tab to have the list of the available smart contracts. Click on the `CODE HASH` link next to `CODE_ID` `7`.

<center><img src="/img/content/tutorials/explorer-3.webp"></img></center>

2. Click on “Instantiate contract”. Then a modal shows up. You see your OKP4 address in the “Sender” field. Set your OKP4 address as “Admin”, and provide a unique name for the instance in the “Label” field. For the “Messages” field, you can set `{}` if you don't need to specify `limits` regarding store usage, or you can submit a configuration like the following:

```json
{ 
  "limits": {
    "max_triple_count": "1000000",
    "max_byte_size": "1000000000",    
    "max_triple_byte_size": "999999",
    "max_query_limit": 30,
    "max_query_variable_count": 30,
    "max_insert_data_byte_size": "99999900",
    "max_insert_data_triple_count": "10000"
  }
}
```

Then click “Send” and “Approve” when the Keplr window appears.

<center><img src="/img/content/tutorials/explorer-4.webp"></img></center>

3. Click on “View transaction” once executed to see all instantiation details. The transaction response from the JSON section gives you the resulting contract address. `okp41rprnv4g92cwhjsr226hkxzysxcsjgeh3llw0ps4wpuwsky4w38fq2gpy7z` is the instantiated address from [the `Instantiate` transaction](https://explore.okp4.network/OKP4%20testnet/tx/D132548E38BF942CEC242E1D380BC385335C4DC80DF68AEA37625C9C404A804E).

<center><img src="/img/content/tutorials/explorer-5.webp"></img></center>

If there is an error ([transaction failed](https://explore.okp4.network/OKP4%20testnet/tx/5A6538E7C127A7A8AEA86BD109FD21832365998AD8BC61ECCA980EBF16DC22D0)),  the `raw_log` in the transaction response from the JSON section gives the error message.

4. The instantiated contract appears in the [contract list of `CODE_ID = 7`](https://explore.okp4.network/OKP4%20testnet/cosmwasm/7/contracts). We can see the `okp41rprnv4g92cwhjsr226hkxzysxcsjgeh3llw0ps4wpuwsky4w38fq2gpy7z` address:

<center><img src="/img/content/tutorials/explorer-6.webp"></img></center>

### Use an OKP4 smart contract to execute messages

Let's insert [these RDF triples](https://github.com/okp4/ontology/blob/d3209eb9395a0292927627004e5114b63bf3cab0/example/rhizome/dataset/0ea1fc7a-dd97-4adc-a10e-169c6597bcde.ttl), to reference an Excel dataset in the ontology. You can only add it in a `cognitarium` contract you instantiated.

1. The Turtle file data should be encoded in base64. You can use an [online tool](https://www.base64encode.org/), or you can use your terminal:

```bash
curl -s https://raw.githubusercontent.com/okp4/ontology/d3209eb9395a0292927627004e5114b63bf3cab0/example/rhizome/dataset/0ea1fc7a-dd97-4adc-a10e-169c6597bcde.ttl | base64 | tr -d '\n\r'
```

2. Click on the “Execute” button for the `cognitarium` previously instantiated. Copy and paste the encoded data in the “Messages” field, following this JSON structure:

```json
{
  "insert_data": {
    "data": "QHByZWZpeCBhcmVhOiA8aHR0cHM6Ly9vbnRvbG9neS5va3A0LnNwYWNlL3RoZXNhdXJ1cy9hcmVhLz4gLgpAcHJlZml4IGNvcmU6IDxodHRwczovL29udG9sb2d5Lm9rcDQuc3BhY2UvY29yZS8+IC4KQHByZWZpeCBkYXRhc2V0OiA8aHR0cHM6Ly9vbnRvbG9neS5va3A0LnNwYWNlL2RhdGF2ZXJzZS9kYXRhc2V0Lz4gLgpAcHJlZml4IGRzdG1ldGE6IDxodHRwczovL29udG9sb2d5Lm9rcDQuc3BhY2UvZGF0YXZlcnNlL2RhdGFzZXQvbWV0YWRhdGEvPiAuCkBwcmVmaXggbGljZW5zZTogPGh0dHBzOi8vb250b2xvZ3kub2twNC5zcGFjZS90aGVzYXVydXMvbGljZW5zZS8+IC4KQHByZWZpeCBtZWRpYXR5cGU6IDxodHRwczovL29udG9sb2d5Lm9rcDQuc3BhY2UvdGhlc2F1cnVzL21lZGlhLXR5cGUvPiAuCkBwcmVmaXggbWV0YTogPGh0dHBzOi8vb250b2xvZ3kub2twNC5zcGFjZS9tZXRhZGF0YS8+IC4KQHByZWZpeCBtZXRhZHN0OiA8aHR0cHM6Ly9vbnRvbG9neS5va3A0LnNwYWNlL21ldGFkYXRhL2RhdGFzZXQvPiAuCkBwcmVmaXggb3dsOiA8aHR0cDovL3d3dy53My5vcmcvMjAwMi8wNy9vd2wjPiAuCkBwcmVmaXggc2VydmljZTogPGh0dHBzOi8vb250b2xvZ3kub2twNC5zcGFjZS9kYXRhdmVyc2Uvc2VydmljZS8+IC4KQHByZWZpeCB0b3BpYzogPGh0dHBzOi8vb250b2xvZ3kub2twNC5zcGFjZS90aGVzYXVydXMvdG9waWMvPiAuCkBwcmVmaXggeHNkOiA8aHR0cDovL3d3dy53My5vcmcvMjAwMS9YTUxTY2hlbWEjPiAuCgpkc3RtZXRhOmQxNjE1NzAzLTRlZTEtNGUyZi05OTdlLTE1YWVjZjFlZWE0ZSBhIG93bDpOYW1lZEluZGl2aWR1YWwsCiAgICAgICAgbWV0YWRzdDpHZW5lcmFsTWV0YWRhdGEgOwogICAgY29yZTpkZXNjcmliZXMgZGF0YXNldDowZWExZmM3YS1kZDk3LTRhZGMtYTEwZS0xNjljNjU5N2JjZGUgOwogICAgY29yZTpoYXNDcmVhdG9yICJBbnNlcyIgOwogICAgY29yZTpoYXNEZXNjcmlwdGlvbiAiQXZlYyAzMTg1IGFsaW1lbnRzIHLDqWbDqXJlbmPDqXMsIGNldHRlIG5vdXZlbGxlIHZlcnNpb24gZGUgbGEgdGFibGUgQ2lxdWFsIGludMOoZ3JlIGxlIGTDqXRhaWwgZGUgdG91cyBsZXMgc3VjcmVzIGluZGl2aWR1ZWxzIGNvbnRlbnVzIGRhbnMgbGVzIGFsaW1lbnRzLiBFbGxlIHByb3Bvc2Ugw6lnYWxlbWVudCBkZXMgZG9ubsOpZXMgYWN0dWFsaXPDqWVzIHN1ciBsZXMgcHJpbmNpcGF1eCBmcnVpdHMgZXQgbMOpZ3VtZXMsIHkgY29tcHJpcyBjZXV4IGN1bHRpdsOpcyBlbiBPdXRyZS1tZXIuIFBvdXIgw6p0cmUgZW4gYWTDqXF1YXRpb24gYXZlYyBsZXMgbm91dmVsbGVzIHByYXRpcXVlcyBhbGltZW50YWlyZXMgZGVzIGZyYW7Dp2FpcywgbGEgdGFibGUgaW5jbHV0IGTDqXNvcm1haXMgdW5lIGNpbnF1YW50YWluZSBkZSBub3V2ZWF1eCBhbGltZW50cyBhZGFwdMOpcyBhdXggcsOpZ2ltZXMgdsOpZ8OpdGFyaWVucy4iQGZyIDsKICAgIGNvcmU6aGFzRGVzY3JpcHRpb24gIldpdGggMywxODUgZm9vZHMgcmVmZXJlbmNlZCwgdGhpcyBuZXcgdmVyc2lvbiBvZiB0aGUgQ2lxdWFsIHRhYmxlIGluY2x1ZGVzIGRldGFpbHMgb2YgYWxsIGluZGl2aWR1YWwgc3VnYXJzIGNvbnRhaW5lZCBpbiBmb29kcy4gSXQgYWxzbyBwcm92aWRlcyB1cGRhdGVkIGRhdGEgb24gdGhlIG1haW4gZnJ1aXRzIGFuZCB2ZWdldGFibGVzLCBpbmNsdWRpbmcgdGhvc2UgZ3Jvd24gaW4gdGhlIEZyZW5jaCBvdmVyc2VhcyB0ZXJyaXRvcmllcy4gVG8ga2VlcCB1cCB3aXRoIHRoZSBuZXcgZWF0aW5nIGhhYml0cyBvZiB0aGUgRnJlbmNoLCB0aGUgdGFibGUgbm93IGluY2x1ZGVzIGFyb3VuZCBmaWZ0eSBuZXcgZm9vZHMgYWRhcHRlZCB0byB2ZWdldGFyaWFuIGRpZXRzLiJAZW4gOwogICAgY29yZTpoYXNEZXNjcmlwdGlvbiAiRGllIG5ldWUgVmVyc2lvbiBkZXIgQ2lxdWFsLVRhYmVsbGUgZW50aMOkbHQgMzE4NSBMZWJlbnNtaXR0ZWwgdW5kIGRldGFpbGxpZXJ0ZSBBbmdhYmVuIHp1IGFsbGVuIGluIGRlbiBMZWJlbnNtaXR0ZWxuIGVudGhhbHRlbmVuIGluZGl2aWR1ZWxsZW4gWnVja2Vybi4gQXXDn2VyZGVtIGVudGjDpGx0IHNpZSBha3R1YWxpc2llcnRlIERhdGVuIHp1IGRlbiB3aWNodGlnc3RlbiBPYnN0LSB1bmQgR2Vtw7xzZXNvcnRlbiwgZWluc2NobGllw59saWNoIGRlciBpbiDDnGJlcnNlZSBhbmdlYmF1dGVuIFNvcnRlbi4gVW0gZGVuIG5ldWVuIEVzc2dld29obmhlaXRlbiBkZXIgRnJhbnpvc2VuIGdlcmVjaHQgenUgd2VyZGVuLCBlbnRow6RsdCBkaWUgVGFiZWxsZSBudW4gcnVuZCA1MCBuZXVlIExlYmVuc21pdHRlbCwgZGllIGbDvHIgdmVnZXRhcmlzY2hlIEVybsOkaHJ1bmcgZ2VlaWduZXQgc2luZC4iQGRlIDsKICAgIGNvcmU6aGFzRm9ybWF0IG1lZGlhdHlwZTphcHBsaWNhdGlvbl92bmRtcy1leGNlbCA7CiAgICBjb3JlOmhhc0ltYWdlIDxodHRwczovL21lZGlhLmlzdG9ja3Bob3RvLmNvbS92ZWN0b3JzL3ZlY3Rvci1kYXRhYmFzZS1pY29uLXZlY3Rvci1pZDg4NjcyOTU2OD9rPTYmbT04ODY3Mjk1Njgmcz0xNzA2NjdhJnc9MCZoPWVGT0g1NmNmTW5vRksyTnRYNkJTZV9BYUl5WVdGVUs0RkN1bUlncE1VWTg9PiA7CiAgICBjb3JlOmhhc0xpY2Vuc2UgbGljZW5zZTpMTy1GUi0xXzAgOwogICAgY29yZTpoYXNQdWJsaXNoZXIgIk9LUDQiIDsKICAgIGNvcmU6aGFzU3BhdGlhbENvdmVyYWdlIGFyZWE6MjUwIDsKICAgIGNvcmU6aGFzVGFnICJhbGltZW50YXRpb24taHVtYWluZSIsCiAgICAgICAgImFsaW1lbnRzIiwKICAgICAgICAiY29tcG9zaXRpb24tZGVzLWFsaW1lbnRzIiA7CiAgICBjb3JlOmhhc1RpdGxlICJUYWJsZSBkZSBjb21wb3NpdGlvbiBudXRyaXRpb25uZWxsZSBkZXMgYWxpbWVudHMgQ2lxdWFsIDIwMjAiQGZyIDsKICAgIGNvcmU6aGFzVGl0bGUgIk51dHJpdGlvbmFsIGNvbXBvc2l0aW9uIHRhYmxlIGZvciBDaXF1YWwgMjAyMCBmb29kcyJAZW4gOwogICAgY29yZTpoYXNUaXRsZSAiVGFiZWxsZSBkZXIgTsOkaHJzdG9mZnp1c2FtbWVuc2V0enVuZyB2b24gTGViZW5zbWl0dGVsbiBDaXF1YWwgMjAyMCJAZGUgOwogICAgY29yZTpoYXNUb3BpYyB0b3BpYzpBZ3JpY3VsdHVyZUZvb2RFbnZpcm9ubWVudEFuZEZvcmVzdHJ5IC4KCmRzdG1ldGE6MTU1OTJmZDQtZTM2OC00NmQzLWIxMTMtNWQwZWY4ZDRkMTBmIGEgb3dsOk5hbWVkSW5kaXZpZHVhbCwKICAgICAgICBtZXRhOkF1ZGl0TWV0YWRhdGEgOwogICAgY29yZTpjcmVhdGVkQnkgPGRpZDprZXk6MHgwNGQxZjFiOGY4YTdhMjhmOWE1YTI1NGMzMjZhOTYzYTIyZjVhNWI1ZDVmNWU1ZDVjNWI1YTU5NTg1NzU2NTU+IDsKICAgIGNvcmU6Y3JlYXRlZE9uICIyMDIzLTAzLTI4VDAwOjAwOjAwKzAwOjAwIl5eeHNkOmRhdGVUaW1lIDsKICAgIGNvcmU6ZGVzY3JpYmVzIGRhdGFzZXQ6MGVhMWZjN2EtZGQ5Ny00YWRjLWExMGUtMTY5YzY1OTdiY2RlIDsKICAgIGNvcmU6bGFzdE1vZGlmaWVkQnkgPGRpZDprZXk6MHgwNGQxZjFiOGY4YTdhMjhmOWE1YTI1NGMzMjZhOTYzYTIyZjVhNWI1ZDVmNWU1ZDVjNWI1YTU5NTg1NzU2NTU+IDsKICAgIGNvcmU6dXBkYXRlZE9uICIyMDIzLTAzLTI4VDAwOjAwOjAwKzAwOjAwIl5eeHNkOmRhdGVUaW1lIC4KCmRhdGFzZXQ6MGVhMWZjN2EtZGQ5Ny00YWRjLWExMGUtMTY5YzY1OTdiY2RlIGEgb3dsOk5hbWVkSW5kaXZpZHVhbCwKICAgICAgICBjb3JlOkRhdGFzZXQgOwogICAgY29yZTpoYXNJZGVudGlmaWVyIDx1cm46dXVpZDowZWExZmM3YS1kZDk3LTRhZGMtYTEwZS0xNjljNjU5N2JjZGU+IDsKICAgIGNvcmU6aGFzUmVnaXN0cmFyIDxkaWQ6a2V5OjB4MDRkMWYxYjhmOGE3YTI4ZjlhNWEyNTRjMzI2YTk2M2EyMmY1YTViNWQ1ZjVlNWQ1YzViNWE1OTU4NTc1NjU1PiA7CiAgICBjb3JlOnByb3ZpZGVkQnkgc2VydmljZTpkMWIwYjRkMy1mOWE2LTQxMTUtYmNkOC1hZDk3MjMzYTdiMDggLgo="
  }
}
```

The default value of “Gas” would not be enough to cover this transaction cost. Click on “Advance” and set `2000000`.  You can also set a `Memo` below. Click on “Send”, then “Approve”.

<center><img src="/img/content/tutorials/explorer-7.webp"></img></center>

3. Click on “View transaction” once executed to see all insertion details. Thus you can check [the `InsertData` transaction](https://explore.okp4.network/OKP4%20testnet/tx/953EB5C7786862F8239D0CD4629738D5C273DE9ECCE3E15D0A4EEBFED98E4328) added 31 triples.

<center><img src="/img/content/tutorials/explorer-8.webp"></img></center>

### Query an OKP4 smart contract

Let's retrieve [the `GeneralMetadata` identifier](https://github.com/okp4/ontology/blob/d3209eb9395a0292927627004e5114b63bf3cab0/example/rhizome/dataset/0ea1fc7a-dd97-4adc-a10e-169c6597bcde.ttl#L14) previously stored.  

1. Click on the “Query” button of the `cognitarium` instance you used to insert data. Click on “Smart query”. Copy-paste this `Select` query:

```json
{
  "select": {
    "query": {
      "select": [
        {
          "variable": "metadataid"
        }
      ],
      "prefixes": [
        {
          "prefix": "core",
          "namespace": "https://ontology.okp4.space/core/"
        },
        {
          "prefix": "dataset",
          "namespace": "https://ontology.okp4.space/dataverse/dataset/"
        },
        {
          "prefix": "metadst",
          "namespace": "https://ontology.okp4.space/metadata/dataset/"
        }
      ],
      "limit": 2,
      "where": [
        {
          "simple": {
            "triple_pattern": {
              "subject": {
                "variable": "metadataid"
              },
              "predicate": {
                "node": {
                  "named_node": {
                    "prefixed": "core:describes"
                  }
                }
              },
              "object": {
                "node": {
                  "named_node": {
                    "prefixed": "dataset:0ea1fc7a-dd97-4adc-a10e-169c6597bcde"
                  }
                }
              }
            }
          }
        },
        {
          "simple": {
            "triple_pattern": {
              "subject": {
                "variable": "metadataid"
              },
              "predicate": {
                "node": {
                  "named_node": {
                    "full": "http://www.w3.org/1999/02/22-rdf-syntax-ns#type"
                  }
                }
              },
              "object": {
                "node": {
                  "named_node": {
                    "prefixed": "metadst:GeneralMetadata"
                  }
                }
              }
            }
          }
        }
      ]
    }
  }
}
```

2. Click on “Query contract”. You should get a JSON with `https://ontology.okp4.space/dataverse/dataset/metadata/d1615703-4ee1-4e2f-997e-15aecf1eea4e` bound to the variable `metadataid` as a result.

<center><img src="/img/content/tutorials/explorer-9.webp"></img></center>

## Recap'

- You can check any blockchain transaction details with an explorer.
- Transfer, delegation and governance operations are also possible with this type of user interface.
- You can **instantiate** (deploy from code), **execute** a message (which modifies the blockchain state) and **query** (read request) a smart contract with the [OKP4 Explorer](https://explore.okp4.network/OKP4%20testnet). No need to [use your terminal with the CLI](https://docs.okp4.network/tutorials/cli-1), and you can more easily analyze transaction results.

Explorers are powerful tools that allow you to interact with the OKP4 blockchain in a user-friendly way. Whether you're a developer looking to deploy and test smart contracts, or an end-user wanting to verify transactions, the OKP4 Explorer has you covered. So why wait? Start exploring the OKP4 network today!
