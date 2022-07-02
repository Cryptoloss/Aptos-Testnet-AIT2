# Aptos-Testnet-AIT2
## Selam Dostlar, Sizlere Aptos Ödüllü Testneti İçin Kodlar Hazırladım/ÖDÜL 500 $APTOS ÖNEMLİ

[Testnet Ödülü Hakkında Detaylı Bilgi]([url](https://twitter.com/Cryptoloss1/status/1542188448005718017?s=20&t=WuQXVvibYWtJiFfYG9zSAQ))

Öncelikle bir adet sanal sunucuya ihtiyacımız var ben Contaba kullanıyorum siz aşşağıdaki sistem gereksinimlerini karşılayan herhangi bir sanal sunucuyu kullanabilirsiniz.

**Sistem Gereksinimleri**

400GB SSD 16GB RAM

Not: Bu sistem gereksinimlerini karşılayacak gücünüz yoksa SSD yerine RAM'den kısın.

Mac kullananlar kod yazmak için [Terminali](https://forum.rues.info/index.php?threads/mac-bilgisayardan-node-kurulumu.1535/#post-7152), [Windows](https://forum.rues.info/index.php?threads/putty-nedir-nasil-kullanilir.1829/) kullananlar ise Putty Tercih edebilir.

Sayfaları Güncelleyelim

`sudo apt update && sudo apt upgrade -y`

Unzip Kodu

`sudo apt-get install jq unzip -y`

Screen Kurulumu (Soru Soracak Y diyelim)

`sudo apt install screen`

Git Kuralım (Y bas Enterla)

`apt install git`

Cargo Kurulumu (Y bas Enterla)

`apt install cargo`

Aptos Repo Klonla

`git clone https://github.com/aptos-labs/aptos-core.git`

Sonra Bu Kodu Girelim

`cd aptos-core`

Geliştirici Ortamını Hazırla (Enter Y) uzun sürecek

`./scripts/dev_setup.sh`

Mevcut Shell Güncelle

`source ~/.cargo/env`

**Validatörümüzü Oluşturacağız**

Test Ağını Kontrol Et

`git checkout --track origin/testnet`

Dizin Oluşturma

```
export WORKSPACE=testnet
mkdir ~/$WORKSPACE
```
   
Key Pair Oluşturma (uzun sürecek sabirla bekleyin)

`cargo run --release -p aptos -- genesis generate-keys --output-dir ~/$WORKSPACE`

**Dikkat**
Bu kod sayesinde 3 dosya oluşturacağız:`private-keys.yaml`, `validator-identity.yaml`,`validator-full-node-identity.yaml`. Dosyalarınızı güvenli bir yere kaydedin ve kimseyle paylaşmayın.

`cargo run --release -p aptos -- genesis generate-keys --output-dir ~/$WORKSPACE`

private-Keys.yaml dosyasını bu kodla açabilirsiniz.(Kaydedin)

`sudo nano /root/testnet/private-keys.yaml`

Validatör Yapılandırma Adımı

```cargo run --release -p aptos -- genesis set-validator-configuration \
    --keys-dir ~/$WORKSPACE --local-repository-dir ~/$WORKSPACE \
    --username isminiyaz\
    --validator-host 35.232.235.205:6180 \
    --full-node-host 34.135.169.144:6182
```
Kullanıcı adımız ile YALM dosyası oluşturalım

`sudo nano /root/testnet/burayaisminiyaz.yaml`

Layout Oluşturma

`vi ~/$WORKSPACE/layout.yaml`

Açılan pencereye aşşağıdaki kodları kopyalayıp yapıştıralım (hepsi birden) **İsim yazmayı unutma** 
kodları girdikten sonra ctrl + x yapıp entere basın

```---
root_key: "F22409A93D1CD12D2FC92B5F8EB84CDCD24C348E32B3E7A720F3D2E288E63394"
users:
  - "buraya ismini Yaz"
chain_id: 40
min_stake: 0
max_stake: 100000
min_lockup_duration_secs: 0
max_lockup_duration_secs: 2592000
epoch_duration_secs: 86400
initial_lockup_timestamp: 1656615600
min_price_per_gas_unit: 1
allow_new_validators: true
```
**Framework**
```
cargo run --release --package framework -- --package aptos-framework --output current
mkdir ~/$WORKSPACE/framework
mv aptos-framework/releases/artifacts/current/build/**/bytecode_modules/*.mv ~/$WORKSPACE/framework/
mv aptos-framework/releases/artifacts/current/build/**/bytecode_modules/dependencies/**/*.mv ~/$WORKSPACE/framework/
```
**Compile Genesis**

`cargo run --release -p aptos -- genesis generate-genesis --local-repository-dir ~/$WORKSPACE --output-dir ~/$WORKSPACE`

Sıradaki kodumuzu tek seferde kopyalayıp yapıştıralım
```
mkdir ~/$WORKSPACE/config
cp docker/compose/aptos-node/validator.yaml ~/$WORKSPACE/validator.yaml
cp docker/compose/aptos-node/fullnode.yaml ~/$WORKSPACE/fullnode.yaml
```

**Config dosyasını açalım**

`sudo nano /root/testnet/validator.yaml`

__şimdi vereeceğim kod ile ilk görseldeki taralı alanları silim verdiğim kodu girin__
![1](https://user-images.githubusercontent.com/98783018/176990094-40835cab-da07-46b7-a9c6-397e401446a0.png)

**Kod:**

`/root/testnet/`

![2](https://user-images.githubusercontent.com/98783018/176990137-deb77367-6ee6-4bda-9305-64673cd18185.png)

Son durum aynı ikinci resimdeki gibi olmalı

Şimdi CTRL + X ile sayfadan çıkalım daha sonra Y ve ENTER

**Validatörü başlatıyoruz**

`screen -S aptos-core`

2. kod

`cargo run -p aptos-node --release -- -f ~/testnet/validator.yaml`

CTRL+A+D ile screenden çıkabilirsiniz

Node'nin çalışıp çalışmadığını kontrol edelim. Öncelikle linke [TIKLA](https://aptos-node.info/)
Açılan menü içerisinden sol en üst taraftaki arama bölümüne VPS adresini gir.


