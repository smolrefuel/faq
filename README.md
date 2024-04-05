# FAQ
#### I got the error "nonce too low"
It's likely your tx got accepted and your swap has been completed, switch chain to original mainnet and check your wallet!

#### I can't make any txs after switching RPC and approving tx
You need to go to metamask settings > Advanced > Click on "Clear activity tab data"

#### I got the error "nonce too high"
It's because you already sent an approval tx before that didn't go through

To solve this, go to metamask settings > Advanced > Click on "Clear activity tab data", and afterwards restart the process from the beginning

#### I got the error " max fee per gas less than block base fee"
You need to modify max fee to increase it much more, for example you can set it to 100 or 200 gwei. Remember to keep priority fee low tho! It should be 0-3 gwei.

Most of the max fee will not be used since it'll only use up to the block base fee, so don't worry about setting a high number there.

#### I got the error "execution reverted"
There are multiple possible reasons for this:
- The amount of tokens you are trying to swap is too low and doesn't cover the cost of the swap. Solve it by increasing amount
- Token has a tax or some other mechanism that isn't supported by paraswap. No solution for this, try another token.
- Token just cant be swapped, eg it was a honeypot... smolrefuel can't do miracles, if your token cant be swapped then we cant swap it either

#### I've been waiting for some time and swap is not going through
Swap can take up to 30 minutes to go through, this is because we are constantly submitting the bundle to flashbots where it competes with other bundles from MEV activity, so it needs to wait for a block with low competition to go through, sometimes that only takes a few minutes and sometimes it takes >40 minutes.

If it takes more than 30 minutes, reset nonces in metamask settings and restart the process.

If you want to speed it up further, modify the gas settings in your approve tx within your wallet to increase the maximum fee and the priority fees, this will increase the bribe to validators and make it more likely for your tx to get in.

#### I've seen an error about fee being lower than base fee
It's because the base gas fee has increased since you signed your approval tx. To solve this, reset your nonces in metamask settings and restart the process.

#### Metamask shows me warnings when changing RPC
These are normal, just make sure not to sign any weird txs after switching RPC and you'll be fine. SmolRefuel only requests an approval tx where you can verify the total amount approved, which should be the same amount you've inputted.

#### 10 ETH appeared in my wallet, where do they come from?
Our RPC simulates a balance of 10 ETH so that your wallet will allow you to sign transactions (otherwise it wouldn't allow you because your balance is too low to cover gas). The 10 ETH that you see is thus fake and will disappear as soon as you switch RPCs.

#### I got stuck
You need to do this:
1. Reset your state by going to metamask settings > Advanced > Click on "Clear activity tab data"
2. Refresh the page and restart the process again to do the swap

#### Why is fee so high?
We need to send 3 txs:
1. One tx sending you gas money for approval tx
2. Your approval tx
3. Swap tx

And these txs need to include bribes to have the bundle be accepted by flashbots, so the fee you're seeing represents the costs of sending those 3 txs + bribes, which is just expensive on mainnet.

#### I'm getting a different error
Contact 0xngmi on twitter.
