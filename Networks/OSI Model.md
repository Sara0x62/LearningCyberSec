# What is the OSI Model?
The **OSI** model (**O**pen **S**ystems **I**nterconnection Model) is a critical model, providing a framework on how all networked devices send, receive and interpret data.

The OSI model is made up of 7 layers, each with their own set of responsibilities and is arranged from **Layer 7 (Application)** to **Layer 1 (Physical)**.

At each layer data passes through, various processes occur, and additional information is appended. This phenomenon is called **encapsulation**

![](../attachments/e224945119a0fec7775e89282265110b.png)

# Layer 7 - Application
The **application layer** of the OSI model *facilitates user interaction* with data through protocols and rules. 
This layer is familiar due to everyday *applications* like email clients, browsers, and file server browsing software (e.g., FileZilla) offering a **GUI** (**G**raphical **U**ser **I**nterface).
Protocols such as **DNS** (**D**omain **N**ame **S**ystem) translate website addresses into IP addresses.
# Layer 6 - Presentation
This layer initiates *standardization*, ensuring consistent data handling regardless of software variations. 
Serving as a *translator* between the application layer (layer 7) and lower layers, it ensures *data compatibility* even if received by different applications. *Security* measures like *data encryption* (e.g., HTTPS) are implemented at this layer.
# Layer 5 - Session
The **session layer** (layer 5) establishes and manages connections between computers, *creating sessions* for data exchange. 
It ensures *synchronization* and breaks data into *smaller packets for transmission*, reducing data loss risks. Sessions are unique, restricting data transmission to within each session.
# Layer 4 - Transport
Layer 4 of the OSI model is crucial for *data transmission* in networks, involving protocols like **TCP** and **UDP**. 
## TCP
or **T**ransmission **C**ontrol **P**rotocol ( [[Study notes/Networks/Networking#TCP/IP Model|TCP/IP Notes]] ), prioritizes reliability and ensures a continuous connection between devices until data transmission is complete. It incorporates error checking to guarantee the accurate reception and reassembly of data sent in small chunks.

| **Advantages of TCP**                                          | **Disadvantages of TCP  <br>**                                                                                  |
| -------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Accuracy of data                                               | Requires a reliable connection; if one data chunk is lost, the entire data set becomes unusable.                |
| Capable of synchronizing (2) devices to prevent data overload. | A slow connection can bottleneck other devices as it reserves the connection on the receiving end continuously. |
| More reliable                                                  | Significantly slower than UDP                                                                                   |
Used for things where data has to be *accurate and complete* (e.g. file transfer, browsing pages, sending emails

## UDP
or **U**ser **D**atagram **P**rotocol, doesn't provide the features TCP does, there is no error checking, reliability or synchronization, while this sounds bad, it does have its merits.

| **Advantages of UDP**                                                                                                 | **Disadvantages of UDP**                                                           |
| --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Much faster than TCP.                                                                                                 | UDP doesn't care if the data is received.                                          |
| UDP leaves the application layer (user software) to decide if there is any control over how quickly packets are sent. | It is quite flexible to software developers in this sense.                         |
| UDP does not reserve a continuous connection on a device as TCP does.                                                 | This means that unstable connections result in a terrible experience for the user. |

UDP is widely used where *speed* is required, such as video streaming (If the view is pixelated it simply shows lost data).
It is also used in protocols such as **ARP** and **DHCP** for discovering devices.

# Layer 3 - Network
The network layer, handles routing and reassembly of data from small to larger chunks. 
Routing determines the *optimal path for data transmission*, involving protocols like **OSPF** (**O**pen **S**hortest **P**ath **F**irst) and **RIP** (**R**outing **I**nformation **P**rotocol). 

Factors include 
- shortest path
- reliability
- speed of physical connection. 

We work with IP addresses here, Devices like routers also operate at this layer (Known as Layer 3 Devices)
# Layer 2 - Data 
The data link layer handles *physical addressing* by adding the **MAC** (**M**edia **A**ccess **C**ontrol) address to packets received from the network layer. 
MAC addresses are *unique identifiers* burned into **N**etwork **I**nterface **C**ards (**NIC**s). They can't be changed but can be spoofed. 
The data link layer ensures data is formatted appropriately for transmission.

# Layer 1 - Physical
This layer deals with the physical components of networking hardware, operating at the lowest level. 
It involves transferring data between devices using *electrical signals* in a binary numbering system (1's and 0's).

e.g. an Ethernet cable

![](../attachments/bfda457fb21fe0df94615793bbdc69f6.avif)