# nmap--notes
NMAP is a cybersecurity tool used for:
- Network mapping
- Host discovery
- Port scanning
- Service detection
- OS fingerprinting.

## Host discovery 
```bash 
nmap -sn <ip-range>
```

## TCP Connect Scan
it perform 3-way handshake.

```bash
nmap -sT <target-ip>   
```
## TCP SYN Scan
```bash
sudo nmap -sS <target-ip>     (requires root/administrator privileges)
```
## UDP Scan
it scan for  UDP ports.
slowest scan
```bash
sudo nmap -sU <target-ip>
```

## Aggressive Scan 
it scan for OS, Versions, Scripts and traceroute
```bash
nmap -A <target-ip>
```
## FIN, NULL, XMAS Scan
it use to bypass firewall.
- for FIN = -sF
- for NULL = -sN
- for XMAS = -sX
```bash
nmap -sF <target-ip>
```
## Service Version Detection
```bash
nmap -sV <>target-ip
```


