# Nervos-CKB Fiber Campaign

**NAME**: Teresia Mkarie<br>
**DATE**: 4th-October-2026<br>

## Tasks Completed
### Quest-One
- **[Connect a Wasm  Node](https://www.fiber.world/docs/build/connect-wasm-node)**<br>Completed the `quest1` that entailed connecting a ` Fiber-WASM` node.Started a  real fiber node then connected it to a fiber Testnet peer.The connection of the node  to the public Fiber Peer Over the `WSS` was succeful showing its runtime state as ready, 1peer Count, node state as running and the node key.<br>
#### 1.Proof of Node Running
![Node Running](ckb_fiberImages\nodestated.png)
#### 2.Proof of successful Inspection 
![](ckb_fiberImages\quest1_inspectedImage.png)

### Quest-Two
- **[Open a Channel and Send Payment](https://www.fiber.world/docs/build/open-channel-payment)**<br>Proceeded to quest2 that entailed `openning a fiber Channel and Sending a Payment`.From the same Browser I used `Connect a Wasm Node`; this was how i achieved quest 2:
#### A.Prepare the Browser Node
This took the most minimum time to start the Wasm and get the Node running.
![Prepare the Browser Node](ckb_fiberImages\quest2_nodeRunning.png)

#### B.Fund The Address
Ran through some errors while trying to fund the address.The peer connection consequently declined running with a `time-out` error as shown below.After many attempts and reloading of the Browser the peer Connection was a success before proceeding to `Open a 499 CKB channel`<br>
![public peer time out](ckb_fiberImages\peer_timeout.png)

#### C.Open a 499 CKB-channel
Openning of the real channel Fiber Testnet Channel was kinda hectic consuming alot of time in the `NEGOTIATING_FUNDING` phase.Even after funding my Testnet Address still remained stuck on this negotiation phase for a longer time(nearly an hour or more).<br>![Negotiating_Funding](ckb_fiberImages\negotiating.png)
##### How I managed to Surpass the Negotiating_Funding Phase.
I tried `npm install` locally from the machine but ran through some security issue that wouldn't allow  me to install the files. Then I discovered that i had some `nervosnetwork/fiber-js` files unistalled so this was the possible reason for the prolonged stuck in the negotiation of funds phase.
![Local Installation Error](ckb_fiberImages\npmInstall_error.png)

##### Fixation of the Delayment
Fixed the Installation Error isssue as shown and later installed the missing Fiber-js file missing 
![Installation_Fix](ckb_fiberImages\installation_Fix.png)<br>

##### Installion of the Missing Fiber-js package
![Fiber-js Installation](ckb_fiberImages\fiber_js.png)

#### Succesful Open a 499 CKB  Channel.
Having fixed the negotiating funding stuck issue the status changed to a number of different status series; Collaborating_Funding Transaction, signing_commitment, awaiting_tx signatures, awaiting chanel ready   to finally Channel_Ready.
##### Proof Of Channel Status
![Channel Status](ckb_fiberImages\channel_status.png)

#### D.Send a  CKB Keysend Payment
After the Channel was successfully on its Ready state, the `send payment` button automatically activated itself allow me to send some ckb to the peer.The send payment was a ssuccess.
![send payment](ckb_fiberImages\send_payment.png)

