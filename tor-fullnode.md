# Tutorial: Running a Bitcoin fullnode on Tor

## Build Tor from Github

### Get sources
```
git clone https://github.com/torproject/tor.git
```

### Compile
```c
cd tor
sh autogen.sh
./configure
make
```

(optional: install Tor globally)
```
sudo make install
```

## Configure and run Tor
Add the following lines to the end of tor configuration file: /etc/tor/torrc 
Generate a new password for Tor access control daemon:
```
("satoshinakamoto" will be used as tor password in bitcoin.conf)
$ tor --hash-password satoshinakamoto

16:1C259D8CEE9E4DBE605C12B0893B8D784B6100AF3D389624513DC4D376
```

```
ControlPort 9051
HashedControlPassword 16:1C259D8CEE9E4DBE605C12B0893B8D784B6100AF3D389624513DC4D376

HiddenServiceDir /var/lib/tor/bitcoin-service/
HiddenServicePort 8333 127.0.0.1:8333
HiddenServicePort 18333 127.0.0.1:18333
```

### Run Tor service
```
sudo /etc/init.d/tor start
```

Check your node hostname on onion network:
```
cat /var/lib/tor/bitcoin-service/hostname
Example: tahgfshdhfhs.onion
```

## [OPTIONAL] Create an hidden service to connect on port 2288 using SSH
Add the following lines to the end of tor configuration file: /etc/tor/torrc
```
HiddenServiceDir /var/lib/tor/ssh_hidden_service/
HiddenServicePort 2288 127.0.0.1:22
```

### Restart Tor service
```
sudo /etc/init.d/tor restart
```

save your SSH hostname to connect using TOR network
```
cat /var/lib/tor/ssh_hidden_service/hostname

Example: wtreterterdsfa.onion
```

Connect using torify:
```
torify ssh username@wtreterterdsfa.onion -p 2288
```

## Configure and run Bitcoind
Edit the Bitcoin configuration file (default path: .bitcoin/bitcoin.conf) and add:

```
proxy=127.0.0.1:9050
torpassword=satoshinakamoto
listen=1
txindex=1
```

Start Bitcoind
```
bitcoind -daemon
```

Check Bitcoin network info
```
bitcoin-cli getnetworkinfo
{
      "name": "onion",
      "limited": false,
      "reachable": true,
      "proxy": "127.0.0.1:9050",
      "proxy_randomize_credentials": true
}
```