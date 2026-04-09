---
# VPS Troubleshooting Guide

[![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-blue.svg)](LICENSE)

> Complete guide for VPS server management and monitoring.

---

## Common Issues

| Issue | Solution | Severity |
|-------|----------|----------|
| SSH Failed | VNC Console | CRITICAL |
| CPU High | kill process | HIGH |
| Memory Full | clear cache | HIGH |
| Disk Full | clean logs | MEDIUM |
| Network Down | check firewall | MEDIUM |

---

## SSH Connection

Use VNC Console from your VPS provider to access server.

```bash
systemctl status sshd
systemctl restart sshd
sshd -t
netstat -tlnp | grep 22
```

### Firewall

```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
ufw allow 22/tcp
firewall-cmd --add-port=22/tcp --permanent
```

---

## CPU High

```bash
top -c
ps aux --sort=-%cpu | head -20
kill -9 PID
```

## Memory Full

```bash
free -h
sync && echo 3 > /proc/sys/vm/drop_caches
dmesg | grep -i memory
```

### Create Swap

```bash
fallocate -l 2G /swapfile && chmod 600 /swapfile && mkswap /swapfile && swapon /swapfile
```
---
## Disk
df -h
---
## Disk
df -h
du -sh /*
apt clean
journalctl --vacuum
---
## Network
nslookup google.com
ping -c 4 8.8.8.8
echo nameserver 8.8.8.8 > /etc/resolv.conf
iptables -F
---
## Data Protection
Use provider snapshots: Vultr, DO, Linode
rsync -avz /var/www /backup/
---
## Prevention
Monitoring script:
CPU=$(top -bn1 | awk NR==2{print int($2)})
if [ $CPU -gt 90 ]; then echo Alert; fi
Backup: tar -czf /backup/www.tar.gz /var/www
Cron: */5 * * * * /path/monitor.sh
---
## Links
https://vpsvip.net
https://nav.clashvip.net
CC BY-NC-SA 4.0
