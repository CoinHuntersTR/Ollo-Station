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

### Log kontrol komutundan sonra log komutu tepki vermiyorsa şu komutu girip ardından yeniden log kontrol yapın.

```
systemctl restart systemd-journald
```

### Sync Durumunuzu öğrenmek için;

```
strided status 2>&1 | jq .SyncInfo
```

### Cüzdan oluşturma: (not edin kaydedin)
```
strided keys add cüzdanismi
```

### Faucet için; Discorda katılmayı unutmayın. ( https://discord.gg/ggQewkUa )

### Validator Olmak İçin;

```
strided tx staking create-validator \
  --amount 9900000ustrd \
  --from cüzdanisminiz \
  --commission-max-change-rate "0.01" \
  --commission-max-rate "0.2" \
  --commission-rate "0.07" \
  --min-self-delegation "1" \
  --pubkey  $(strided tendermint show-validator) \
  --moniker nodeisminiz \
  --chain-id=STRIDE-TESTNET-4 
```

### Explorer

```
https://explorer.kjnodes.com/ollo/staking
```

### Discorddan Role-Request Odasına Explorerdan validator linkinizi atıp rol almayı unutmayın.

## Ollo Station için Önemli Komutlar

### Unjail komutu

```
strided tx slashing unjail --from=Cüzdanismi --chain-id=STRIDE-TESTNET-4 --gas-prices=0.025ustrd
```

### Node'u silmek için gerekli komut

```
sudo systemctl stop strided
sudo systemctl disable strided
sudo rm /etc/systemd/system/stride* -rf
sudo rm $(which strided) -rf
sudo rm $HOME/.stride* -rf
sudo rm $HOME/stride -rf
sed -i '/STRIDE_/d' ~/.bash_profile
```

### Kolay Gelsin..

