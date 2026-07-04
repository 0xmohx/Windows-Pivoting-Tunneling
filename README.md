# Windows-Pivoting-Tunneling

> Documentation of my hands-on practice with Windows network pivoting, SSH tunneling, SOCKS proxies, and multi-hop access techniques in a controlled lab environment.

## Overview

This repository documents my practical work while studying Windows Pivoting, Tunneling, and Port Forwarding.

The project focuses on understanding how segmented enterprise networks can be accessed through multiple pivot points using SSH tunnels and SOCKS proxies. Rather than simply documenting commands, the goal is to explain the methodology, networking concepts, and decision-making process behind each pivot.

During this lab I successfully chained multiple SSH tunnels, built nested SOCKS proxies, enumerated internal networks, and reached isolated Windows systems through several pivot hosts.

---

## Objectives

- Understand enterprise network segmentation.
- Perform internal network enumeration.
- Practice SSH Local, Remote and Dynamic Port Forwarding.
- Build SOCKS proxies using OpenSSH.
- Perform Nested (Multi-hop) Pivoting.
- Access isolated Windows hosts through multiple pivot points.
- Document the complete attack path.

---

## Skills Demonstrated

- Network Enumeration
- SSH Pivoting
- Dynamic Port Forwarding (`ssh -D`)
- Local Port Forwarding (`ssh -L`)
- Remote Port Forwarding (`ssh -R`)
- SOCKS Proxy Chaining
- ProxyChains
- Multi-hop Pivoting
- Windows Remote Desktop Pivoting
- Internal Network Mapping
- Attack Path Documentation

---

## Tools Used

| Tool | Purpose |
|------|----------|
| Nmap | Host and service enumeration |
| OpenSSH | SSH tunneling and port forwarding |
| ProxyChains | Route tools through SOCKS proxies |
| xfreerdp | Remote Desktop access |
| Draw.io | Network topology diagrams |
| Kali Linux | Attacker workstation |

---

## Repository Structure

```
Windows-Pivoting-Tunneling/
│
├── diagrams/
│   ├── network-map.drawio
│   ├── network-map.png
│   └── README.md
│
├── images/
│
├── labs/
│   └── HTB/
│       └── Pivoting-Tunneling-Skills-Assessment.md
│
├── LICENSE
└── README.md
```

---

## Network Topology

The complete network map used during the lab can be found in:

```
diagrams/network-map.drawio
```

A rendered image is also available:

```
diagrams/network-map.png
```

---

## Key Learning Outcome

One of the most valuable concepts learned during this project was **Nested Pivoting**.

There is an important difference between:

- Connecting to an existing SOCKS proxy using ProxyChains.
- Creating a new SOCKS proxy with `ssh -D`.

Each successful SSH connection can become a new pivot point capable of reaching additional internal networks.

Example:

```
Kali
 │
SSH Pivot #1
 │
SSH Pivot #2
 │
SSH Pivot #3
 │
Internal Network
```

Every new SSH session can expose another internal network while creating another SOCKS endpoint for the next hop.

Although multiple nested tunnels are technically possible, long SSH chains increase latency and operational complexity. In larger environments, dedicated tunneling solutions such as Ligolo-ng or Chisel are often preferred.

---

## Disclaimer

This repository is intended for educational purposes only.

All techniques were practiced in authorized laboratory environments such as Hack The Box Academy.

No sensitive information, credentials, or challenge flags are included in this repository.
