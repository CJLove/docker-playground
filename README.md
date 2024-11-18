# Docker networking playground

## Host Setup

- vlan interface(s) defined relative to actual device (e.g. enp1s0)
  - `x-vm-net` 11.0.1.0/24
  - `test-net` 10.20.20.0/24
  - `test2-net` 10.30.30.0/24

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

Client
```
socat - udp:localhost:5000
```