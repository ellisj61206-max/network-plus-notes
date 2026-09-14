# Missed Questions

Every practice question I got wrong, with my answer next to the correct one. This was the single most useful study artifact I produced - the wrong answers showed patterns the scores alone did not.

Two sources: section quiz retakes, and a 100-question full practice exam.

---

## Section quiz retakes

### Network Protocols

**Which IPsec component provides data confidentiality?**
My answer: DES
Correct: **ESP (Encapsulating Security Payload)**

**Which part of the IPsec suite provides data integrity and authentication but not encryption?**
My answer: ESP
Correct: **AH (Authentication Header)**

Takeaway: ESP encrypts, AH authenticates. I had these backwards in both directions, which is why I missed them as a pair.

**Which does NOT refer to GRE?**
My answer: Does not provide encryption or security on its own
Correct: **Provides authentication, encryption, and data integrity**

Takeaway: GRE is a tunnel with no security of its own. The negation in the question is what caught me.

**Three features of Telnet:**
- Provides username and password authentication
- Transmits data in an unencrypted form
- Enables remote login and command execution

### Cloud Computing Concepts

**Which solution replaces traditional network hardware functionality with software via virtualization?**
My answer: SDN
Correct: **NFV (Network Functions Virtualization)**

Takeaway: NFV virtualizes the network *functions*. SDN separates the control plane from the data plane. Related, not interchangeable.

**A cloud gateway that lets instances send and receive unencrypted traffic to and from the internet:**
My answer: Default gateway
Correct: **Internet gateway**

### Network Cabling

**Which refers to coaxial cabling?**
- Used to carry cable television signals
- Copper cabling
- Offers protection against external interference
- Used in broadband cable internet access
- Features a single, central conductor surrounded by insulation

**What does NOT refer to Cat 5 cabling?**
My answer: Supports maximum cable segment length of 100 meters
Correct: **Supports maximum cable segment length of 55 meters**

**Maximum data transfer rate for Cat 7 over a standard 100-meter run:**
My answer: 25 Gbps
Correct: **10 Gbps**

### Routing Technologies

**Which are link-state routing protocols?**
My answer: IS-IS, EIGRP
Correct: **IS-IS, OSPF**

Takeaway: EIGRP is Cisco's advanced distance-vector protocol, not link-state. This one cost me repeatedly.

### Physical Interface Troubleshooting

**What performance issue do CRC metrics help identify?**
My answer: Bandwidth / throughput
Correct: **Transmission error rates**

**Which port status means a port is temporarily inactive due to network conditions, configuration, or security policy?**
My answer: Disabled
Correct: **Suspended**

### Network Services Troubleshooting

**Which refers to a switch port that does not forward traffic to prevent loops?**
My answer: Disabled port
Correct: **Blocked port**

Takeaway: blocked, suspended, and disabled are three different states and the exam tests the difference. Disabled = an admin turned it off. Blocked = STP broke a loop. Suspended = conditions or policy.

**Which is NOT a common metric used by routing protocols to determine the optimal path?**
My answer: Load
Correct: **Administrative distance**

Takeaway: administrative distance ranks how trustworthy a routing *source* is. It is not a path metric.

---

## 100-question practice exam

**Q32. Advantage of a full tunnel VPN over split tunnel?**
My answer: Faster connection speeds for accessing external websites
Correct: **Increased security by routing all traffic through the company's secure network**

**Q43. Monitoring the contents of data between a secure segment and the rest of the network to prevent leaks. Best tool?**
My answer: Port mirroring
Correct: **DLP (Data Loss Prevention) system**

Takeaway: port mirroring copies traffic for analysis. DLP inspects content and acts on it.

**Q52. Workstation is connected to a switch but the admin does not know which port. Best method to identify it?**
My answer: Run a packet capture on the workstation
Correct: **Review the switch's MAC address table**

**Q67. Which frequency range do microwaves interfere with?**
My answer: 5 GHz
Correct: **2.4 GHz**

**Q77. A diagram with detailed physical connection info, including connector and cable types. Which diagram?**
My answer: Logical diagram
Correct: **Wiring diagram**

**Q78. In the three-tier model, at which layer does routing primarily occur?**
My answer: Access layer
Correct: **Distribution layer**

**Q89. What purpose does an IDF serve, installed in each floor's wiring closet?**
My answer: To serve as the main connection point for external internet access
Correct: **To reduce the distance data must travel, acting as a secondary hub for network connections**

Takeaway: that description is the MDF. The IDF is the extension.

**Q92. Which show command verifies membership of switch ports in specific network segments?**
My answer: show mac-address-table
Correct: **show vlan**

**Q95. Best action if a network port is found administratively down but needs reactivating?**
My answer: Issue the 'port enable' command
Correct: **Issue the 'no shutdown' command**

---

## Patterns across everything I missed

1. **Paired protocols I had reversed.** ESP vs AH, NFV vs SDN, EIGRP vs OSPF. Learning them as a contrast rather than two separate definitions was what fixed it.
2. **Port state vocabulary.** Blocked, suspended, disabled, administratively down. Four states, four different causes.
3. **Negation questions.** Several misses were questions asking which option does NOT apply. Slowing down on the word "not" was worth real points.
4. **Tool vs purpose confusion.** Port mirroring vs DLP, packet capture vs MAC table. Knowing what a tool does is not the same as knowing when it is the right answer.
