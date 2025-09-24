
# Task 1 – Foundations of Cybersecurity (Days 1–12)

This README is a fill-in template for your ApexPlanet internship Task 1 submission. Replace placeholders with your own details and screenshots.

## 1) Lab Overview
- **Goal:** Build a safe, isolated hacking lab and learn Linux, networking, crypto, and core tools.
- **Topology:** Kali (attacker) ↔ Metasploitable2 (target) on a Host-Only network; Kali also has NAT for internet updates.

```
        Internet
           |
         [NAT]
           |
        [Kali]
           |  Host-Only (e.g., 192.168.56.0/24)
      -------------
           |
    [Metasploitable2]
```

## 2) VM Specs
| VM | Role | CPU/RAM | Disk | Network | IP |
|----|------|---------|------|---------|----|
| Kali Linux | Attacker workstation | 2 vCPU / 4GB+ | 30GB+ | Adapter 1: NAT, Adapter 2: Host-Only | 192.168.56.10x |
| Metasploitable2 | Vulnerable target | 1 vCPU / 1GB | 10GB | Adapter 1: Host-Only | 192.168.56.10y |

> Replace IPs with your actual addresses.

## 3) Setup Steps (brief)
1. Create **Host-Only** network in VirtualBox (e.g., `192.168.56.0/24`, DHCP on).
2. Install **Kali** with **two adapters** (NAT + Host-Only). Update packages.
3. Import **Metasploitable2** OVA; set **Host-Only** adapter. Note its IP (`ifconfig`/`ip a`).
4. Test connectivity: from Kali → `ping <metasploitable-ip>`.

## 4) Linux Fundamentals (commands I practiced)
- Navigation: `pwd`, `ls -la`, `cd`, `cat`, `head`, `tail`, `less`
- Files/Perms: `touch`, `mkdir`, `rm -rf`, `cp`, `mv`, `chmod`, `chown`
- Packages: `sudo apt update && sudo apt upgrade -y`, `apt install`, `dpkg -i <pkg.deb>`
- Networking: `ip a`, `ip r`, `ping`, `traceroute`, `netstat -tulpen` or `ss -tulpen`
- Processes: `ps aux`, `top`/`htop`, `kill`, `systemctl status`

## 5) Networking Basics (notes I wrote)
- OSI vs TCP/IP mapping
- IP/Subnetting example I solved
- DNS and HTTP/HTTPS summary

## 6) Cryptography Basics (OpenSSL hands-on)
- Hash: `echo -n "text" | sha256sum`
- Symmetric enc/dec:
  - `openssl enc -aes-256-cbc -md sha256 -pbkdf2 -salt -iter 100000 -in msg.txt -out msg.enc`
  - `openssl enc -d -aes-256-cbc -md sha256 -pbkdf2 -iter 100000 -in msg.enc -out msg.dec.txt`
- Asymmetric (RSA):
  - `openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048`
  - `openssl rsa -in private.pem -pubout -out public.pem`
  - Encrypt: `openssl pkeyutl -encrypt -pubin -inkey public.pem -in msg.txt -out msg.rsa.enc`
  - Decrypt: `openssl pkeyutl -decrypt -inkey private.pem -in msg.rsa.enc -out msg.rsa.dec.txt`

## 7) Tools I tried
- **Wireshark**: capture on Host-Only interface; filter `icmp` while pinging target.
- **Nmap**: `nmap -sn 192.168.56.0/24` (host discovery) — full scans in Task 2.
- **Burp Suite**: launched Community Edition and configured browser proxy for later tasks.
- **Netcat**: `nc -lvp 4444` and `echo hello | nc <kali-ip> 4444` for a quick demo.

## 8) Screenshots Checklist (attach in `/screenshots`)
- Kali desktop + `ip a` showing Host-Only IP
- Metasploitable2 console showing IP
- Successful `ping` from Kali → Metasploitable
- Wireshark ICMP capture

## 9) Video Plan (≈5 min)
1. Show topology and VM settings (NAT + Host-Only).
2. Show Kali + Metasploitable IPs; demo ping.
3. Quick Wireshark capture demo.
4. Close with where the notes/cheat-sheet live in the repo.

## 10) Repo Structure (suggested)
```
task-1/
  README.md
  linux-cheatsheet.md
  notes/
    networking-notes.md
    crypto-notes.md
  screenshots/
    kali-ip.png
    metasploitable-ip.png
    ping.png
    wireshark-icmp.png
```

## 11) Ethics
Use this lab **only** in your isolated environment and for learning. Do not scan systems you don’t own or have written permission to test.

---

### Fill below with your own notes
- What I learned today:
- Issues I faced and fixes:
- Next steps:
