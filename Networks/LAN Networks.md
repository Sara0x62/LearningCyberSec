# LAN Topologies
### Star Topology
![[Pasted image 20240326054957.png]]

| **Pros**                                                                                        | **Cons**                                                                                                |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Reliability and scalability due to individual connections via a central device (switch or hub). | Higher cost due to additional cabling and dedicated networking equipment.                               |
| Easy scalability, allowing for the addition of more devices as network demand increases.        | Increased maintenance requirements as the network scales, making troubleshooting harder.                |
|                                                                                                 | Centralized hardware failure can disrupt network communication, although such devices are often robust. |

### Bus Topology
![[Pasted image 20240326062949.png]]

| **Pros**                                       | **Cons**                                                                  |
| ---------------------------------------------- | ------------------------------------------------------------------------- |
| Easy and cost-efficient to set up              | Prone to become slow/bottlenecked with multiple devices                   |
| Simple structure resembling a tree's branches. | Difficult troubleshooting due to all data traveling along the same route. |
|                                                | Little redundancy / Single point of failure along the backbone.           |
### Ring Topology (aka. token topology)
![[Pasted image 20240326064845.png]]

| **Pros**                                                                               | **Cons**                                                            |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Minimal cabling and less dependence on dedicated hardware (compared to star topology). | Inefficient data travel may require visiting multiple devices.      |
| Easy troubleshooting due to single direction for data travel.                          | Vulnerable to network failure if a cable is cut or a device breaks. |
| Less prone to bottlenecks (compared to bus topology).                                  |                                                                     |

### What is a Switch?
![[2504bf9d718556c764c28843f43febe0.png]]
Switches are network devices that aggregate multiple devices like computers and printers using Ethernet. They're common in larger networks connecting numerous devices via ports of various sizes. Switches efficiently manage network traffic by directing packets only to the intended recipient, unlike hubs or repeaters.
They enhance network redundancy's by allowing connection to routers, ensuring uninterrupted connectivity in case of path failure, albeit potentially impacting performance slightly.

### What is a router?
![[e83d39192c6a3e8168f842d9a680a7c3.png]]
Routers connect networks and facilitate data transfer between them through routing. Routing is the process of guiding data across networks by establishing paths for successful delivery, particularly beneficial when multiple paths exists between connected devices.

# Subnetting
Networks vary in size and structure, with subnetting allowing the division of a network into smaller segments.
Similar to slicing a cake, subnetting allocates portions of the network to different departments, such as Accounting, Finance, and Human Resources in a business setting.
![[dfdda87fb215cd723555bde32345e05e.png]]
Network administrators employ subnetting to organize and allocate specific network segments, mirroring real-world departmental divisions. 

Subnetting involves dividing the network based on the number of hosts, indicated by a subnet mask.
![[3e3b2a9eeaf249ce0a7f4dbb46f0bd14.png]]
An IP Address is made of 4 sections called octets, as is a subnet mask.
They are represented as a number of 4 bytes (32 bits) from 0 to 255.

Subnets use IP's in 3 ways:
- Identify network address
- Identify host address
- Identify default gateway

| **Type**        | **Purpose**                                                                                                                                    | **Explanation**                                                                                                                                                                                                                                      | **Example**   |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| Network Address | This address identifies the start of the actual network and is used to identify a network's existence.                                         | For example, a device with the IP address of 192.168.1.100 will be on the network identified by 192.168.1.0                                                                                                                                          | 192.168.1.0   |
| Host Address    | An IP address here is used to identify a device on the subnet                                                                                  | For example, a device will have the network address of 192.168.1.1                                                                                                                                                                                   | 192.168.1.100 |
| Default Gateway | The default gateway address is a special address assigned to a device on the network that is capable of sending information to another network | Any data that needs to go to a device that isn't on the same network (i.e. isn't on 192.168.1.0) will be sent to this device. These devices can use any host address but usually use either the first or last host address in a network (.1 or .254) | 192.168.1.254 |

Subnetting benefits:
- Efficiency
- Security
- Full Control
# ARP Protocol
The **A**ddress **R**esolution **P**rotocol (**ARP**) facilitates devices in associating MAC addresses with IP addresses on a network. 

### How does ARP Work?
It works through these 2 types of messages it sends.
1. **ARP Request:**
    - Broadcasted message sent by a device to all devices on the network.
    - Asks whether any device's MAC address matches the requested IP address.
    - Initiates the search for the MAC address corresponding to the target IP address.
2. **ARP Reply:**
    - Response sent by a device if it possesses the requested IP address.
    - Confirms the match between the IP address and the MAC address.
    - Acknowledges the ARP request and allows the requesting device to store this information in its cache.


![[2107060a6e1df30659654335b878e91a-1.png]]

# DHCP Protocol
**DHCP** (**D**ynamic **H**ost **C**onfiguration **P**rotocol) automates the assignment of IP addresses on a network. 
When a device connects, it sends a *DHCP Discover* request to find DHCP servers. A server responds with a *DHCP Offer*, proposing an IP address. 
The device confirms with a *DHCP Request*, and upon acknowledgment (*DHCP ACK*) from the server, it begins using the assigned IP address.
![[0514189b8424bb6493f7b427b40425e2.png]]

---
[[Study notes/Networks/Networking|Networking]] | [[Security & Tools]]