# VPS Troubleshooting

## Issues

| Issue | Solution |
|-------|----------|
| SSH | VNC Console |
| CPU | kill process |
| Disk | apt clean |

## SSH Fix

```bash
systemctl status sshd
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

## Resources

- https://vpsvip.net
- https://nav.clashvip.net

## License

CC BY-NC-SA 4.0
