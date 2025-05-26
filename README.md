# Scan-your-Local-Network-for-Open-Ports-
🔍 Scan Your Local Network for Open Ports using Nmap (-sS TCP SYN Scan)

This guide explains how to use Nmap’s TCP SYN scan (`-sS`) to scan your local network for open ports. TCP SYN scan is the default and most popular scan option in Nmap. It’s fast, stealthy, and effective.

📌 What is `-sS`?

`-sS` tells Nmap to perform a TCP SYN scan, often referred to as a "half-open" scan because it doesn't complete the TCP handshake. It sends a SYN packet and waits for a response:

 - SYN-ACK = Port is open
 - RST = Port is closed
 - No response or filtered = Possibly filtered/firewalled
   
📦 Requirements

 - OS: Linux, macOS, or Windows
 - Nmap Installed:
    - Linux: sudo apt install nmap
    - macOS: brew install nmap
    - Windows: Download here
      
🔧 Usage

1. Identify Your Local IP and Subnet
Run:

 - Linux/macOS:
`ip a`

 - Windows (CMD/PowerShell):

`ipconfig `

Example: If your IP is `192.168.1.100` with subnet `/24`, the network range is likely:

`192.168.1.0/24`

2. Run the TCP SYN Scan
   
`sudo nmap -sS 192.168.1.0/24`

🔑 `sudo` is required for raw packet scanning.

📝 Output Explanation

Nmap will return a list of live hosts and their open TCP ports:

```python
Nmap scan report for 192.168.1.10
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
443/tcp  open  https
```
💡 Optional Enhancements

Add OS detection & service version:

`sudo nmap -sS -A 192.168.1.0/24`

Save output to file:

`sudo nmap -sS 192.168.1.0/24 -oN scan_results.txt`

Faster scan (less accurate timing):

`sudo nmap -sS -T4 192.168.1.0/24`

⚠️ Legal Warning

⚠️ Only scan networks that you own or have explicit permission to test. Unauthorized scanning is illegal and unethical.

