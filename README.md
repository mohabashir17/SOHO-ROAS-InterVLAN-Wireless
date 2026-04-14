# SOHO-ROAS-InterVLAN-Wireless

## Enterprise SOHO Network Deployment | VLAN Segmentation | ROAS | Wireless Integration

---

## Project Overview

This project implements a **Small Office/Home Office (SOHO)** network with three departments: Guest/Sales (VLAN 10), IT (VLAN 20), and Administration (VLAN 30). The network features:

- **Router-on-a-Stick (ROAS)** for inter-VLAN routing
- **802.1Q trunking** between switch and router
- **Department-specific wireless access points**
- **VLAN isolation** at Layer 2 with routing at Layer 3

---

## Network Topology

[Network Topology](https://github.com/mohabashir17/SOHO-ROAS-InterVLAN-Wireless/blob/main/Topology.png)

---

## IP Addressing Scheme

| Department     | VLAN ID | Subnet         | CIDR | Gateway         | Host Range     |
|----------------|--------|----------------|------|------------------|----------------|
| Guest/Sales    | 10     | 192.168.1.0    | /26  | 192.168.1.1      | .1 - .62       |
| IT             | 20     | 192.168.1.64   | /26  | 192.168.1.65     | .65 - .126     |
| Administration | 30     | 192.168.1.128  | /26  | 192.168.1.129    | .129 - .190    |

**Subnet Mask:** 255.255.255.192  
**Available IPs per subnet:** 62

---

## Technologies Implemented

| Technology                 | Purpose                          |
|--------------------------|----------------------------------|
| VLAN 10, 20, 30          | Department isolation             |
| 802.1Q Trunking          | Carry multiple VLANs to router   |
| Router-on-a-Stick (ROAS) | Inter-VLAN routing               |
| Wireless Access Points   | Department-specific WiFi         |
| DHCP (optional)          | Dynamic IP allocation            |

---


## Verification

All verification outputs are available here:  
👉 [View Verification Results](https://github.com/mohabashir17/SOHO-ROAS-InterVLAN-Wireless/blob/main/Verfications.md)

---

## Configurations

All device configurations can be accessed here:  
👉 [View Device Configurations](https://github.com/mohabashir17/SOHO-ROAS-InterVLAN-Wireless/tree/main/Configs)

---

## How to Use This Project

### Prerequisites
- Cisco Packet Tracer 8.0 or higher  
- Basic understanding of VLANs and routing  

### Steps
1. Clone or download this repository  
2. Open `SOHO.pkt` in Cisco Packet Tracer  
3. Allow devices to fully boot  
4. Test connectivity between VLANs  

---

## Project Structure

```text
SOHO-ROAS-InterVLAN-Wireless/
├── SOHO.pkt
├── Topology.png
├── README.md
├── Verfications.md
└── Configs/
```

---

## Author

Mohamed Bashir Ali

---

## License

This project is for educational and portfolio purposes.
