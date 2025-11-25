---
layout: single
title: "20 Essential Network and Security Commands (Beginner-Friendly Guide)"
description: "Learn the 20 most important network and cybersecurity commands every IT professional should master — with clear explanations and real-world examples. Perfect for beginners, sysadmins, and certification prep."
tags:
  - terminal
  - network
  - cybersecurity
  - linux
  - windows
  - dns
category:
  - cybersecurity
  - certification
---

If you work with networking, cybersecurity, DevOps, or system administration, mastering the command line is not optional, it’s essential. Many real-world troubleshooting scenarios require fast diagnostics, and graphical interfaces often don’t give you enough insight.

That’s why I created this beginner-friendly and optimized guide covering the **20 most essential network and security commands**. Whether you're preparing for certifications (CompTIA Network+, Security+, PenTest), managing a server, or learning Linux, these commands will quickly become part of your daily toolkit.

I have listed each command in my order with clear descriptions, use cases, and practical examples.

---
## 20 Essential Network and Security Commands (Explained Clearly)

#### 1. **ping**
**Purpose:** Test connectivity between your device and a target domain/IP. This command is a must have in our tool list. 

**Best for:** Checking if a server, router, or website is reachable.  
**Examples:**
```bash
ping google.com       # for domains
ping 8.8.8.8          # for IP addresses
```

---
#### 2. **traceroute / tracert**
**Purpose:** Display each hop along the path to a destination.  
**Best for:** Diagnosing latency, routing issues, and packet loss.  
**Example:**
```bash
traceroute 8.8.8.8    # Linux OS
tracert 8.8.8.8       # Windows OS
```

---
#### 3. **ipconfig / ifconfig / ip a**
**Purpose:** View IP address, subnet mask, gateway, and interface details.  
**Examples:**
```bash
ipconfig /all     # Windows OS
ifconfig          # macOS, BSD, and old Linux OS version
ip a              # Modern version os Linux OS
```

---
#### 4. **nslookup**
**Purpose:** Query DNS records.  
**Best for:** Verifying domain-to-IP resolution.  
**Example:**
```bash
nslookup google.com
```

---
#### 5. **dig**
**Purpose:** Perform advanced DNS lookups.  
**Best for:** DNS debugging, troubleshooting propagation, or checking specific record types.  
**Example:**
```bash
dig google.com A
```

---
#### 6. **netstat**
**Purpose:** Show active connections, listening ports, and protocol statistics.  
**Best for:** Investigating suspicious traffic or open ports.  
**Examples:**
```bash
netstat -tuln    # Linux (TCP/UDP ports in numeric form)
netstat -an      # Windows (all connections and listening ports)
```

---
#### 7. **nmap**
**Purpose:** Scan networks to discover devices, OS fingerprints, and open ports.  
**Best for:** Security auditing and network mapping.  
**Example:**
```bash
nmap -sS 192.168.1.1
```

---
#### 8. **netcat (nc)**
**Purpose:** Create TCP/UDP connections, scan ports, and transfer data.  
**Example:**
```bash
nc -zv 192.168.1.1 22-80
```

---
#### 9. **tcpdump**
**Purpose:** Capture and analyze packets from a network interface.  
**Best for:** Low-level network troubleshooting.  
**Example:**
```bash
tcpdump -i eth0
```

---
#### 10. **wireshark / tshark**
**Purpose:** Deep packet inspection. It's a `tcpdump` command alternative.
**Best for:** Security analysis and protocol debugging.  
**Example:**
```bash
tshark -i eth0
```

---
#### 11. **whois**
**Purpose:** Display domain registration data.  
**Best for:** Investigating suspicious or unknown domains.  
**Example:**
```bash
whois google.com
```

---
#### 12. **hostname / hostnamectl**
**Purpose:** View or change the system hostname.  
**Example:**
```bash
hostnamectl set-hostname server01
```

---
#### 13. **ip route / route**
**Purpose:** Display or modify routing tables.  
**Best for:** Diagnosing gateway issues.  
**Example:**
```bash
ip route
```

---
#### 14. **arp / ip neigh**
**Purpose:** Show ARP table entries (IP ↔ MAC mappings).

**Best for:** Check IP duplicity in the network and manage packages.

**Examples:**
```bash
arp -a          # Shows the ARP table
ip neigh        # Shows the current neighbour table in kernel
```

---
#### 15. **curl / wget**
**Purpose:** Retrieve data from URLs, test APIs, or fetch files.  
**Examples:**
```bash
curl -I http://domain.com
wget http://domain.com/file.txt
```

---
#### 16. **ss**
**Purpose:** Show socket statistics (modern replacement for `netstat`).  
**Example:**
```bash
ss -tuln
```

---
#### 17. **iptables / ufw / firewalld**
**Purpose:** Configure Linux firewall rules.
- `iptables`: Low-level packet filter tool.
- `ufw`: User-friendly interface for iptables.
- `firewalld`: Dynamic firewall with zone management.

**Examples:**
```bash
sudo iptables -L
sudo ufw allow 22
```
Obs.: Pay attention to this command, because you can block the server connection and you can't access the address anymore.

---
#### 18. **ethtool**
**Purpose:** View or modify Ethernet adapter settings.  
**Example:**
```bash
ethtool eth0
```

---
#### 19. **speedtest-cli**
**Purpose:** Test internet speed from the terminal.  
**Example:**
```bash
speedtest-cli
```
Install on Debian/Ubuntu:
```bash
sudo apt install speedtest-cli
```

---
#### 20. **hping3**
**Purpose:** Create custom TCP/IP packets for firewall testing.  
**Example:**
```bash
hping3 -S -p 80 192.168.1.1
```

Check the installed version:
```bash
hping3 --version
```

---
### My Final Thoughts
These 20 commands are among the **most important tools for networking, cybersecurity, and systems engineers**. Learning them will dramatically improve your troubleshooting skills and help you pass certifications such as:
- CompTIA Network+
- CompTIA Security+
- CCNA
- Linux+ 

For more details, check each command's documentation:
```bash
man <command>
```

Each command shown here deserves an explanation at a later time. For now, I'm listing all for suggestions. But I can describe each one soon.

If you have questions or want deeper tutorials, feel free to reach out. I’d be happy to help!
