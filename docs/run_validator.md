# How to run a validator

Note:   
*DO NOT* expose your validators rpc port publicly on the internet. Treat validators with more care than full nodes      
You *do not* need to a run a validator to earn LLD staking rewards. As a user you can simply become a nominator and stake your coins without needing to run a validator.   

compile the node with cargo:

```
git clone https://github.com/liberland/liberland_substrate && cd liberland_substrate && cargo build --release

```

install subkey:
```
cargo install subkey
```

generate keys:
```
$ subkey generate
Secret phrase:       power popular buffalo predict renew gasp stay steak blanket opinion current stove
  Secret seed:       0x542c112cb6130d531ba9751cb209d8c3782c0158783562e1336b1628e834354a
  Public key (hex):  0xbefda47b8e41d8bd1642d6cdf4560b914915466ead377d7646a805cae9344141
  Account ID:        0xbefda47b8e41d8bd1642d6cdf4560b914915466ead377d7646a805cae9344141
  Public key (SS58): 5GP8JWw8Vg1VK42h1D2mXxBt5AQ7MDGdAH4F87QGoWCuD5nr
  SS58 Address:      5GP8JWw8Vg1VK42h1D2mXxBt5AQ7MDGdAH4F87QGoWCuD5nr


```

Grab your seed phrase and use the seedphrase to generate the next keys:

## Generate grandpa, babe, audi and imol keys for your validator   

```
$ subkey inspect "power popular buffalo predict renew gasp stay steak blanket opinion current stove//grandpa" --scheme ed25519
$ subkey inspect "power popular buffalo predict renew gasp stay steak blanket opinion current stove//babe" --scheme sr25519
$ subkey inspect "power popular buffalo predict renew gasp stay steak blanket opinion current stove//im_online" --scheme sr25519
$ subkey inspect "power popular buffalo predict renew gasp stay steak blanket opinion current stove//authority_discovery" --scheme sr25519

```




# Sync the node   
Sync your node without the validator flag to the latest finalized block:   
```
./target/release/substrate --chain customSpecRaw.json --bootnodes /ip4/162.55.230.227/tcp/30333/p2p/12D3KooWRdDm7tDTR8uL9CQxvnvXrUBPLJfrKuHJaCLZfWz9WzeY --base-path /tmp/hayek --unsafe-pruning --pruning=1000 
```

## Submit keys

```
curl http://localhost:9933  -H "Content-Type:application/json;charset=utf-8" -d '{
    "jsonrpc":"2.0",
    "id":1,
    "method":"author_insertKey",
    "params": [
        "babe",
        "SEEDGOESHERE//babe",
        "PUBKEY"
    ]
}'

curl http://localhost:9933  -H "Content-Type:application/json;charset=utf-8" -d '{
    "jsonrpc":"2.0",
    "id":1,
    "method":"author_insertKey",
    "params": [
        "gran",
        "SEEDGOESHERE//grandpa",
        "PUBKEY"
    ]
}'

curl http://localhost:9933  -H "Content-Type:application/json;charset=utf-8" -d '{
    "jsonrpc":"2.0",
    "id":1,
    "method":"author_insertKey",
    "params": [
        "imol",
        "SEEDGOESHERE//im_online",
        "5Ehp3to58kyKEpZd8PyXGWr2TpXVCS1b31W5TkiLKvxr4CJn"
    ]
}'

curl http://localhost:9933  -H "Content-Type:application/json;charset=utf-8" -d '{
    "jsonrpc":"2.0",
    "id":1,
    "method":"author_insertKey",
    "params": [
        "audi",
        "SEEDGOESHERE//authority_discovery",
        "PUBKEY"
    ]
}'

```

## check that keys have been added  
check the directory you specified with `--base-path`:  
```
$ ls /tmp/hayek/chains/hayek/keystore/
```





### restart node with validator flag:   
```
./target/release/substrate --chain customSpecRaw.json --bootnodes /ip4/162.55.230.227/tcp/30333/p2p/12D3KooWRdDm7tDTR8uL9CQxvnvXrUBPLJfrKuHJaCLZfWz9WzeY --base-path /tmp/hayek --unsafe-pruning --pruning=1000 --validator
```


