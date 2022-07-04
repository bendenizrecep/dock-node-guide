## dock-node-guide

### first we install docker and then we install screen
```
sudo snap install docker
screen -S main
```

### Enter the codes in order
```
sudo -s

docker run -p 9944:9944 -p 30333:30333 docknetwork/dock-substrate:latest --chain ./cspec/knox_raw.json --ws-external

curl https://sh.rustup.rs -sSf | sh

rustup update nightly

rustup target add wasm32-unknown-unknown --toolchain nightly

cargo build --release

cargo build --release --features mainnet
```
###After these codes, there is the key creation part, we will do it using UI instead of using scripts.

https://docs.dock.io/validators/tooling/key-generation

We will only do what is explained in the _Using Browser UI_ section from the page in the link above.

### We continue to enter the codes in order
```
insert_session_key_with_seed.js
knox_raw.json
-chain=/cspec/knox_raw.json

```

#### Code Required to View Logs (We need to monitor the logs and confirm it's working.)

```
sudo docker logs dock-node -f --tail 100
```

### Becoming Validator _continue in order_

```
cargo build --release --features mainnet
./target/release/dock-node --chain-spec=./cspec/knox_raw.json --validator 
docker run -d -p 9944:9944 -p 9933:9933 -p 30333:30333 docknetwork/dock-substrate:mainnet --chain=./cspec/knox_raw.json --validator

```
