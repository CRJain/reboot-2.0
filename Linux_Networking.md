# Linux Networking
Friday Aug 14 : Session 020
## Topics to be covered
- Communication Devices
  - Hub
  - Bridge
  - Switch
  - Router
  - Firewall Devices
- Ipv4 and Ipv6
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
