Configure Port Security – MAC Address Binding
📌 What is Port Security?

Port Security is a Layer 2 security feature on Cisco switches that prevents unauthorized devices from connecting to the network.

It works by allowing only specific MAC addresses to communicate through a switch port.

🎯 What is MAC Address Binding?

MAC Address Binding means manually assigning (binding) a specific MAC address to a switch port.

If another device with a different MAC address connects to that port, the switch will trigger a security violation.

🛠 Configuration Example
Step 1: Enter Interface Configuration Mode (first switch0)

Switch> enable
Switch# configure terminal
Switch(config)# interface range fastEthernet 0/1-2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security maximum 2
Switch(config-if)# switchport port-security mac-address sticky
Switch(config-if)# switchport port-security violation Restrict

Step 2: Enter Interface Configuration Mode (second switch1)

Switch> enable
Switch# configure terminal
Switch(config)# interface range fastEthernet 0/1-2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security maximum 2
Switch(config-if)# switchport port-security mac-address sticky
Switch(config-if)# switchport port-security violation Restrict

🔎 Verification Commands
Switch# show port-security interface fa0/1
Switch# show port-security address

Router Configuration – DHCP + Interface Setup
Step 1️⃣ Enter Global Configuration Mode

Router> enable
Router# configure terminal

Step 2️⃣ Configure DHCP Excluded Addresses

(Reserved IP addresses for gateway, servers, or manual assignments)


Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
Router(config)# ip dhcp excluded-address 192.168.2.1 192.168.2.10

Step 3️⃣ Configure DHCP Pool for Network 192.168.1.0/24

Router(config)# ip dhcp pool IP_COMMON
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit

Step 4️⃣ Configure DHCP Pool for Network 192.168.2.0/24

Router(config)# ip dhcp pool IP_COMMON2
Router(dhcp-config)# network 192.168.2.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.2.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit

Step 5️⃣ Configure Router Interfaces

Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface FastEthernet0/1
Router(config-if)# ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Step 6️⃣ Verification Commands

Router# show ip dhcp binding
Router# show ip dhcp pool
Router# show ip interface brief

✅ Why is Port Security Important?

✔ Prevents unauthorized device access
✔ Protects against MAC flooding attacks
✔ Enhances internal network security
✔ Ideal for office, campus, and enterprise networks

👨‍💻 Author

Farid M
Cybersecurity Student


