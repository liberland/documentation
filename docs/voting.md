## Voting with LLM on-chain asset   

Because of the design and implementation of LLM, LLM is not a native substrate token. Rather, LLM is a custom implementation  
of an on-chain asset. Liberland's chain comes with a custom democracy voting integration, being the first chain that allows users to vote with   
on-chain assets instead of the native substrate balances. 


Read more about on-chain assets here:
https://marketplace.substrate.io/pallets/pallet-assets/   

Indept LLM documentation:
https://github.com/liberland/liberland_substrate/blob/main/frame/llm/Readme.md   


## Setup enviroment:  
We recommend that you manually clone the github repository and build it:
```
git clone https://github.com/liberland/liberland_substrate && cd liberland_substrate/ && cargo build --release

```
Run the node in dev mode to make things easy:
```
./target/release/substrate --dev --
```

Navigate to [polkadot.js ](https://polkadot.js.org/apps/) and choice local node.

### Become an on-chain citizen
In order to vote or interact with the political system, a user needs to become and on-chain citizen.
The requirements for being a citizen is:
*  Approved roled with the citizen field   
*  Pooled llm

### Politic pooling LLM   
Get some LLM:
Navigate over to `polkadot.js > Developer > extrinsics > llm > fakesend `

Allocate LLM for politics:
`polkadot.js > Developer > extrinsics > llm > politicslock `

Check your LLM balance by going to `Developer > chainstate > llm > select llmPolitics and llm.llmBalance `

## LLMPolitics
This is the amount of LLM you have allocated for Politics, these llm can not be used for any type of non-voting functionality

## LLMBalance  
This is your liquid LLM balance  

Unpool your llm with :
`polkadot.js > Developer > extrinsics > llm > politicsunlock `


