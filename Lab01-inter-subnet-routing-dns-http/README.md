# Lab 01: Inter-Subnet Routing with Dedicated DNS and HTTP Servers

## Overview
This repository contains a Cisco Packet Tracer laboratory setup demonstrating inter-subnet routing using a Cisco 2911 Router to connect three distinct Local Area Networks (LANs). The design includes a dedicated services subnet hosting an HTTP Web Server and a DNS Server.

---

## Network Topology & Design

The network is partitioned into three main subnets connected through `Router3`:

1. **Subnet 1 (`192.168.1.0/24`):**
   - **Switch0** connecting end-user devices (`192.168.1.10`, `192.168.1.11`).
2. **Subnet 2 (`192.168.2.0/24`):**
   - **Switch1** connecting end-user devices (`192.168.2.10`, `192.168.2.11`).
3. **Subnet 3 (`192.168.3.0/24`):**
   - **Switch3** connecting a client PC (`192.168.3.10`), a **DNS Server** (`DnsServer`), and an **HTTP Web Server** (`httpServer`).

---

## IP Addressing Table

| Device Name | Interface | IP Address | Subnet Mask | Default Gateway | DNS Server |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Router1** | Gig0/0 | `192.168.1.1` | `255.255.255.0` | N/A | N/A |
| **Router2** | Gig0/1 | `192.168.2.1` | `255.255.255.0` | N/A | N/A |
| **Router3** | Gig0/2 | `192.168.3.1` | `255.255.255.0` | N/A | N/A |
| **PC-PT (Subnet 1)** | FastEthernet0 | `192.168.1.10` | `255.255.255.0` | `192.168.1.1` | `192.168.3.X` |
| **Laptop-PT (Subnet 1)** | FastEthernet0 | `192.168.1.11` | `255.255.255.0` | `192.168.1.1` | `192.168.3.X` |
| **Laptop-PT (Subnet 2)** | FastEthernet0 | `192.168.2.10` | `255.255.255.0` | `192.168.2.1` | `192.168.3.X` |
| **PC-PT (Subnet 2)** | FastEthernet0 | `192.168.2.11` | `255.255.255.0` | `192.168.2.1` | `192.168.3.X` |
| **PC-PT (Subnet 3)** | FastEthernet0 | `192.168.3.10` | `255.255.255.0` | `192.168.3.1` | `192.168.3.X` |
| **DnsServer** | FastEthernet0 | `192.168.3.X` | `255.255.255.0` | `192.168.3.1` | `192.168.3.X` |
| **httpServer** | FastEthernet0 | `192.168.3.Y` | `255.255.255.0` | `192.168.3.1` | `192.168.3.X` |

*(Note: Replace `192.168.3.X` and `192.168.3.Y` with the exact static IPs assigned to your DNS and HTTP servers).*

---

## Key Configurations & Verification

1. **Inter-Subnet Routing:**
   - Configured interface gateways on `Router3` (`Gig0/0`, `Gig0/1`, `Gig0/2`).
   - Verified full end-to-end ICMP reachability (`ping`) across all three subnets.

2. **DNS & HTTP Services:**
   - Configured an **A Record** on the `DnsServer` mapping the domain name (e.g., `www.example.com`) to the `httpServer` IP address.
   - Set the DNS Server IP on all host computers across all subnets.
   - Tested HTTP access from client devices in Subnet 1 and Subnet 2 via the web browser using the domain name.

---

## File Structure

```text
.
├── Lab05-Topology.pkt      # Cisco Packet Tracer project file
├── README.md               # Documentation and execution steps
└── screenshots/            # Verification screenshots (Ping tests & HTTP browser output)