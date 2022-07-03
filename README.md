# Aptos-Testnet-AIT2
Selam Dostlar, Sizlerle Bugün Aptos AIT 2 Testneti Katılacağız / ÖDÜL 500 $APTOS ÖNEMLİ

Less Goo

Aptos Node Testnetinin Ödül Dağıtımı Hakkında Detaylı Bilgi [TIKLA](https://twitter.com/Cryptoloss1/status/1542188448005718017?s=20&t=e7tew4fNQwBXbbUHUaLqJQ)

Daha Önce Hiç Node Kurmayan Arkadaşlar İçin Kaynaklar Bulunan Discord [RUES](https://discord.gg/MppxydEX)

_Aşşağıdaki kodu girdikten bir süre sonra sizden Node İsmi isteyecek ben Node ismimi Cryptoloss yaptım_

`wget -q -O aptos.sh https://api.nodes.guru/aptos.sh && chmod +x aptos.sh && sudo /bin/bash aptos.sh`

[Aptos Websitesine](https://community.aptoslabs.com/) Gidelim Sing Up Butonuna Basıp Githup İle Siteye Bağlanalım

Siteye giriş yaptıktan sonra ilk olarak **discord** doğrulamasını daha sonrada diğer görevleri tamamlayalım


![adımları tamamla](https://user-images.githubusercontent.com/98783018/177036748-693f82e4-cfe5-456b-9585-5457e30f18bb.png)

Sıradaki kod ile account adress, private key, consesus key gibi bilgilere ulaşacağız bu bilgilerimizi kaybolmayacağını düşündüğümüz bir yere kaydedelim.

```
source ~/.bash_profile 
cat ~/.aptos/$APTOS_NODENAME.yaml
```

![account key](https://user-images.githubusercontent.com/98783018/177036844-3ca2f777-8964-4417-9564-076c627f66f9.png)


Source ile başlayan kod sayesinde consensus key vb bilgilerimizi almıştık şimdi ise bu bilgileri açılan websitedeki kutucuklara giriyoruz ve KYC yapıyoruz


![public keys](https://user-images.githubusercontent.com/98783018/177036936-8ad995d1-6787-4794-978f-bec27c496e3d.png)

**Faydalı Kodlar:**

Logları Gör

`docker logs -f --tail 100 aptos-validator-1`

Reset At

`cd ~/.aptos && docker-compose restart`

Sync Durumu

`curl 127.0.0.1:9101/metrics 2> /dev/null | grep aptos_state_sync_version`

Node Durdur

`cd ~/.aptos && docker-compose stop`

Eğer Yaptığınız İşlemler Doğruysa Aptostan Mail Gelecek, 11 Temmuzda Bir Daha Mail Gelecek Node Kurmaya Seçilip Seçilmediğiniz Hakkında

[Telegram](https://t.me/LossNodeDuyuru)

[Youtube](https://www.youtube.com/channel/UCKIpdWDFJN59nkVQHn5xfZA)


