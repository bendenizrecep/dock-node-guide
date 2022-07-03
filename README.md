## dock-node-guide

### ilk önce docker yüklüyoruz ve ardından screen kurulumu yapıyoruz
```
sudo snap install docker
screen -S main
```
### node yüklemesi

```
git clone --branch latest --depth 1 https://github.com/substrate-developer-hub/substrate-node-template

cd substrate-node-template

cargo b -r

```
#### help komutu ile birr çok şeyi görebiliriz 
```
./target/release/node-template --help

```
#### burayı tam anlamadım //alice yazar da denenebilir
```
./target/release/node-template key inspect //nodeismi gelmesi gerekebilir burda bir soru işareti var
```
#### bu kod ile node başlıyor

```
./target/release/node-template --dev

```



### validator nod için gerekli ıvır zıvır (düzenlencek)
```

docker run -p 9944:9944 -p 30333:30333 docknetwork/dock-substrate:latest --chain ./cspec/knox_raw.json --ws-external

curl https://sh.rustup.rs -sSf | sh

rustup update nightly

rustup target add wasm32-unknown-unknown --toolchain nightly

cargo build --release

cargo build --release --features mainnet

cargo build --release --features small_durations

cargo build --release --features fastblock

docker build --build-arg features='--features mainnet' .

./target/release/dock-node build-spec --chain=testnet > knox_test.json
./target/release/dock-node build-spec --chain=knox_test.json --raw > knox_test_raw.json



```


