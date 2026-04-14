# SOHO-ROAS-InterVLAN-Wireless

## Enterprise SOHO Network Deployment | VLAN Segmentation | ROAS | Wireless Integration

---

## Project Overview

This project implements a **Small Office/Home Office (SOHO)** network with three departments: Guest/Sales (VLAN 10), IT (VLAN 20), and Management (VLAN 30). The network features:

- **Router-on-a-Stick (ROAS)** for inter-VLAN routing
- **802.1Q trunking** between switch and router
- **Department-specific wireless access points**
- **VLAN isolation** at Layer 2 with routing at Layer 3

---

## Network Topology

![Network Topology](diagram.png)

---

## IP Addressing Scheme

| Department | VLAN ID | Subnet | CIDR | Gateway | Host Range |
|------------|---------|--------|------|---------|------------|
| Guest/Sales | 10 | 192.168.1.0 | /26 | 192.168.1.1 | .1 - .62 |
| IT | 20 | 192.168.1.64 | /26 | 192.168.1.65 | .65 - .126 |
| Management | 30 | 192.168.1.128 | /26 | 192.168.1.129 | .129 - .190 |

**Subnet Mask:** 255.255.255.192  
**Available IPs per subnet:** 62

---

## Technologies Implemented

| Technology | Purpose |
|------------|---------|
| VLAN 10, 20, 30 | Department isolation |
| 802.1Q Trunking | Carry multiple VLANs to router |
| Router-on-a-Stick (ROAS) | Inter-VLAN routing using subinterfaces |
| Wireless Access Points | Department-specific WiFi |
| DHCP (optional) | Dynamic IP allocation |

---

## Router Configuration (ROAS)
interface GigabitEthernet0/0.10
encapsulation dot1Q 10
ip address 192.168.1.1 255.255.255.192
no shutdown

interface GigabitEthernet0/0.20
encapsulation dot1Q 20
ip address 192.168.1.65 255.255.255.192
no shutdown

interface GigabitEthernet0/0.30
encapsulation dot1Q 30
ip address 192.168.1.129 255.255.255.192
no shutdown

