# Send a Multi-Hop Invoice Payment

**Name**: Teresia Mkarie<br>
**Date**: 30th-10-2026 <br>

I ran two independent Fiber nodes in my browser, sent 1 CKB from one to the other through Bottle (a public intermediary node neither of them is connected to the other through), then sent it back the other way. 

## Quest One: A Fiber Multi-Hop Run
Entails paying someone I share No Channel with.Multi-hop payments let one send assets to anyone in the Fiber Network without opening a direct channel.The sender computes a route through intermediate nodes which forward the payment automatically in exchange for  a small fee.

## How the Multi-Hop Operated
- Sender A and Receiver C never opened a channel with each other.
- Both opened a channel with Bottle B instead 
- Sender A paid a 1 CKB invoice created by C, routed A -> B -> C.

## The Payment Flow
In Fiber, a multi-hop payment takes place through four phases: `pathfinding`, `onion construction`, `hop-by-hop forwarding` and settlement.As referrenced from [Multi-Hop Routing](https://www.fiber.world/docs/concept/routing/multi-hop#the-payment-flow).

**Pathfinding.** My node checks its map of the network and picks a route with low fees and enough liquidity.

**Onion construction.** The sender wraps each hop's instructions in its own layer of encryption, so every node only sees its neighbors.

**Hop-by-hop Forwarding.** The payment plus fees is locked in a time-locked contract at each hop, with shorter deadlines as it moves along.

**Settlement.** The recipient reveals a secret that unlocks each contract on the way back, and each relay keeps its small fee.
## Proofs for The Multi-Hop Invoice Payment.
### 1.Setup Sender and Receiver.
I reused my saved nodes, so there was no fresh  setup.Waited for the nodes to be running.I treated `Sender A` and `Receiver C` as two separate entities, each with its own node and funds.
![Prepare the Browser Node](Campaign7\step1.png)

### 2.Waiting For Channel State && Funding Testnet Address.
I waited for the channel state to show `Channel_Ready`, then proceeded to funding the Testnet address with Testnet CKB from [CKB_Faucets](https://faucet.nervos.org/).
![Awaiting Channel State](Campaign7\step2.png)

### 3.Channel_Ready
Before creating the Invoice, I waited until both the `A-B` and `C-B` Channels showed `CHANNEL-READY,checked the Liquidity bars which showed that on the A to Bottle B, Outbound from A was `400CKB`and Inbound to A was `151CKB`. On the Bottle B to C bar,Inbound to C was `151CKB` and outbound from C was `400CKB`. Sender A could send up to 400CKB,but onlyy 151CKB sat on Bottle B to C.
![Channel_Ready State](Campaign7\step3.png)


### 4.Invoice Created && Payment is Pending
Receiver C created a 1 CKB invoice with the payment flow showing **Sender A -> Bottle B-> Receiver C** and the Invoice status to be open with the page showing a `Payment Pending`.
![Pending Payment](Campaign7\step4.png)

### 5.Payment Completed Successfully
The payment went through successfully.The page showed Payment completed, 1 CKB received by C, and the invoice flipped from`Open` to `Paid`. The routing fee came out at 0.005 CKB against a 1 CKB maximum.
![Payment Completed](Campaign7\step5.png)

## Quest Two: Restore Receiving Liquidity.
### 1.Restore Receiving Liquidity.
I returned to the `Create Invoice` button then using the `Create another Invoice` i opened the `Restore Receiving liquidity` set my return amount to 1CKB,reviewed the routing-fee allowance before sending it back to A.
![Restoring Receiving Liquidity](Campaign7\step6.png)

## What the liquidity bars showed.
When I opened the `Restore Liquidity` button,i realised the liquidity bars for reversing the payment direction was abit different. The outbound from `A` had dropped from `400CKB to 397.975CKB`.The reverse payment increases Bottle’s liquidity toward C, allowing C to receive more payments.This moves existing funds and incur routing fees. The Inbound to A now registered an increase to `153.025CKB`.Inbound to C became `149.015CKB` while the outbound from C became `401.985CKB`. 

### 2.Liquidity Restored && 1CKB Received by A
![Liquidity Restored](Campaign7\step7.png)

## Key-Learning
### 1.How The Available Liquidity is calculated
- I learnt that a new channel funded with 499 CKB will normally reserve 99 CKB for on-chain settlement, leaving 400 CKB for payments before transfers and fees. Another 1 CKB is reserved for the maximum routing fee.
### 2.Fiber Liqudity
- Fiber uses payment channels to move value off-chain frequently and at a very low cost.Once the channel is openned, assets are locked in the channel.Liquidity is essential when building Fiber wallets,payment-acceptance applications, routing nodes, and payment services. <br>
- I learnt that Fiber does not require the sender and recipient to share a direct channel. A payment can pass through one or more intermediate nodes so long as their is a path with correct direction and enough capacity for the network.
### 3.Invoice
- I learnt that an invoice is a payment request generated by a recipient in the Fiber network which encodes everything a sender needs to make a payment.Every Fiber Invoice carries a Currency core field whose Network identifier uses the `bech32m` encoding `fibb`(mainnet), `fibt`(testnet) or `fibd`(devnet)
### 4.Multi-Hop Payments
- I learnt that multi-hop payments allow one to send assets to anyone within the Fiber Network without opening a direct channel.The sender computes a route through intermediate nodes, wraps the routing instructions in layers of onion encryption and locks each hop with a time-locked contract(TLC).

