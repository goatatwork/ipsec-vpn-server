Source:
https://github.com/hwdsl2/docker-ipsec-vpn-server

To start the VPN server:
```
docker run \
    --name ipsec-vpn-server \
    --env VPN_IPSEC_PSK=<preshared-key> \
    --env VPN_USER=<username> \
    --env VPN_PASSWORD=<vpn-user-password> \
    --env VPN_DNS_SRV1=8.8.8.8 \
    --env VPN_DNS_SRV2=1.1.1.1 \
    --restart=always \
    -p 500:500/udp \
    -p 4500:4500/udp \
    -v /lib/modules:/lib/modules:ro \
    -d --privileged \
    hwdsl2/ipsec-vpn-server
```

Alternatively, an environment file can be used:
```
docker run \
    --name ipsec-vpn-server \
    --env-file ./dot-env \
    --restart=always \
    -p 500:500/udp \
    -p 4500:4500/udp \
    -v /lib/modules:/lib/modules:ro \
    -d --privileged \
    hwdsl2/ipsec-vpn-server
```