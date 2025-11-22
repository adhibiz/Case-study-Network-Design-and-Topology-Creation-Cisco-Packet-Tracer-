# Network Design and Topology Creation (Cisco Packet Tracer)
## 1. Introduction
This report provides a detailed explanation of a Cisco Packet Tracer network using a router-based DHCP configuration. It includes the network topology, IP addressing, device configuration, and testing results.
## 2. Network Topology Overview
The network consists of multiple switches and end devices connected to a central ISR router that provides DHCP services.
## Devices Used
~~~
- 1 × ISR Router
- 3 × Cisco Switches
- 11 × PCs
- 3 × Servers
- 1 × Meraki Server
~~~
<img width="945" height="1108" alt="image" src="https://github.com/user-attachments/assets/0887ff4b-3e1c-44e6-b3d7-dc41bf61f252" />

 
## 3. IP Addressing Scheme
Network: 192.168.1.0/24
Gateway: 192.168.1.1
## 4. DHCP Configuration on Router
~~~
Router >enable
Router #configure terminal
Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9
Router(config)# ip dhcp pool MYPOOL
Router(dhcp-config)# network 192.168.50.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.50.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
~~~
## 5. Router Interface Configuration
~~~
interface gigabitEthernet0/0
 ip address 192.168.50.1 255.255.255.0
 no shutdown
~~~
## 6. Device (PC & Server) DHCP Settings
Each device should be configured:
Desktop → IP Configuration → DHCP
## 7. Network Connectivity Tests
From any PC2:
ping 192.168.50.16
ping other PCs/servers
 ![Uploading image.png…]()

Successful replies confirm DHCP + routing works.
## 8. Conclusion
The network successfully uses router-based DHCP to automatically assign IP addresses to all devices. Connectivity between devices is verified through ping tests.
