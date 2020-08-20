# Linux Networking
#### August 14, 2020 : Session 020
## Topics to be covered
- Communication Devices
  - Hub
  - Bridge
  - Switch
  - Router
  - Firewall Devices
- IPv4 and IPv6
- CCNA (Cisco Certified Network Associate)
  - MTA
  - MTU
  - Routing Protocols
    - SPF
    - OSPF
    - RIP
- Subnetting
- Telnet, SSH, RDP, FTP, DNS, DHCP, DDNS
- DoS, DDoS, DNS Poisioning
- SMTP, LDAP, Kerberos, NFS, CIFS, GFS

## Bare Requirements for Networking
1. Capability
  - NIC (Network Interface Card)
2. Medium
  - Wired
  - Wireless
    - RF (Radio Frequency)
    - Bluetooth
    - Wifi, Hotspot, etc.
3. Protocol
  - ICMP, TCP, UDP, etc.

## NIC
- Types of Card (Based on Speed):
  - Ethernet Card (10 Mbps)
  - Fast Ethernet Card (100 Mbps)
  - Giga Ethernet Card (1000 Mbps)
- NICs are available as Wired and Wireless both.
- Generally Desktops have one NIC and Laptops have two NICs (one wired and one wireless).
- Maximum internet speed depends on the NIC of a system.
  If a faster and slower cards are communicating then the max. speed would be of slower card.
- Types of Card (Based on Transmission Modes):
  - Simplex - Can either Send or Receive
  - Half Duplex - Can Send and Receive both but only one at a time
  - Full Duplex - Can Send and Receive simultaneously
- [Auto-Negotiation] happens while communication happens between a Higher Transmission mode 
  supporting card and a lower transmission supporting card. The Higher one degrades its capability
  to match the other card's capability.
#### How to check number of NICs using linux?
- by running ```ifconfig``` or ```ip a``` or ```nmcli connection show``` commands on terminal
#### To check the info about a device
- run ```ethtool <device_name>```

## Medium
- Wired
  - Types of Cables:
    - RJ-45 (LAN Cable)
    - Optical Fiber
    - Serial Cable
- Wireless
  - It is a technology.
  - It doesn't mean without wire.
  - Like Bluetooth, RF, NFC are also technologies.
  - Set of Rules (these rules are accepted or approved by IEEE):
    - 300 meters range over 2.x GHz frequency
    - generally lower speed than wired
    - Standard made by IEEE for
      - Wifi are 802.11/802.11a/802.11b/802.11g/802.11n etc.
      - LAN are 802.3/802.4 etc.
      - Bluetooth is 802.15

> RFC - A Request for Comments (RFC) is a publication from the Internet Society (ISOC) and its associated bodies, 
  most prominently the Internet Engineering Task Force (IETF), the principal technical development and standards-setting 
  bodies for the Internet.

#### August 18, 2020 : Session 021
## IP Address
- It is the Logical Address of a computer.
- We can understand it in reference to permanent and current address format, like
  - Permanent Address would be a computer's MAC Address.
  - Current(Logical) Address would be like IP.
- Categories are:
  - IPv4
  - IPv6
#### IPv4
- Example:
  - 192.168.0.100
  - Here, each partition is of 1 Byte(i.e.,8 bits). Total size of IPv4 Address is 4 Bytes(32 bits).
  - The range of each partition is 0-255(2^8 bits, i.e. 256).
- We can run ```ipconfig``` command (on Windows) and ```ifconfig``` command (on Linux, Mac) to view IP related info.
- Somewhere there is an IP Collection and a wire which is taken out from there contains IP (which can further be divided into muliple IPs).
> **Question: Among following which IPv4 Addresses are wrong?**
> - (A) 192.168.200.255
> - (B) 192.168.100.09
> - (C) 192.168.100.05
> - (D) 192.168.5000

> **Answer:** Option (B) is incorrect IPv4 Address. This is because leading 0 represents octal representation and octal has values from 0-7. As 9 is out of range, it makes this option incorrect and similarly makes the option (C) correct. In option (D) the last partition has capacity to store 2 Bytes (i.e. 2^16 bits = 65536), range could be from 0 to 65535 (and 5000 lies in this only), hence the given IP is correct.

> **Question: How is 192.168.5000 converted to 192.168.19.136?**
![Practical Example](https://github.com/CRJain/reboot-2.0/blob/master/image.png)

> **Answer:** 19.136 can be written as 19(2^8)+136(2^0)=5000. The whole IP Address can be represented by a single number, as 192(2^24)+168(2^16)+19(2^8)+136(2^0) = 3232240520.

> **Question: Convert 897858594 to equivalent IPv4 address using math.**

> **Answer:** 53.132.60.34. To achieve this we can convert the given number into it's binary and the make groups of 8 bits from end and write them in their decimal form.

> **Solution:** Binary of 897858594 => 110101 10000100 00111100 00100010
>   - (00110101) = (53) in decimal [added 2 zeroes in start to complete 8 bits]
>   - (10000100) = (132) in decimal
>   - (00111100) = (60) in decimal
>   - (00100010) = (34) in decimal

> Hence, our final IPv4 address looks like **53.132.60.34**

> **Question: How to connect to 0.0.0.0?**

> **Answer:** 0.0.0.0 as a target address refers variously to a non-routable host or to “this" host. In practice connecting to 0.0.0.0 is equivalent to connecting to localhost. When binding, “this" host expands to “any address on this host” — so applications commonly accept connections by binding to 0.0.0.0, which means they’ll receive packets addressed to any IPv4 address on the system. Localhost is a single address, mostly 127.0.0.1, while 0.0.0.0 means all addresses on this host.

> **Question: Can we connect to 127.0.0.1 (localhost) from some other PC, if yes then how?**

> **Answer:** We can connect to localhost from anywhere using tunneling protocol which allows private network communications to be sent across public network. For e.g., ngrok is a tool to achieve this.

> **Question: What address is used by Bluetooth to connect with devices?**

> **Answer:** Bluetooth uses a radio technology called frequency-hopping spread spectrum. It uses many protocols to search the devices in proximity. It uses a master slave architecture. Bonds between devices are created using pairing. When they pair up they share their MAC ADDRESS, NAME AND PROFILE and usually stores them in memory. Devices also share a secret key. Data is transmitted in packets over Bluetooth channels.

#### August 18, 2020 : Session 022
#### NetMask
- Role of Netmask is to divide IP address into 2 parts - Network ID and Host.
- For e.g.,let IP is 192.168.10.200 and NetMask is 255.255.255.0, then
  - 192.168.10 is called Network ID and,
  - 200 is Host
- If two systems are directly connected and they have exact same Network ID, then they can communicate with each other.
> **Question: How to connect multiple systems in a local area?**

> **Answer:** **Switch** would be the correct answer. It understands MAC (newer Switch can understand both IP as well as MAC and are called Layer 3 Switch). Switch supports Full Duplex mode, so simultaneous communications can happen. It supports all type of communications. It works on Layer 2 (now-a-days on Layer 3 also). It is secure and same Network ID systems can communicate with each other.

> We can also use **Hub** but it doesn't understand IP or MAC Address and hence, broadcasts any message from the origin to all connected systems. Thus, leading to lack of security. Hub works on Physical Layer of OSI(Open Systems Interconnection) Model. It doesn't allow multiple communications at the same time.

- **Router** can be used for communications between systems having different Network IDs. It works on Layer 3 of OSI Model.
- We can assign netmask using ```netmask``` command. For e.g., ```ifconfig virbr0 172.27.10.200 netmask 255.255.0.0```.
- If we have IP as 192.168.10.200 and netmask as 255.255.255.0, then we can have 256-2=254 unique IP addresses (192.168.10.1 - 192.168.10.254).
  - 192.168.10.0 is called Network IP and,
  - 192.168.10.255 is called Broadcast IP
- When we assign an IP without providing a netmask value, it automatically gets assigned with a netmask value called **Default NetMask**.
  - Default Netmask depends on Class of IP.
  - If IP is like 0-127.0-255.0-255.0-255 => Default netmask will be 255.0.0.0 (Class A IP). It can have 2^24 unique IP addresses.
  - If IP is like 128-191.0-255.0-255.0-255 => Default netmask will be 255.255.0.0 (Class B IP). It can have 2^16 unique IP addresses.
  - If IP is like 192-223.0-255.0-255.0-255 => Default netmask will be 255.255.255.0 (Class C IP). It can have 2^8 unique IP addresses.
  - If IP is like 224-239.0-255.0-255.0-255 => It doesn't have a netmask (Class D IP). It can't be assigned to any of the devices we use. It is not made for normal networking purposes. It is used for **Multi-casting**.
  - If IP is like 240-255.0-255.0-255.0-255 => It is reserved for Scientific Research + **Broad-casting** (Class E IP).
- **Casting** means communicating.
- If communication of a system happens with
  - only one system, it is called **Uni-casting**.
  - all the systems, it is called **Broad-casting**.
  - more than one system but not all, it is called **Multi-casting**.
> **Distance-vector routing protocol**
> A distance-vector routing protocol in data networks determines the best route for data packets based on distance. Distance-vector routing protocols measure the distance by the number of routers a packet has to pass, one router counts as one hop. Some distance-vector protocols also take into account network latency and other factors that influence traffic on a given route.

> **Routing Information Protocol**
> The Routing Information Protocol is one of the oldest distance-vector routing protocols which employ the hop count as a routing metric. RIP prevents routing loops by implementing a limit on the number of hops allowed in a path from source to destination.
> - Multi-casting IP of RIP is 224.0.0.9
