
# Linux Cheat-Sheet (Task 1)

## Files & Directories
- `pwd` – where am I
- `ls -la` – list with perms
- `cd /path` – move
- `mkdir -p a/b/c`
- `touch file.txt`
- `cp src dst` | `mv src dst`
- `rm -rf <path>` (careful!)

## Permissions & Ownership
- `chmod 755 file` (rwx r-x r-x)
- `chown user:group file`
- `umask` – default perms mask

## Viewing & Searching
- `cat`, `less`, `head`, `tail -f`
- `grep -R "pattern" .`
- `find . -type f -name "*.log"`

## Packages & Services (Debian/Kali)
- `sudo apt update && sudo apt upgrade -y`
- `sudo apt install wireshark nmap burpsuite netcat-traditional traceroute git -y`
- `systemctl status <svc>` | `systemctl start/stop <svc>`

## Networking
- `ip a` – addresses
- `ip r` – routes
- `ping <ip>`
- `traceroute <host>`
- `ss -tulpen` – listening sockets
- `curl -I https://example.com`

## Users & Processes
- `adduser <name>`
- `passwd <name>`
- `ps aux | grep <proc>`
- `top` / `htop`

## Archiving
- `tar -czf archive.tgz folder/`
- `tar -xzf archive.tgz`

## Git Basics
- `git init`
- `git add .`
- `git commit -m "Task 1 setup"`
- `git branch -M main`
- `git remote add origin <repo-url>`
- `git push -u origin main`
