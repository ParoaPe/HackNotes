# DNSMASQ

- Install dnsmasq
```bash
sudo apt install dnsmasq
```

- Add `dns=dnsmasq`to /etc/NetworkManager/NetworkManager.conf
```bash
sudo vi /etc/NetworkManager/NetworkManager.conf   
[main]
dns=dnsmasq
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

- Uncomment `conf-dir` in /etc/dnsmasq.conf
```bash
sudo vi /etc/dnsmasq.conf
# Include all files in a directory which end in .conf
conf-dir=/etc/dnsmasq.d/,*.conf
```

- Create a personal conf file
```bash
sudo vi /etc/dnsmasq.d/olivierprotips.conf 
server=192.168.2.91
server=8.8.8.8

address=/.quotient.thm/10.10.250.116
```

- Launch service
```bash
sudo systemctl start dnsmasq
sudo systemctl enable dnsmasq
```

- Disable systemd-resolved
```bash
sudo systemctl disable systemd-resolved.service
sudo systemctl stop systemd-resolved.service
```

- Modify /etc/resolv.conf
```bash
nameserver 127.0.0.1
options edns0 trust-ad
```

## DEPRECATED

```bash
sudo systemctl restart network-manager.service
```