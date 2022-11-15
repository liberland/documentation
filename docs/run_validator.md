
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

## Submit keys

## check that keys have been added

restart node with validator flag
