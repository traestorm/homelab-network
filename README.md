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

## Not committed

- Private keys (WireGuard, TLS)
- ISP credentials
- Any `.env` files

# Components

| Component | Tech | Status |
|---|---|---|
| VPN | WireGuard | 🚧 |
| Firewall | nftables | 🚧 |
| DNS | systemd-resolved / dnsmasq | 🚧 |
| DHCP | dnsmasq / systemd-networkd | 🚧 |
| Routing | static (OSPF later) | 🚧 |
| Certs | mkcert (internal) / acme.sh (public) | 🚧 |

## Quick Start

```bash
# 1. Load firewall rules
sudo nft -f nftables/ruleset.nft

# 2. Start WireGuard
sudo systemctl enable --now wireguard

# 3. Configure DNS
sudo cp dns/zones/* /etc/resolvconf/zones/
sudo systemctl restart systemd-resol
```
