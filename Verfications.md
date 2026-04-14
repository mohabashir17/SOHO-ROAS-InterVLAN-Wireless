# Verification Outputs

---

## 1. VLAN Configuration (SW1)

```bash
SW1#show vlan brief

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/10, Fa0/11, Fa0/12, Fa0/13
                                                Fa0/14, Fa0/15, Fa0/16, Fa0/17
                                                Fa0/18, Fa0/19, Fa0/20, Fa0/21
                                                Fa0/22, Fa0/23, Fa0/24, Gig0/2
10   Guest/Sales                      active    Fa0/1, Fa0/2, Fa0/3
20   IT                               active    Fa0/4, Fa0/5, Fa0/6
30   Administration                   active    Fa0/7, Fa0/8, Fa0/9
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
SW1#
```

---

## 2. Trunk Interface (SW1 ↔ R1)

```bash
SW1#show interfaces trunk

Port        Mode         Encapsulation  Status        Native vlan
Gig0/1      on           802.1q         trunking      1

Port        Vlans allowed on trunk
Gig0/1      10,20,30

Port        Vlans allowed and active in management domain
Gig0/1      10,20,30

Port        Vlans in spanning tree forwarding state and not pruned
Gig0/1      10,20,30
```

---

## 3. Router-on-a-Stick (ROAS) Configuration

```bash
R1#show ip interface brief

Interface              IP-Address      OK? Method Status                Protocol 
GigabitEthernet0/0     unassigned      YES unset  up                    up 
GigabitEthernet0/0.10  192.168.1.1     YES manual up                    up 
GigabitEthernet0/0.20  192.168.1.65    YES manual up                    up 
GigabitEthernet0/0.30  192.168.1.129   YES manual up                    up 
GigabitEthernet0/1     unassigned      YES unset  administratively down down 
GigabitEthernet0/2     unassigned      YES unset  administratively down down 
Vlan1                  unassigned      YES unset  administratively down down 
```

---

## 4. Routing Table

```bash
R1#show ip route

Gateway of last resort is not set

     192.168.1.0/24 is variably subnetted, 6 subnets, 2 masks

C       192.168.1.0/26   is directly connected, GigabitEthernet0/0.10
L       192.168.1.1/32   is directly connected, GigabitEthernet0/0.10

C       192.168.1.64/26  is directly connected, GigabitEthernet0/0.20
L       192.168.1.65/32  is directly connected, GigabitEthernet0/0.20

C       192.168.1.128/26 is directly connected, GigabitEthernet0/0.30
L       192.168.1.129/32 is directly connected, GigabitEthernet0/0.30
```

---

## 5. Inter-VLAN Ping Test

```bash
PC0 (VLAN 10)> ping 192.168.1.66

Pinging 192.168.1.66 with 32 bytes of data:

Request timed out.
Reply from 192.168.1.66: bytes=32 time<1ms TTL=127
Reply from 192.168.1.66: bytes=32 time<1ms TTL=127
Reply from 192.168.1.66: bytes=32 time<1ms TTL=127

Ping statistics for 192.168.1.66:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

---

## 6. DHCP Bindings

```bash
R1#show ip dhcp binding

IP address       Client-ID/Hardware address   Lease expiration   Type
-----------------------------------------------------------------------
192.168.1.2      00E0.8F52.2D72              --                Automatic
192.168.1.3      0006.2A10.D7B8              --                Automatic
192.168.1.4      0001.63E7.9EDD              --                Automatic
192.168.1.5      0006.2AE3.D9C1              --                Automatic
192.168.1.66     000C.852A.E5C6              --                Automatic
192.168.1.67     0060.3E47.9A90              --                Automatic
192.168.1.68     000B.BE9A.494D              --                Automatic
192.168.1.130    0010.116D.46D8              --                Automatic
192.168.1.131    0090.0CB3.A9EB              --                Automatic
192.168.1.132    0030.F265.7494              --                Automatic
```
