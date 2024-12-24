# change/set dns in systemd

**1. open /etc/systemd/resolved.conf with editor**
```bash
sudo vim /etc/systemd/resolved.conf
```

**2. choose dns**
- [mullvad](https://mullvad.net/en/help/dns-over-https-and-dns-over-tls) **recommend**
- [cloudflare](https://developers.cloudflare.com/1.1.1.1/ip-addresses/)

**reference:**
- [mullvad](https://mullvad.net/en/help/dns-over-https-and-dns-over-tls)
- [arch-wiki](https://wiki.archlinux.org/title/Domain_name_resolution#DNS_servers)
- [cloudflare](https://developers.cloudflare.com/1.1.1.1/setup/linux/)
