# Domain 5.0 - Network Troubleshooting

Exam weight: 24%. The largest single domain, and the one I scored worst on going in.

---

## 5.1 Troubleshooting Methodology

1. **Identify the problem** - ask the user questions. Try to duplicate the problem on another system; it makes the cause much easier to isolate.
2. **Establish a theory of probable cause** - start with the obvious. Occam's razor. Use a top-down or bottom-up approach through the OSI model.
3. **Test the theory** - evaluate the test. What changed?
4. **Establish a plan of action** - find the simplest way to implement the fix. Make backups and have a rollback path.
5. **Implement the plan** - execute during a window that works.
6. **Verify full system functionality** - confirm every part works as intended, and ask how to prevent recurrence.
7. **Document findings** - write up the process and the outcome for future use and prevention.

---

## 5.2 Cable, Interface, and Hardware Issues

### Cable issues

- **Cable writing** - the type and rating are printed on the cable sheath.
- **Cable categories** - the TIA standardizes cable construction. IEEE specifies the minimum cable for each standard: 1000BASE-T needs Cat 5 minimum, 10GBASE-T needs Cat 6 or 6a.
- **Cable tester** - qualifies a cable for the speeds you plan to run and verifies it works.
- **Crosstalk (XT)** - interference between pairs inside a sheath.
  - **NEXT (near-end crosstalk)** - measured at the transmitting end.
  - **FEXT (far-end crosstalk)** - measured away from the transmitter.
  - **AXT (alien crosstalk)** - interference from other cables.
  - **ACR (attenuation to crosstalk ratio)** - signal lost vs signal interfered with.
- **EMI** - avoid power cords, fluorescent lights, and anything else pushing electromagnetic interference into a cable.
- **Attenuation** - signal loss, increasing with distance and cable length.
- **Terminating cables** - preparing the cable end so it seats and functions properly.

### Interface issues

The Ethernet frame:

Preamble - SFD - Destination MAC - Source MAC - Type - Payload - FCS

- **Preamble and Start Frame Delimiter** - identify the start of the frame; not visible in a packet capture.
- **Type** - specifies the kind of data being carried.
- **Payload** - the data itself.
- **FCS (Frame Check Sequence)** - confirms the data was not altered in transit.
- **CRC (Cyclic Redundancy Check)** - compares the received frame to the sent one. A CRC mismatch means an error. **CRC metrics identify transmission error rates**, not bandwidth or throughput problems.
- **show interfaces** - displays interface errors and statistics on a switch.
- **LACP** - combines multiple physical interfaces into one logical channel, giving failover and higher aggregate speed.

Port status note: a port that is temporarily inactive because of network conditions, configuration, or security policy is **suspended**, not disabled.

### Hardware issues

- **PoE (Power over Ethernet)** - one cable for data and power. Power comes from the switch itself (endspan) or in-line (midspan). Common for IoT devices like cameras and lights.

| Standard | Power |
| --- | --- |
| PoE | 15.4 W DC |
| PoE+ | 25.5 W DC |
| PoE++ | 51 W or 71.3 W, can run 10GBASE-T |

- **Transceiver matching** - the transceiver must match the fiber type. Single-mode transceiver for single-mode fiber, multi-mode for multi-mode.

---

## 5.3 Switching Issues

- **BPDU (Bridge Protocol Data Unit)** - how spanning tree sends topology updates and configuration changes.
- **Root bridge** - the bridge with the lowest bridge ID.
- **Gateway of last resort** - where a packet is sent when its destination route is not in the routing table.
- A port that is **administratively down** is reactivated with the **no shutdown** command.
- To verify which switch ports belong to which segment, use **show vlan**, not show mac-address-table.
- To find which port a workstation is plugged into, **review the switch MAC address table**.

---

## 5.4 Wireless Issues

- **Disassociation frames** - sent from an AP or device to temporarily or permanently disconnect a device. Because they are not authenticated, they can be abused for denial of service.

---

## 5.5 Tools

### Software tools

- **CDP (Cisco Discovery Protocol)** - discovers information about connections to switches on a switched network. Cisco-specific.
- **LLDP (Link Layer Discovery Protocol)** - the vendor-neutral equivalent.

### Command line tools

- **tracert** - Windows trace command.
- **traceroute** - macOS/Linux/Unix trace command. Increases TTL by one per request so the full path can be recorded.
- **tcpdump** - captures packets from the CLI on macOS/Linux/Unix. Writes to a pcap file for Wireshark.
- **windump** - the Windows version of tcpdump.
- **netstat** - network statistics.
  - netstat -a - all active connections
  - netstat -b - binaries (Windows)
  - netstat -n - IPs only, no name resolution
- **ipconfig** (Windows) / **ifconfig** (Linux, macOS) / **ip** (newer Linux) - shows IPv4 and IPv6 info.
- **arp** - the layer 2 equivalent of ipconfig. arp -a shows the local ARP table.

### Hardware tools

- **Tone generator** - locates a cable in a large environment.
- **Cable tester** - verifies a cable is punched down or terminated properly and works internally.
- **Physical switch taps** - plug into a switch to send a copy of transmitted data to a protocol analyzer.
- **Wi-Fi analyzer** - analyzes 802.11 signals, identifying open channels, APs, and sources of interference.
- **Visual fault locator** - a flashlight for fiber optics; finds physical problems inside the cable.

### Basic network device commands

| Command | What it shows |
| --- | --- |
| show mac-address-table | The MAC table for the device |
| show route | Routes and next hops the router takes |
| show interface | Settings of a logical interface |
| show config | The device configuration |
| show arp | The ARP cache |
| show vlan | VLANs associated with a switch |
| show power | PoE power used by devices and switch capacity |
