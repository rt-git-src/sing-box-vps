## Prepare
- get a VPS, e.g. [HostVDS](https://hostvds.com/)
- add a subdomain, e.g. [here](https://freedns.afraid.org/), and relate it with the VPS's IP
- `ssh root@your_vps_ip`

## Setup container files
```
apt update && \
apt upgrade -y && \
apt install podman-compose certbot && \
certbot certonly --register-unsafely-without-email --standalone -d vpn.yourdomain.com && \
systemctl enable certbot.timer && \
systemctl start certbot.timer && \
mkdir -p container && \
cd container && \
wget bit.ly/sing-box-compose-yaml -O compose.yaml && \
wget bit.ly/sing-box-server-json -O sing-box/config/server.json
```

## Edit config and run
- add domain and passwords to `server.json`
- `podman compose up -d`
