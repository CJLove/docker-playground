# Docker networking playground

Test container with networking tools and docker compose file for deploying it with various Docker network configurations
- `bridgeNet` - 172.20.20.0/24
- `nodeNet` - 192.168.1.0/24 with macvlan connection to an interface on the host on this same subnet


## Verifying connectivity with Netcat (nc)

- TCP
Server
```
socat -v tcp-l:5000,fork exec:'/bin/cat'
```

Client
```
nc <IP addr> 5000
```

- UDP
Server
```
socat -v PIPE udp-recvfrom:5000,fork
```
```
socat - udp:localhost:5000
```