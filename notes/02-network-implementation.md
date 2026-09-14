# Domain 2.0 - Network Implementation

Exam weight: 20%

---

## 2.1 Routing Technologies and Bandwidth Management

### Static and dynamic routing

- **Routing table** - stores IP information the router uses to determine the best route.
- **Static routing** - administrative control of the routing table. You are the one in control.
- **Dynamic routing** - routers advertise routes to each other, so tables update in near real time. Routers both listen for subnet information and give it out. Dynamic routing determines the **best path** between routers and subnets.

### Routing protocols

- **EIGRP (Enhanced Interior Gateway Routing Protocol)** - Cisco protocol, relatively easy to configure. Distance-vector (advanced).
- **OSPF (Open Shortest Path First)** - **link-state** protocol, common inside an autonomous system, well-established standard.
- **BGP (Border Gateway Protocol)** - used with WANs, the standard that runs the internet.
- **IS-IS** - the other **link-state** protocol. Worth pairing with OSPF in your head; EIGRP is not link-state.

### Other routing concepts

- **Routing metrics** - internal value the routing table uses to pick between redundant links. Common metrics include hop count, bandwidth, delay, load, and cost. **Administrative distance is not a metric** - it ranks the trustworthiness of the routing source.
- **FHRP (First Hop Redundancy Protocol)** - devices use a virtual IP as their default gateway, so if one router's VIP disappears another takes over and traffic keeps flowing.
- **Subinterfaces** - multiple logical interfaces on one physical connection, each with its own IP and subnet mask.

### Network Address Translation

Private IP ranges:

- 10.0.0.0 - 10.255.255.255
- 172.16.0.0 - 172.31.255.255
- 192.168.0.0 - 192.168.255.255

**PAT (Port Address Translation)** - maps the same public IP to many private IPs using different port numbers.

---

## 2.2 Switching Technologies

### VLANs and trunking

- **VLAN** - a group of devices in the same broadcast domain, separated logically rather than physically.
- **VLAN trunk** - carries multiple VLANs over one connection without individual links, while keeping each VLAN isolated to its matching VLAN on the other end.
- **VLAN IDs** - 12 bits, supporting up to 4094 VLANs.
- **Native VLAN** - does not get a VLAN tag and traverses a trunk untagged.
- **Layer 3 switch** - a switch and router in the same physical device; each function still operates at its own OSI layer.
- **VoIP** - runs phone communications over IP, removing the need for separate phone cabling.

### Interface configurations

- Two basic settings to consider when plugging in an Ethernet cable: **speed** and **duplex**.
- **LAG (Link Aggregation)** - multiple physical interfaces act as one larger interface, usually via **LACP**.
- **MTU (Maximum Transmission Unit)** - the largest IP packet that can be transmitted.
- **Jumbo frames** - Ethernet frames with a payload larger than the default 1500 bytes, typically 9216. Every device in the path must support them.

### Spanning Tree Protocol

Two switches connected by a cable create a loop, and there is no way to break a loop at the MAC layer. STP prevents loops at layer 2.

Port states:

| State | Behavior |
| --- | --- |
| Blocking | Prevents sending, to break a loop |
| Listening | Not forwarding; clearing the MAC table |
| Learning | Not forwarding; adding to the MAC table |
| Forwarding | Data passes through |
| Disabled | Admin has turned the port off |

**RSTP (802.1w)** is the updated version of STP.

Note for the exam: a port that is not forwarding **to prevent a loop** is a **blocked** port, not a disabled port. Disabled means an admin turned it off.

---

## 2.3 Wireless Implementation

### Wireless technologies

- **802.11** - the standard covering nearly all wireless.
- **Band steering** - lets the network choose the better frequency rather than leaving it to the device.
- **DFS (Dynamic Frequency Selection)** - avoids frequency conflict by selecting channels not in use by nearby devices, where possible.
- **TPC (Transmit Power Control)** - the AP determines client power levels so devices operate at an optimal level.
- **IBSS (Independent Basic Service Set)** - two devices connecting directly without an AP.
- **ESSID** - the name shared by a group of APs, letting a device roam between them without reconnecting.
- **Captive portal** - authentication screen shown when connecting to an AP.
- **WPA/WPA2/WPA3 PSK** - everyone shares the same pre-shared key.
- **WPA/WPA2/WPA3 Enterprise** - authenticates users individually against an authentication server.

### Securing wireless

- Ensuring all wirelessly transmitted data is encrypted is the single most important control.
- **MIC (Message Integrity Check)** - confirms encrypted wireless data is unchanged on arrival.
- **WPA (Wi-Fi Protected Access)** - built to replace the insecure WEP.
- **Microwaves interfere with the 2.4 GHz band**, not 5 GHz.

---

## 2.4 Physical Installations

- **Distribution frame** - passively terminates cables.
- **MDF (Main Distribution Frame)** - central point of the network, usually the data center. A good testing point.
- **IDF (Intermediate Distribution Frame)** - an extension of the MDF that connects users to the network. Its purpose is to **reduce the distance data must travel** by acting as a secondary hub, typically one per floor.
- Most racks are standardized at 19 inches wide.
- Rack height is measured in units; 1U = 1.75 inches.
- **Hot and cold aisles** - manage airflow in server rooms to keep equipment in an optimal environment.
- **Fiber bend radius** - fiber must not be bent too aggressively or it will break.

### Power

- **Amp (ampere)** - rate of electron flow past a point in one second.
- **Volt** - the electrical pressure pushing electrons through a point.
- **Watt** - the amount of energy being consumed.
- **V x A = W**
- **AC (Alternating Current)** - distributes electricity efficiently over long distances.
- **DC (Direct Current)** - current moves in one direction at one voltage.
- **UPS (Uninterruptible Power Supply)** - short-term power backup to maximize server uptime.
