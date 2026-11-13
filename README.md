# Homelab Network

Network-layer configuration for my home lab. Network-first approach:
this repo must be working before any VMs or containers exist.

## Topology

```
[ISP Router]
    │
[Homelab Firewall/Router]  ← nftables, WireGuard server
    │
[Switch]
    ├── [Server: DNS, DHCP, Certs]
    ├── [Server: VMs/Containers]
    └── [Client devices]
```
