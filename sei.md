## Download latest snapshot (using the example of Osmosis)  
Stop Sei service  
`systemctl stop seid.service`  

Remove old data in directory `~/.sei-chain/data`  
```
rm -rf ~/.sei-chain/data; \
mkdir -p ~/.sei-chain/data; \
cd ~/.sei-chain/data
```

Download snapshot  
```bash
SNAP_NAME=$(curl -s http://94.130.10.43/sei/ | egrep -o ">sei.*tar" | tr -d ">"); \
wget -O - http://94.130.10.43/sei/${SNAP_NAME} | tar xf -
```
![alt text](https://github.com/c29r3/cosmos-snapshots/blob/main/2021-01-20_14-19.png?raw=true)

Start service and check logs  
```
systemctl start seid.service; \
journalctl -u seid.service -f --no-hostname
```
