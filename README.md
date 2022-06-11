# Raspberry-Pi-Hotspot
The script(s) in this directory enable a Raspberry Pi to perform hotspot duties while forwarding client traffic through the ethernet port (or another wifi card/dongle) and out to the web.

## Installed software (and their dependencies)
- hostapd
- dnsmasq
- iptables-persistent

## Files edited
- /etc/network/interfaces
- /etc/dhcpcd.conf
- /etc/dnsmasq.conf
- /etc/hostapd/hostapd.conf (created and edited)
- /etc/default/hostapd
- /etc/sysctl.conf

## 3 iptables rules added
```
sudo iptables -t nat -A  POSTROUTING -o ethX -j MASQUERADE
sudo iptables -A FORWARD -i ethX -o wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i wlan0 -o ethX -j ACCEPT
```

## User input required
- prompted for hotspot ssid
- prompted for hotspot password
- asked which interface to route traffic out to the internet
- asked which interface to be used as a hotspot
- asked to reboot

