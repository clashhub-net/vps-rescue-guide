# VPS Troubleshooting Guide

## Common Issues

| Issue | Solution |
|-------|----------|
| SSH Failed | VNC Console |
| CPU 100% | kill process |
| Memory Full | free -h |
| Disk Full | apt clean |

## SSH Connection

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
