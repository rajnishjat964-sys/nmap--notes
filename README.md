# nmap-notes
NMAP is a cybersecurity tool used for:
- Network mapping
- Host discovery
- Port scanning
- Service detection
- OS fingerprinting.

## Host discovery 
It is for standard scan. 
```bash 
nmap -sn <ip-range>
```
### ARP Scan
It is cannot be blocked by OS firewall, but it only works within the same local network. It would not work across routers.
```bash
sudo nmap -PR -sn <target-ip>
```
### ICMP Echo request (Type 8)
If host is alive, it replies with Echo reply (Type 0)
```bash
sudo nmap -PE -sn <target-ip>
```
### ICMP Timestamp/Subnet Mask request
It is used when standard pings are blocked, but if it is poorly deployed firewall or it has loopholes.

- For Timestamp Scan = -PP
- For Address Mask Scan = -PM

```bash
sudo nmap -PP -sn <target-ip>
```
### TCP Pings 
When firewalls block ICMP ,TCP Pings are used to trick the host into responding.

- For TCP SYN Scan = -PS
- For TCP ACK Scan = -PA
```bash
sudo nmap -PA -sn <target-ip>
```
### UDP Scan 
```bash
sudo nmap -PU -sn <target-ip>
```
## TCP Connect Scan
it perform 3-way handshake.
```bash
sudo nmap -sT <target-ip>   
```

## TCP SYN Scan
requires root/administrator privileges
```bash
sudo nmap -sS <target-ip>     
```

## UDP Scan
Scans UDP ports. UDP scans are usually slower than TCP scans.
```bash
sudo nmap -sU <target-ip>
```

## Aggressive Scan 
Performs OS detection, version detection,script scanning, and traceroute.
```bash
nmap -A <target-ip>
```

## FIN, NULL, XMAS Scan
These scans can sometimes help identify ports while bypassing certain firewall or filtering rules.
- for FIN = -sF
- for NULL = -sN
- for XMAS = -sX
```bash
nmap -sF <target-ip>
```

## Service Version Detection
```bash
nmap -sV <target-ip>
```

## Default Scripts
Runs Nmap's default NSE (Nmap Scripting Engine) scripts to gather additional information about services.
```bash
nmap -sC <target-ip>
```

## NSE Scripts
NSE scripts automate service enumeration, vulnerability checks, and information gathering.
### FTP Anonymous Login Check (ftp-anon)
Checks whether anonymous login is allowed on an FTP server.
```bash
nmap --script ftp-anon -p 21 <target-ip>
```
### SSH Authentication Methods (ssh-auth-methods)
Lists the authentication methods supported by an SSH server.
```bash
nmap --script ssh-auth-methods -p 22 <target-ip>
```

## Timing Templates
control speed of nmap scanning
### Levels
- paranoid (-T0) : very slow, max stealth
- sneaky(-T1) : slow, avoid detection
- polite(-T2) : low network load
- normal(-T3) : default, balanced
- aggressive(-T4) : fast, less stealth
- insane(-T5) : very fast, less accurate
```bash
sudo nmap -sS -T4 <target-ip>  (a aggressive TCP SYN scan)
```

## OS Detection
```bash
sudo nmap -O <target-ip>
```


