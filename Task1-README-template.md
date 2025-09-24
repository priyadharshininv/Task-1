
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
