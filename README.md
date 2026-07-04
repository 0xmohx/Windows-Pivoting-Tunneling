# Windows Pivoting & Tunneling

> A hands-on documentation project covering Windows Pivoting, SSH Tunneling, SOCKS Proxies, Port Forwarding, and Multi-hop Pivoting techniques practiced in authorized laboratory environments.

---

# Overview

This repository documents my practical work while studying Windows Pivoting, Tunneling, and Port Forwarding.

The focus is not only on executing commands, but also on understanding the networking concepts, attack paths, and decision-making process required to move through segmented enterprise networks.

The labs included in this repository demonstrate how an initial foothold can be leveraged to enumerate internal networks, establish SSH tunnels, create SOCKS proxies, perform lateral movement, and ultimately access isolated systems through multiple pivot points.

---

# Objectives

- Understand enterprise network segmentation.
- Perform internal network enumeration.
- Practice SSH Local, Remote, and Dynamic Port Forwarding.
- Build SOCKS proxies using OpenSSH.
- Perform Nested (Multi-hop) Pivoting.
- Access isolated Windows hosts through multiple pivot points.
- Practice lateral movement across segmented networks.
- Document the complete attack path in a reproducible manner.

---

# Skills Demonstrated

- Network Enumeration
- Linux Enumeration
- Windows Enumeration
- SSH Authentication
- SSH Local Port Forwarding (`ssh -L`)
- SSH Remote Port Forwarding (`ssh -R`)
- SSH Dynamic Port Forwarding (`ssh -D`)
- SOCKS Proxy Creation
- ProxyChains
- Nested (Multi-hop) Pivoting
- Lateral Movement
- Credential Discovery
- LSASS Memory Analysis
- Windows Remote Desktop (RDP)
- Internal Network Mapping
- Attack Path Documentation

---

# Tools Used

| Tool | Purpose |
|------|----------|
| Nmap | Host and service enumeration |
| OpenSSH | SSH tunneling and port forwarding |
| ProxyChains | Route traffic through SOCKS proxies |
| xfreerdp | Remote Desktop access |
| pypykatz | Offline LSASS credential extraction |
| Draw.io | Network topology diagrams |
| Kali Linux | Attacker workstation |

---

# Repository Structure

```text
Windows-Pivoting-Tunneling/
│
├── diagrams/
│   ├── network-map.drawio
│   ├── network-map.png
│   └── README.md
│
├── images/
│   └── HTB/
│       └── Pivoting-Tunneling-Skills-Assessment/
│           ├── 01-web-shell.png
│           ├── 02-webadmin-key.png
│           ├── 03-ssh-pivot.png
│           ├── 04-internal-enumeration.png
│           ├── 05-rdp-login.png
│           ├── 06-lsass-dump.png
│           ├── 07-pypykatz-creds.png
│           ├── 08-second-network-scan.png
│           ├── 09-nested-pivot.png
│           └── 10-final-access.png
│
├── labs/
│   └── HTB/
│       └── Pivoting-Tunneling-Skills-Assessment.md
│
├── LICENSE
└── README.md
```

---

# Included Labs

| Platform | Lab | Status |
|----------|-----|--------|
| HTB Academy | Pivoting, Tunneling & Port Forwarding Skills Assessment | ✅ Completed |

---

# Network Topology

The network diagram used throughout the lab is available in:

```text
diagrams/network-map.drawio
```

A rendered version is also included:

```text
diagrams/network-map.png
```

---

# Key Learning Outcome

One of the most valuable concepts practiced throughout this project was **Nested Pivoting**.

There is an important distinction between:

- Using **ProxyChains** to route traffic through an existing SOCKS proxy.
- Creating a **new SOCKS proxy** with `ssh -D`.

Every successful SSH connection can become a new pivot point capable of reaching additional internal networks.

```text
                 Kali
                   │
          SSH -D 9050
                   │
            Pivot Host #1
                   │
          SSH -D 1081
                   │
            Pivot Host #2
                   │
          Internal Network
```

This layered approach allows access to progressively deeper network segments while maintaining a controlled attack path.

Although multiple nested SSH tunnels are technically possible, each additional hop introduces latency and increases operational complexity. In larger environments, dedicated tunneling frameworks such as **Ligolo-ng**, **Chisel**, or **WireGuard** are often preferred for their scalability and ease of management.

---

# Future Additions

This repository will continue to expand with additional Windows Pivoting and Tunneling scenarios, including:

- Reverse Port Forwarding
- Chisel
- Ligolo-ng
- Socat
- Meterpreter Pivoting
- WinRM Pivoting
- SMB Pivoting
- SOCKS over Meterpreter
- Multi-Forest Pivoting
- Active Directory Pivoting

---

# Disclaimer

This repository is intended for educational purposes only.

All techniques were practiced in authorized laboratory environments, including Hack The Box Academy.

No challenge flags, sensitive information, or active exploitation targets are included. The focus is on methodology, documentation, and defensive understanding of pivoting techniques.
