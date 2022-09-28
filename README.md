# Ollo Station Node Testneti

![1_SdfNCpGceClqhW9oDrJ9SQ](https://user-images.githubusercontent.com/111747226/192885867-b9efe612-681b-4461-8ce5-7e306a7ed237.png)




### Sistem Gereksinimleri 

|CPU | RAM  | Disk  | 
|----|------|----------|
|   4| 8GB  | 100GB    |

 # Daha önce Node kurulumu yapmadıysanız buradan sırasıyla adımları takip ederek tüm süreci öğrenebilirsiniz.
  ## Yeni Başladım Rehberi; [Pusula Finans Labs.](https://www.labs.pusulafinans.com/category/rehber/)
  ### 1. [Testnet ve Node test kurulum rehberi Bölüm-1](https://www.labs.pusulafinans.com/2022/08/23/testnet-ve-node-kurulum-rehberi/)
  ### 2. [Yeni Chrome Tarayıcı nasıl açarım?](https://www.labs.pusulafinans.com/2022/08/23/yeni-chrome-tarayici-nasil-acarim/)
  ### 3. [Ücretsiz Sunucu Kiralama](https://www.labs.pusulafinans.com/2022/08/23/nasil-ucretsiz-sunucu-kiralarim/)
  ### 4. [Digital Ocean Nasıl Kayıt olurum?](https://www.labs.pusulafinans.com/2022/08/23/digital-oceana-nasil-kayit-olabilirim/)
  ### 5. [MobaXTerm Terminal Kurulumu](https://www.labs.pusulafinans.com/2022/08/23/mobaxterm-terminal-kurulumu/)
  
### Kuruluma başlayalım.

```
wget -O ollo.sh https://raw.githubusercontent.com/pusulafinanslabs/Ollo-Station/main/ollo.sh && chmod +x ollo.sh && ./ollo.sh
```

### Log kontrol komutu

```
journalctl -fu ollod -o cat
```

### Sync Durumunuzu öğrenmek için;

```
ollod status 2>&1 | jq .SyncInfo
```

### Cüzdan oluşturma: (not edin kaydedin)
```
ollod keys add CUZDANISMI
```

### Faucet için; Discorda katılmayı unutmayın. ( https://discord.gg/TrPSz3bn )

### Validator Olmak İçin;

```
ollod tx staking create-validator \
  --amount 49500000utollo \
  --from CUZDANISMI \
  --commission-max-change-rate "0.01" \
  --commission-max-rate "0.2" \
  --commission-rate "0.07" \
  --min-self-delegation "1" \
  --pubkey  $(ollod tendermint show-validator) \
  --details="Kendini Tanıt" \
  --website="website veya mail adresi" \
  --moniker NodeName \
  --chain-id ollo-testnet-0
```

### Explorer

```
https://explorer.kjnodes.com/ollo/staking
```

### Discorddan Role Odasından rol almayı unutmayın!!

## Ollo Station için Önemli Komutlar

### Unjail komutu

```
ollod tx slashing unjail --from=CUZDANISMI --chain-id=ollo-testnet-0 --gas-prices=0.025utollo
```

### Peer komutu

```
echo "$(ollod tendermint show-node-id)@$(curl ifconfig.me):32657"
```

### Node'u silmek için gerekli komut

```
sudo systemctl stop ollod
sudo systemctl disable ollod
sudo rm /etc/systemd/system/ollo* -rf
sudo rm $(which ollod) -rf
sudo rm $HOME/.ollo* -rf
sudo rm $HOME/ollo -rf
sed -i '/OLLO_/d' ~/.bash_profile
```

### Kolay Gelsin..

