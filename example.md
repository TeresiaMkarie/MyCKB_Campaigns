cat > README.md << 'EOF'
# Paying Someone I Share No Channel With: A Fiber Multi-Hop Run

By Teresia

I ran two independent Fiber nodes in my browser, sent 1 CKB from one to the other through Bottle (a public node neither of them is connected to the other through), then sent it back the other way. This README is my account of how it went, what I saw, and what I would tell the next person.

## The short version

- Sender A and Receiver C never opened a channel with each other.
- Both opened a channel with Bottle B instead (499 CKB each).
- A paid a 1 CKB invoice created by C, routed A -> B -> C.
- Then C paid 1 CKB back to A, using the same two channels.
- I used: [hosted demo / local project, pick one]

## Proof

| What | Link or file |
|---|---|
| Quest 1: Payment completed + invoice Paid | screenshots/quest1-paid.png |
| Quest 2: liquidity bars BEFORE return payment | screenshots/quest2-before.png |
| Quest 2: liquidity bars AFTER return payment | screenshots/quest2-after.png |
| Channel A <-> Bottle (CHANNEL_READY) | [FILL IN: screenshot or tx link] |
| Channel C <-> Bottle (CHANNEL_READY) | [FILL IN: screenshot or tx link] |

## How it went, step by step

**Setting up the nodes.** [FILL IN: did you reuse saved nodes or start fresh? Any wait on faucet funds?] I treated A and C as two separate people. Different node, different funds, different view of the world.

**Opening channels.** Each node opened a public channel with Bottle using the preset 499 CKB. I kept a little extra on-chain CKB aside for fees. [FILL IN: how long until CHANNEL_READY, and anything you noticed while waiting.]

**Checking liquidity before paying.** Before creating any invoice, I looked at the maximum invoice the route supported. [FILL IN: the number you saw.] This matters because a route is only as strong as its weakest hop. You can have plenty of money on your side and still be unable to pay, if the next hop cannot pass it along.

**Quest 1, the payment.** C created a 1 CKB invoice. On A, I reviewed the amount and the maximum routing fee before sending. [FILL IN: the max fee shown.] Result: Payment completed, invoice status Paid.

**Quest 2, sending it back.** I used Create another invoice to return to that step, took the screenshot of both liquidity bars first, then opened Restore receiving liquidity. I replaced the suggested amount with 1 CKB, checked the maximum return supported it, reviewed the fee allowance, and sent it back to A.

## What the liquidity bars showed

[FILL IN with your real numbers]

| | A <-> Bottle | Bottle <-> C |
|---|---|---|
| Before Quest 1 | | |
| After Quest 1 | | |
| After Quest 2 | | |

The thing I found most useful to see: a payment does not create or destroy money in a channel, it shifts balance from one side to the other. Quest 1 moved balance toward C. Quest 2 moved some back, which is why it is called restoring receiving liquidity. It also cost a small routing fee, so I did not end up exactly where I started. [FILL IN: the actual difference you measured.]

## What surprised me

[FILL IN: 2 or 3 honest points. Examples of the kind of thing worth writing: how fast or slow the channels became ready, how the fee allowance compared to the fee actually charged, how obvious or unobvious the liquidity direction was at first.]

## Things I would tell the next person

- Keep the payment small. 1 CKB is plenty to prove the flow.
- If you see insufficient liquidity, look at the channel amounts first. Saved channels carry history from earlier payments.
- The hosted demo and a local run use separate browser storage. Your nodes will not carry across, so pick one and stay with it.
- Take the "before" screenshot before you click anything in Quest 2. You cannot go back and capture it afterwards.

## Mistakes and fixes

[FILL IN: anything that went wrong and how you solved it. Even one small stumble makes the write-up more believable and more useful.]

## Why this is worth caring about

Without routing through an intermediary, every pair of people who want to pay each other would need their own channel, which means locking up funds and paying on-chain fees each time. With a hub like Bottle, you open one channel and can reach anyone else connected to it. That is the whole idea, and doing it by hand with two nodes made it click for me in a way reading about it did not.
EOF