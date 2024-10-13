<p style="font-size:14px" align="right">
<a href="https://t.me/airdropasc" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
</p>

<p align="center">
  <img height="300" height="auto" src="https://user-images.githubusercontent.com/109174478/209359981-dc19b4bf-854d-4a2a-b803-2547a7fa43f2.jpg">
</p>


# ZENROCK TESTNET NODE
## Link
- [Explorer](https://testnet.itrocket.net/zenrock/staking)
- [Discord](https://discord.gg/bnJfVmHg)
- [Documentation](https://docs.zenrocklabs.io/)
- [Twitter](https://x.com/OfficialZenRock)
## SPEK VPS MINIMUM
|  Hardware/VPS |  Minimum |
| ------------ | ------------ |
| CPU  | 4 or more physical CPU cores  |
| RAM | At least 6GB of memory (RAM) |
| Penyimpanan  | At least 100GB of SSD disk storage |
| Internet | At least 10mbps network bandwidth |
## Auto Install
```
bash <(curl -s https://data.zamzasalim.xyz/file/uploads/zenrock.sh)
```
- Pastikan cek status node `zenrockd status 2>&1 | jq` Jika sudah false baru buat wallet
- Setelah buat walllet claim faucet di [discord](https://discord.gg/bnJfVmHg)
- Jika sudah masuk cek saldo kalian `zenrockd q bank balances $(zenrockd keys show wallet -a)`
- Kemudian Lanjut buat Validator
## Perintah Berguna
### Cek Logs Node
```
sudo journalctl -u zenrock-testnet.service -f --no-hostname -o cat
```
### Start Node
```
sudo systemctl start zenrock-testnet.service
```
### Stop Node
```
sudo systemctl stop zenrock-testnet.service
```
### Cek Status Node
```
sudo systemctl status zenrock-testnet.service
```
### Cek Sinkron Node
```
zenrockd status 2>&1 | jq
```
### Create Wallet
```
zenrockd keys add wallet
```
### Delete Wallet
```
zenrockd keys delete wallet
```
### Cek Saldo Wallet
```
zenrockd q bank balances $(zenrockd keys show wallet -a)
```
### Delegate Token to your self
```
zenrockd tx validation delegate $(zenrockd keys show wallet --bech val -a) 1000000urock --from wallet --chain-id gardia-2 --gas-adjustment 1.4 --gas auto --gas-prices 30urock -y
```
### Delegate Token to more Validator
```
zenrockd tx validation delegate <TO_VALOPER_ADDRESS> 1000000urock --from wallet --chain-id gardia-2 --gas-adjustment 1.4 --gas auto --gas-prices 0urock -y
```
### Delete Node
```
cd $HOME
sudo systemctl stop zenrock-testnet.service
sudo systemctl disable zenrock-testnet.service
sudo rm /etc/systemd/system/zenrock-testnet.service
sudo systemctl daemon-reload
rm -f $(which zenrockd)
rm -rf $HOME/.zrchain
```
