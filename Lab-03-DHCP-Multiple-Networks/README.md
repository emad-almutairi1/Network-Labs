# Lab 03: Configure DHCP Server in Packet Tracer (Part 02)

## Objective
- Create multiple DHCP pools for different networks.
- Configure DHCP to assign IP addresses dynamically.
- Understand why DHCP requests from remote networks fail without DHCP Relay.
- Configure the router to forward DHCP requests using `ip helper-address`.
- Test connectivity using ping, including broadcast IP addresses.
- Add an extra network and switch as a bonus exercise.

## Equipment / Tools
- Cisco Packet Tracer
- 1 Cisco 2911 Router
- 3 Switches (including the bonus switch)
- 1 DHCP Server
- PCs and laptops
- Ethernet cables

## Network Topology

The topology contains three networks connected through one router.

| Network | Network Address | Subnet Mask | Addressing |
|---|---|---|---|
| Network 1 | `192.168.5.0/24` | `255.255.255.0` | DHCP Server |
| Network 2 | `10.0.0.0/8` | `255.0.0.0` | DHCP Server |
| Network 3 | `172.16.0.0/16` | `255.255.0.0` | DHCP Server |

## Step-by-Step Procedure

### Step 1: Create the Topology
- Place one Cisco 2911 router, three switches, one DHCP server, and the end devices.
- Connect the DHCP server and two PCs to Switch0.
- Connect the devices in Network 2 to Switch1.
- Connect two PCs to Switch2 for Network 3.
- Connect all three switches to separate router interfaces.
- Configure the appropriate cabling and verify that the links are active.

### Step 2: Configure the Router
- Assign an IP address to each router interface according to its network.
- Enable each interface using the `no shutdown` command.
- Configure the DHCP server with a static IP address and the correct default gateway.

### Step 3: Configure the DHCP Server
- Open **Services > DHCP**.
- Enable the DHCP service.
- Create a separate DHCP pool for each network.
- Configure the default gateway, subnet mask, starting IP address, and maximum number of users for each pool.
- Ensure that the DHCP server has a static IP address and does not receive its address from its own DHCP pool.

### Step 4: Configure Network 1
- Set the PCs in Network 1 to obtain their IP addresses automatically.
- Verify that the PCs receive valid addresses from the DHCP server.
- Test connectivity using `ping`.

### Step 5: Configure DHCP for Network 2
- Initially, DHCP requests from Network 2 fail because DHCP broadcasts do not normally cross routers.
- Configure DHCP Relay on the router interface connected to Network 2 using the `ip helper-address` command.
- Set the helper address to the DHCP server's IP address.
- Renew the PCs' DHCP addresses and verify connectivity.

### Step 6: Add Network 3 (Bonus)
- Add the third switch and connect it to the router.
- Connect the Network 3 PCs to the new switch.
- Configure the router interface for `172.16.0.0/16`.
- Create a third DHCP pool on the DHCP server for Network 3.
- Configure `ip helper-address` on the router interface connected to Network 3.
- Set the PCs to DHCP and verify that they receive addresses from the correct pool.

### Step 7: Test Broadcast IP
- Identify the broadcast address of each network.
- Use the `ping` command to test the broadcast address where supported.
- Observe the results and understand that routers generally do not forward directed broadcasts by default.

## Verification
- Verify that all router interfaces are up.
- Check that each PC receives an IP address from the correct subnet.
- Verify the default gateway and subnet mask.
- Test communication between devices using `ping`.
- Confirm that DHCP works across all three networks after configuring DHCP Relay.

## Conclusion
This lab demonstrates how to configure multiple DHCP pools, assign IP addresses dynamically, and use DHCP Relay to support clients on different networks. The bonus exercise extends the original topology by adding a third switch and network.
