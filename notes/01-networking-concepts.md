# Domain 1.0 - Networking Concepts

Exam weight: 23%

---

## 1.1 OSI Model

Mnemonic: **All People Seem To Need Data Processing**

| Layer | What lives there |
| --- | --- |
| 7 Application | What you see |
| 6 Presentation | Application encryption (TLS/SSL) |
| 5 Session | Protocols managing the conversation |
| 4 Transport | Ports, TCP/UDP |
| 3 Network | IP addresses, routers, packets |
| 2 Data Link | Frames, MAC addresses, NIC, Extended Unique Identifier (EUI) |
| 1 Physical | Cables, fiber, the signal itself |

---

## 1.2 Networking Appliances and Functions

- **Router** - routes traffic between IP subnets.
- **Firewall** - filters traffic by port number or application; often encrypts traffic through a VPN.
- **Proxy** - sits between users and the external network, adding a verification step for information and communication.
- **NAS vs SAN** - NAS (Network Attached Storage) gives access to the entire scope of data at once. SAN (Storage Area Network) allows individual block-level access and changes, which is more efficient.
- **QoS (Quality of Service)** - controls how much dedicated bandwidth different applications get.

---

## 1.3 Cloud Concepts

### Designing the cloud

- **Elasticity** - ability to scale cloud resources up or down on demand.
- **NFV (Network Function Virtualization)** - replaces traditional network hardware functions with software. Gives networks cloud-style flexibility.
- **VPC (Virtual Private Cloud)** - a pool of resources created inside a public cloud.
- **VPC NAT gateway** - private cloud subnets reach external resources, but external resources cannot reach back in because of network address translation.
- **VNIC (Virtual Network Interface Card)** - software instance of a physical NIC that connects VMs to a virtual network.

### Cloud service models

- **SaaS (Software as a Service)** - pay to use prebuilt software with no backend to manage. Gmail, Office 365.
- **IaaS (Infrastructure as a Service)** - you manage the hardware layer; your data is hosted but more in your control.
- **PaaS (Platform as a Service)** - the middle ground between SaaS and IaaS.

---

## 1.4 Ports, Protocols, and Traffic Types

The analogy that made IP click:

- The network topology is the road (Ethernet, DSL, cable).
- IP is the truck.
- TCP and UDP are the boxes in the truck holding your data.

### Other useful protocols

- **GRE (Generic Routing Encapsulation)** - tunnel between two endpoints. No built-in encryption.
- **IPsec** - security at OSI layer 3 for routed data.
- **IKE (Internet Key Exchange)** - lets sender and receiver agree on rules and authenticate each other before communication is established.
- **Transport mode vs tunnel mode** - transport mode inserts an IPsec header and trailer. Tunnel mode adds a new IP header at the front of the packet, which is more secure.
- **ESP (Encapsulating Security Payload)** - encrypts the packet, adds an ESP header and trailer plus an integrity check value at the end.
- **AH (Authentication Header)** - provides data integrity and authentication but **not** encryption. ESP is the one that provides confidentiality.

---

## 1.5 Transmission Media and Transceivers

### Wireless standards

- **IEEE 802.11** is the standard for wireless networking.
- 802.11n = Wi-Fi 4
- 802.11ac = Wi-Fi 5
- 802.11ax = Wi-Fi 6
- 802.11be = Wi-Fi 7
- **LTE** - 4G data technology, supports around 150 Mbps download.

### Copper cabling

- Cables themselves do not have speeds. The electrical signals sent over the copper determine the speed.
- Cable standards are referred to by category: Cat 6, Cat 7, etc.
- **Coaxial cable** - one central conductor surrounded by insulation and metal shielding.
- **Twinaxial cable** - same topology as coax but with two central conductors.
- **Transceiver** - a transmitter and receiver for your cables.
- **SFP (Small Form-factor Pluggable)** - a transceiver type. SFP+ handles higher speeds, up to 16 Gbit/s.
- **QSFP (Quad SFP)** - transceiver handling 4 channels.

---

## 1.6 Network Topologies and Architectures

- **Star** - all devices connect to a central device.
- **Mesh** - multiple links to the same place; devices have multiple routes to the same destination.

### Three-tier architecture

1. **Core** - the center of the network: servers, databases.
2. **Distribution** - midpoint between core and users. **Routing primarily happens here.**
3. **Access** - where users connect; the endpoint layer.

### Traffic flow

- **East-west** - traffic staying inside one data center. Relatively fast response times.
- **North-south** - traffic entering or leaving the data center. Different security posture than east-west.

---

## 1.7 IPv4 Addressing and Subnetting

### IPv4 basics

- **APIPA (Automatic Private IP Addressing)** - gives a link-local IP usable only within the local subnet when DHCP is unavailable. Uses ARP to confirm the address is unique.

### Classful subnet masks

| Class | Default mask |
| --- | --- |
| A | 255.0.0.0 |
| B | 255.255.0.0 |
| C | 255.255.255.0 |

### Calculating subnets

- **VLSM (Variable Length Subnet Mask)** - lets admins define their own network sizes.
- Number of subnets = 2 ^ (subnet bits)
- Hosts per subnet = 2 ^ (host bits) - 2

Worked examples:

**172.20.4.10/23** (Class B)
Mask in binary: 11111111.11111111.11111110.00000000
7 subnet bits, so 2^7 = 128 subnets
9 host bits, so 2^9 - 2 = 510 hosts per subnet

**192.168.30.1/30** (Class C)
Mask in binary: 11111111.11111111.11111111.11111100
6 subnet bits, so 2^6 = 64 subnets
2 host bits, so 2^2 - 2 = 2 hosts per subnet

### Magic number subnetting

**192.168.83.54 with 255.255.255.192** - find network and broadcast
256 - 192 = 64, so subnets increment by 64
54 falls in the 0-63 block
Network address: 192.168.83.0
Broadcast address: 192.168.83.63

**10.180.122.244 with 255.248.0.0**
256 - 248 = 8, so the second octet increments by 8
8, 16, ... 160, 168, 176, 184
176 is the block 180 falls into
Network address: 10.176.0.0
Broadcast address: 10.183.255.255

---

## 1.8 Modern Network Environments

### Software Defined Networking

- **Infrastructure layer / data plane** - processes frames and traffic; handles forwarding, trunking, NAT.
- **Control layer / control plane** - manages what the data plane does: routing tables, session tables.
- **Application layer / management plane** - configure and manage the device via SSH, browser.

### VXLAN

- **DCI (Data Center Interconnect)** - connects multiple data centers, using the cloud to distribute applications.
- **VXLAN (Virtual Extensible LAN)** - takes layer 2 traffic and wraps it inside a layer 3 UDP packet so it can cross any standard IP network. Commonly paired with SDN to manage VXLANs across locations.

### Infrastructure as Code

- **IaC** - uses code to build cloud infrastructure.
- **IaC playbook** - conditional steps that automate handling of IaC issues; a reusable template, the same way the IaC itself is reusable.

### IPv6 addressing

- Groups of zeros can be abbreviated with a double colon (::), but only **once** per address.
- Leading zeros in each group can also be dropped.
- 2600:DDDD:1111:0001:0000:0000:0000:0001 becomes 2600:DDDD:1111:1::1
- IPv4 and IPv6 cannot communicate directly. Tunneling, dual-stack, and translation bridge the gap.
- **6to4** - sends IPv6 over an IPv4 network. Does not support NAT.
- **4in6** - tunnels IPv4 over IPv6.
- **Dual-stack** - systems get both an IPv4 and an IPv6 address.
- **NAT64** - translates between IPv6 and IPv4.
