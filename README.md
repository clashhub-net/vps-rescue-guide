# VPS Troubleshooting Guide

[![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-blue.svg)](LICENSE)

> Complete guide for VPS fault diagnosis and troubleshooting

## Common Issues

| Issue | Solution |
|-------|----------|
| SSH Failed | VNC Console |
| CPU 100% | kill process |
| Disk Full | apt clean |
| Memory Full | free -h |

## SSH Troubleshooting

```bash
systemctl status sshd
systemctl restart sshd
netstat -tlnp | grep 22
```

## Firewall

```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
ufw allow 22/tcp
```

## Resources

- https://vpsvip.net
- https://clash-for-windows.net
- https://nav.clashvip.net

## License

CC BY-NC-SA 4.0
