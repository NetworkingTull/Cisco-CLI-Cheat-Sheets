

-AccessPort-
interface g0/0
switchport mode access
switchport access Vlan 10
switchport trunk allowed vlan add
switchport trunk allowed vlan add
do show vlan

-TrunkPort-
interface g0/1
switchport mode trunk
switchport trunk allowed Vlan 10,20,30
switchport trunk native vlan 1001
do show interface trunk

-ROAS-
interface g0/0
no shutdown
interface g0/0.1
encapsulation dot1q 10
ip address 10.0.0.64 255.255.255.192
interface g0/0.2
encapsulation dot1q 20
ip address 10.0.0.128 255.255.255.192
interface g0/0.3
encapsulation dot1q 30
ip address 10.0.0.190 255.255.255.192

-CreateVLAN-
vlan 10
name SALES
vlan 20
name HR
do show vlan brief

-DeleteVLAN-
no vlan 20
do show vlan






















 Modes:
#   >  User Exec Mode
#   #  Privileged Exec Mode
#   (config)# Global Configuration Mode
#   (config-if)# Interface Configuration Mode

# ----------------------
# 1. Basic Navigation
# ----------------------
enable                 # Go from User Exec (>) to Privileged Exec (#)
disable                # Go from Privileged Exec (#) to User Exec (>)
configure terminal     # Enter Global Configuration Mode (config)#
exit                   # Exit current mode
end                    # Exit to Privileged Exec Mode (#)
reload                 # Reboot device
write memory / copy running-config startup-config  # Save config

# ----------------------
# 2. Viewing Information
# ----------------------
show running-config    # Current configuration
show startup-config    # Configuration saved in NVRAM
show version           # Device info, IOS version, uptime
show ip interface brief  # Summary of interfaces and IPs
show interfaces        # Detailed interface status
show vlan brief        # VLAN info
show mac address-table  # MAC addresses learned by switch
show arp               # ARP table
show cdp neighbors     # Directly connected Cisco devices
show logging            # View system logs
ping <IP>              # Test connectivity
traceroute <IP>        # Trace path to a host

# ----------------------
# 3. Interface Configuration
# ----------------------
interface <type/number>      # Enter interface config mode
description <text>           # Label interface
ip address <IP> <subnet>     # Assign IP address
no shutdown                  # Enable interface
shutdown                     # Disable interface
exit                         # Exit interface mode

# ----------------------
# 4. VLAN Configuration (Switches)
# ----------------------
vlan <ID>                    # Create VLAN
name <vlan_name>              # Name VLAN
interface vlan <ID>           # Enter VLAN interface mode
switchport mode access        # Set port to access mode
switchport access vlan <ID>   # Assign VLAN to port
switchport mode trunk         # Set trunk mode
switchport trunk allowed vlan <IDs>  # Set allowed VLANs

# ----------------------
# 5. Routing (Layer 3)
# ----------------------
ip route <dest> <mask> <next-hop>   # Static route
show ip route                       # View routing table
router ospf <process-id>            # Enable OSPF
network <IP> <wildcard-mask> area <area>  # OSPF network
router rip                          # Enable RIP
version 2                            # RIP version 2
network <IP>                        # RIP network

# ----------------------
# 6. Security / Access
# ----------------------
enable secret <password>         # Set privileged exec password
line console 0
 password <password>
 login
exit
line vty 0 4
 password <password>
 login
 transport input ssh telnet
exit
service password-encryption        # Encrypt plaintext passwords

# ----------------------
# 7. Troubleshooting
# ----------------------
show ip route
show ip interface brief
show cdp neighbors
ping <IP>
traceroute <IP>
debug <feature>      # Only use in lab, can be heavy on production
undebug all           # Stop all debugging

*End ChatGPT Sourced Table*
