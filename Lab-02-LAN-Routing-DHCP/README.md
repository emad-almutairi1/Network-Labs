# Lab 02: Connecting Three LANs Using a Router and DHCP

## Overview
This lab demonstrates how to connect three Local Area Networks (LANs) using a Cisco 2911 router in Cisco Packet Tracer. It covers static IP addressing, DHCP configuration, and communication between different networks.

## Objectives
- Connect three LANs using a router.
- Configure static IP addresses for network devices.
- Configure a DHCP server for dynamic IP addressing.
- Configure DNS and HTTP servers.
- Verify communication between networks.

## Tools and Equipment
- Cisco Packet Tracer
- 1 Cisco 2911 Router
- 2 Switches
- 6 PCs
- 1 DHCP Server
- 1 DNS Server
- 1 HTTP Server
- Ethernet cables

## Network Configuration

| Network | IP Address Range | Configuration |
|---|---|---|
| Easy-Network | 192.168.1.0/24 | DHCP |
| Hard-Network | 192.168.2.0/24 | Static IP |
| Service Network | 10.0.0.0/8 | Static IP |

## Servers
- **DHCP Server:** Assigns IP addresses dynamically to Easy-Network clients.
- **DNS Server:** 10.0.0.3
- **HTTP Server:** 10.0.0.2

## Implementation
1. Create the network topology in Cisco Packet Tracer.
2. Connect the three switches to the router interfaces G0/0, G0/1, and G0/2.
3. Configure the router interfaces and IP addresses.
4. Configure the DHCP server and address pool.
5. Assign static IP addresses to Hard-Network devices.
6. Configure the DNS and HTTP services.
7. Test connectivity between networks and access the HTTP server.

## Expected Results
- Easy-Network clients receive IP addresses automatically through DHCP.
- Hard-Network devices use manually configured IP addresses.
- Devices can communicate across the three networks.
- DNS resolution and HTTP access work correctly after proper configuration.

## Software
Cisco Packet Tracer

