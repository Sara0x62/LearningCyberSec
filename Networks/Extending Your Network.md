# Intro to Port Forwarding
By default, without port-forwarding, services are only locally available.
For example; a webserver on port 80, then this is only available to users inside your local network (LAN).
If we want to make this public to the internet we'd have to **port-forward**.

This is managed by the router of a network, unlike firewalls which simply determine if certain traffic is allowed through, even if the port is open.
# Firewalls 101
A Firewall is a device in a network responsible for deciding what traffic enters or exits.
They operate on *Layers 3 & 4 of the OSI Model (Network & Transport)*

(Extra; A newer type of firewall "**WAF**" or "*Web Application Firewall*" works on Layer 6 & 7 - Presentation & Application)

These are configured by an administrator to **permit** or **deny** traffic based on:
- Source of **Incoming** traffic (firewall configured to accept/deny certain networks?)
- **Outgoing** traffic (firewall configured to accept/deny traffic to a certain network?)
- The **port** (Is the firewall accepting traffic to the destined port?)
- What **protocol** (Firewall accepting/denying certain protocols? - TCP/UDP/Both?)

There are 2 primary category's of Firewalls
### 1. Stateful Firewalls
This type of firewall uses the entire information from a connection; rather than inspecting an individual packet, this firewall determines the behaviour of a device **based upon the entire connection**.

This firewall type consumes many resources in comparison to stateless firewalls as the decision making is dynamic. For example, a firewall could allow the first parts of a TCP handshake that would later fail.

If a connection from a host is bad, it will block the entire device.
### 2. Stateless Firewalls
This firewall type relies on fixed rules to decide packet acceptance.
For instance, one bad packet won't necessarily block the entire device. Although they use fewer resources, they're less intelligent, working only as well as their defined rules. 
They *excel at handling high traffic volumes from specific hosts*, like in a Distributed Denial-of-Service attack.

# VPN Basics
A **VPN** (**V**irtual **P**rivate **N**etwork) allows devices of different networks to communicate securely, making a dedicated path between them over the Internet (known as a **tunnel**).

VPN's offer some nice benefits:
- **Allows networks in different locations to be connected** (e.g. Businesses with multiple offices)
- **Privacy** (Data is encrypted and safe view for those outside the VPN)
- **Anonymity** (VPNs protect your traffic from being viewed by ISP's and other intermediaries and therefore tracked. The level of anonymity depends on the VPN)


| **VPN Technology** | **Description**                                                                                                                                                                     |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PPP                | used in PPTP (below) to allow **authentication and data encryption** (uses private/public keys) - this technology is non-routable                                                   |
| PPTP               | The **P**oint-to-**P**oint **T**unneling **P**rotocol (**PPTP**) allows data from PPP to travel outside the network. - Easier to set up but weakly encrypted vs alternatives.       |
| IPSec              | Internet Protocol Security (IPSec) encrypts data using the Internet Protocol (IP) framework. - Difficult to set up, strong encryption and supported on many devices (If successful) |

# LAN Networking Devices

## What is a Router?
Routers connect networks by passing data between them using **routing** protocols. They operate at *Layer 3 of the OSI model* and feature interfaces for configuration.
Routing finds the best path for data delivery, considering factors like 
- **shortest route**
- **reliability**
- **fastest medium** (e.g. Copper or Fibre)

Routers are distinct from switches and are essential for managing complex network connections.
## What is a Switch?
A **switch** is a dedicated networking device for connecting multiple devices (3-63 devices) via Ethernet cables.
Switches operate at both **Layer 2** and **Layer 3** of the OSI model, but Layer 2 switches cannot function at Layer 3.

In a **Layer 2** switch, frames are forwarded to connected devices based on their **MAC address**.

**Layer 3** switches are more advanced, handling both frame forwarding and **packet routing** using the IP protocol.

**VLAN** (**V**irtual **L**ocal **A**rea **N**etwork) technology divides a network into separate virtual segments, enhancing security and control over device communication.

# Other Components
## Load Balancers
Load balancers distribute website traffic among multiple servers to ensure high availability and handle heavy loads. They use algorithms like **round-robin** or weighted distribution and perform health checks on servers. If a server fails, traffic is redirected until it's operational again.
## CDN (Content Delivery Networks)
CDNs cut down traffic to your website by hosting static files across numerous servers worldwide. When a user requests a file, the CDN directs them to the nearest server for faster access.
## Databases
Databases store and retrieve information for websites. They vary in complexity from simple text files to clustered servers for speed and resilience. Common databases include MySQL, MSSQL, MongoDB, GraphQL, and Postgres, each with unique features.
## WAF (Web Application Firewall)
WAFs protect web servers from hacking and denial-of-service attacks. They analyse web requests for common attack techniques, verify requests are from real browsers, and use rate limiting to prevent excessive requests. Suspicious requests are dropped before reaching the web server.