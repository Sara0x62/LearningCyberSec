# Introduction to Security Operations
A **S**ecurity **O**perations **C**enter (**SOC**) comprises of IT Security Professionals, dedicated to round-the-clock monitoring of a company's network and systems. Their objectives include:
1. **Identify Network Vulnerabilities**
2. **Detect unauthorized activity**
3. **Discover policy violations**
4. **Detect intrusions**
5. **Support incident response efforts**
# Elements of Security Operations
## Data Sources
The SOC utilizes various **data sources** to monitor the network for intrusions and malicious behaviour, including:

- **Server logs**: Contain information on activities like login attempts.
- **DNS activity**: Logs domain name queries, aiding in monitoring internal communications.
- **Firewall logs**: Reveal details of network packet activity.
- **DHCP logs**: Provide insights into devices joining the network.

These are among the primary sources, with others also aiding in network security monitoring, often aggregated through **S**ecurity **I**nformation and **E**vent **M**anagement (**SIEM**) systems for efficient correlation and response to attacks.

## SOC Services:
SOC services encompass both reactive and proactive measures:

Reactive services include:
- **Monitoring security posture.**
- **Managing vulnerabilities.**
- **Analysing malware.**
- **Detecting intrusions.**
- **Reporting incidents.**

Proactive services include:
- **Network security monitoring (NSM).**
- **Threat hunting.**
- **Threat intelligence gathering.**

Additionally, the SOC may provide cybersecurity training to enhance user awareness and prevent breaches.

# Practical Example of SOC
We use a firewall to halt ongoing attacks. A firewall inspects network packets entering and leaving a system. Basic types of firewalls inspect:

- Source and destination IP addresses: Like postal addresses, IP addresses facilitate internet communication.
- Source and destination port numbers: Similar to room numbers within a building, port numbers enable programs to communicate over a network.

A firewall rule example:

| Source IP  | Destination IP | Source Port | Destination Port | **Action** |
| ---------- | -------------- | ----------- | ---------------- | ---------- |
| 172.16.4.1 | 10.10.10.41    | ANY         | 80               | PASS       |
| 172.16.8.1 | 10.10.10.8     | ANY         | 23               | DROP       |

These rules dictate:
- Allow all packets from 172.16.4.1 to 10.10.10.41 on port 80 (PASS).
- Block all packets from 172.16.8.1 to 10.10.10.81 on port 23 (DROP).