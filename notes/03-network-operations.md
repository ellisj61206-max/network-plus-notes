# Domain 3.0 - Network Operations

Exam weight: 19%

---

## 3.1 Documentation and Life Cycle Management

### Documentation types

| Document | What it shows |
| --- | --- |
| Physical network map | Physical layout and wiring path; no logical interfaces |
| Logical network map | High-level view including WAN, used for planning |
| Rack diagram | A single rack in detail, without entering the data center |
| Cable map / wiring diagram | The wires in an office or building, including connector and cable types |
| Network diagram | Devices arranged by the OSI layer they operate at |

- **IPAM (IP Address Management)** - plan, track, and configure DHCP and IP addressing. Makes IP problems easier to spot.
- **SLA (Service Level Agreement)** - the minimum services that must be provided.
- **Site survey** - maps wireless infrastructure for a site, usually with a heat map.

### Life cycle management

- **End-of-life** - the manufacturer stops supporting the product.
- **End-of-support** - the manufacturer stops updating it, which makes it a significant security risk.
- **Firmware** - the software inside the hardware; the OS of a hardware device.
- **Decommissioning** - what you do with a device once you are done with it. You do not want critical information going in the trash.
- Documenting **all** hardware and software changes is the most important part of change management.
- **Production configuration** - the standard config for a deployed device, usually tested before deployment.
- **Backup configuration** - the fallback if the production config does not go as planned.
- **Baseline / golden config** - the ideal standardized configuration for a device or system.

---

## 3.2 Monitoring

### SNMP

- **MIB (Management Information Base)** - the database SNMP stores information in.
- **SNMP v1** - original structured tables, no encryption.
- **SNMP v2** - data type enhancements and bulk transfers, still unencrypted.
- **SNMP v3** - adds encryption.
- **OID (Object ID)** - the value SNMP queries to get a reading.
- **Walking a MIB** - stepping through all OIDs on an IP to gather management data.
- **SNMP trap** - a real-time alert sent from a network-enabled device to central management.

### Logs and monitoring

- **NetFlow** - gathers traffic statistics from all sources on a network. Uses a probe to watch communication and summarize records.
- **Protocol analyzers** - solve complex application issues on the network. Wireshark is the standard example.
- **Network performance baseline** - maps out what a normal day looks like, so deviations stand out.
- **Syslog** - the standard for message logging; each entry gets a facility code. Feeds into a SIEM.
- **SIEM** - logs all security events on a network.
- **API integration** - control and manage devices programmatically, without SSH or Telnet. Enables CLI automation.
- **Port mirroring** - copies traffic from one port to another configured port for analysis of traffic, performance, or security.
- Note: port mirroring copies traffic for analysis. To stop sensitive data leaving a segment, the right tool is **DLP (Data Loss Prevention)**, not port mirroring.

---

## 3.3 Disaster Recovery

- **DRP (Disaster Recovery Plan)** - the steps taken to recover after an attack or data loss.
- **RTO (Recovery Time Objective)** - how long it takes to get back up and running, measured from the normal service level or baseline.
- **RPO (Recovery Point Objective)** - how much data loss is acceptable, expressed in time. Drives how often you back up.
- **MTTR (Mean Time To Repair)** - average time an issue takes to fix.
- **MTBF (Mean Time Between Failures)** - used to predict how long you can go without an outage.

### Recovery sites

| Site | What is there |
| --- | --- |
| Cold | Nothing in it. No hardware. A temporary space |
| Warm | Somewhere in the middle: power, racks, partial equipment |
| Hot | An exact replica, same hardware, managed like the live data center |

### Network redundancy

- **Active-passive** - two devices installed, only one operating; the other is the failsafe. Configs must be identical with real-time communication between them.
- **Active-active** - both devices in use simultaneously. More complex to manage than active-passive.

---

## 3.4 IPv4/IPv6 Support Services

### DHCP

DHCP automates what would otherwise be manual IPv4 configuration. Four steps, **DORA**:

1. **Discover** - find a DHCP server.
2. **Offer** - receive an IP configuration offer.
3. **Request** - lock in the offer.
4. **Acknowledge** - confirm to the server that the config is now running.

- DHCP Discover requests are broadcasts (255.255.255.255), so they only travel the local subnet.
- **DHCP relay** - a router configuration that lets DHCP broadcast requests leave the local subnet.

### Configuring DHCP

- **Address assignment** - the server picks from the pool of available addresses in that scope. The address is reclaimed after the lease expires.
- **Lease period** - how long a system may hold an address.
- **Address reservation** - locks a specific IP to a device by matching its MAC address.
- **T1 timer** - at 50% of lease time, the device checks in with the DHCP server to renew.
- **T2 timer** - at 87.5% of lease time, the device tries to renew with any available DHCP server.

### IPv6 and SLAAC

- **NDP (Neighbor Discovery Protocol)** - uses multicast instead of broadcast to obtain an address.
- **SLAAC (Stateless Address Autoconfiguration)** - configures an IP without a DHCP server, asking a neighbor for config info via NDP, using RS (router solicitation) and RA (router advertisement) to find routers on the subnet.
- **DAD (Duplicate Address Detection)** - confirms no duplicate IPs exist on the network.

### DNS

- **FQDN (Fully Qualified Domain Name)** - the full domain name of a site.
- **Primary and secondary DNS servers** - the secondary is contacted when the primary is unreachable. Redundancy.
- **Local name resolution** - used for test servers or when no DNS server is configured. Uses a hosts file mapping names to addresses.
- **Forward lookup** - name to IP.
- **Reverse lookup** - IP to FQDN.
- Command line tools: dig or nslookup. Forward: dig example.com. Reverse: dig -x x.x.x.x.
- **Authoritative server** - the main server of a DNS zone, holding the source files.
- **Non-authoritative server** - a branch of the authoritative server in the same zone, usually serving cached information.
- **DNSSEC** - digitally signs DNS responses to guarantee integrity.
- DNS requests and responses are otherwise sent in the clear.

### DNS record types

| Record | Purpose |
| --- | --- |
| SOA | Start of authority; describes the DNS zone |
| A | IPv4 address of a host |
| AAAA | IPv6 address of a host |
| CNAME | Maps an alias to the canonical name |
| MX | Host name of a mail server |
| TXT | Arbitrary text, often machine-readable instructions |
| NS | Name servers for a domain |
| PTR | Reverse of an A/AAAA record; points to a domain name |

---

## 3.5 Remote Access

### VPNs

- **VPN concentrator** - encryption and decryption device, usually built into a firewall.
- **Client-to-site VPN** - remote device connects in to a concentrator. Laptops, phones, BYOD.
- **Site-to-site VPN** - always on, usually built into the firewall, connects networks and sites.
- **Clientless VPN** - runs inside an HTML5 browser with no software installed.
- **Full tunnel vs split tunnel** - full tunnel sends all traffic through the VPN and the client does not decide. Split tunnel sends only VPN-destined traffic through the tunnel and the rest out normally. **Full tunnel is the more secure option**, because all traffic routes through the company's secure network.

### Remote access methods

- **SSH** - secure connection to switches and devices.
- **VNC** - alternative to RDP, uses the RFB protocol.
- **Console cable** - direct physical connection to a system. Useful when a device is not reachable any other way.
- **Jump server** - one device that reaches all others configured to it. Must be heavily secured, since it allows mass connection.
