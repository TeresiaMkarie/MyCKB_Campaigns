# Build a Simple Lock

**Name**: Teresia Mkarie<br>
**Date**: 3rd-August-2026<br>

## Tasks Completed

- **[Build a Simple Lock](https://docs.nervos.org/docs/dapp/simple-lock)**: Completed the full-stack dApp tutorial covering the ``hash-lock`` toy lock how script args store an expected hash, how the preimage is supplied via `WitnessArgs.lock`, and how CCC builds unlock transactions with `completeInputsByCapacity`, cell deps, and witness injection.
- **[Deploy a custom Lock Script]()**: Built the Script by compiling the contracts using **`pnpm install && pnpm build`**.Deployed the `hash-lock contract`

## Issues During Build

When building the contract I discovered that you need a `CKB degugger` running the environment locally is not only enough.I ran with a code1: ``ckb-debugger:command not Found``<br>
![build error](../pictures/hash_error.png)

## How I Fixed the Issue.

Referenced from -**[Debug with CKB-Debugger](https://docs.nervos.org/docs/script/rust/rust-debug#debug-with-ckb-debugger)** :First, I installed CKB-Debugger using cargo.I learnt that th CKB-Debugger was a powerful standalone command-line tool designed for offchain script development.With the CKB-Debugger, I efficiently identified and resolved issues in my Scripts, ensuring smooth execution.The build was a success!<br>
![build success](../pictures/hashlock_build.png)

### Deployment of the Contract

After Building and Complilation,discovered that the contract files now became available in the ``simple-lock/dist`` directory.Proceeded to deploy the Script binary to the Devnet.
![build success](../pictures/Deployment.png)

## Deployment of the Contracts
### 1.Devnet Deployment

I deployed the script in the devnet network and noticed that the contract files were now available in the `simple-lock/dist directory`.I discovered that i needed to have a pre-funded account to obtain a private key.The `private key` was to be replaced in the environment variables.Before obtaining the private key my devnet deployment ran with an error<br>
![deploy error](../pictures/unfunded_devnet.png)

### *How I fixed the Devnet Deployment Issue

 Obtained private key from pre-funded accounts.Then replaced the private key into my environment variables.Deployment was a success!

### 2.Testnet Deployment

I tried to deploy the Contract in the Testnet Network.Had alot of errors before it finally deployed successfully.

## Issues During Testnet Deployment.

Insufficient Testnet faucets to deploy and no address to be funded.<br>![testnet error](../pictures/testnetIssue.png)

### *How I fixed the Testnet Deployment Issue

1.**[Generate Address for Testnet](https://docs.nervos.org/docs/sdk-and-devtool/rust)**: I Researched on how to obtain a new address for funding from the referrence.Discovered that you need Testnet Faucets for the address generated before deployment.Obtained my faucets at **[Faucets](https://faucet.nervos.org/)** 
2.Changed the devnet variable to testnet in `package.json` under network and in my environment variables.
Testnet Deployment was Built Successful!![Testnet success](../pictures/testnetSuccess.png)

## Deployment of the dApp Frontend.

Finally, I managed to deploy the frontend dApp,Had it running in `localhost:3000` ![Frontend Running](../pictures/frontendport.png)
The frontend was Deployed successful showing the `preimage` &`hash` that was generated.![Frontend Running](../pictures/frontend.png)

## Key Learnings

**1.Lock Script Identity & Addresses**: From the [Build a Simple Lock](https://docs.nervos.org/docs/dapp/simple-lock) tutorial a CKB address is an encoded lock script. When script args change (e.g. a new hash), the address changes entirely. balance is the sum of live cell capacity locked by that script.<br><br>
**2.CKB Address**: The CKB address is just the encoded version of the Lock Script that is computed from the `Lock Script` using the CCC utils `ccc.Address.fromScript`.It acts like a safe deposit box.<br><br>
**3.Hash_Lock Safety of Use**: Learnt that the `hash_lock` is not very secure for guarding the CKB tokens.