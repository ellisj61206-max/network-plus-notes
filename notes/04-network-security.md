# Domain 4.0 - Network Security

Exam weight: 14%

---

## 4.1 Security Concepts

### Keys, certificates, and access

- **PKI (Public Key Infrastructure)** - the set of rules and policies around digital certificates and keys.
- **Certificate authorities** - let you know whether an unknown site or resource can generally be trusted.
- **Self-signed certificates** - internal CAs signing certificates for internal use.
- **IAM (Identity and Access Management)** - manages who can access what, using access control lists to hold the rules and policies.
- **RBAC (Role-Based Access Control)** - access granted based on your role and what that role needs.
- **Geographic restrictions** - assign access based on where a user connects from. Helps flag suspicious logins.
- **Geofencing** - allow or deny access based on physical location, e.g. only usable at the office.

### Physical security

- **CCTV** - networked back to one central point.
- Combine multiple physical factors: PIN and badge, fingerprint and PIN.

### Authentication (AAA)

- **Authentication** - proves you are who you say you are.
- **Authorization** - grants access based on who you are.
- **Accounting** - tracks that login data.
- **AAA server** - stores authentication information and communicates with devices requesting access to verify identity.
- **SSO (Single Sign-On)** - grants all assigned resources after one initial authentication, usually on a timer.
- **RADIUS** - one of the most common AAA protocols. Centralizes authentication for all users, available on nearly all systems.
- **LDAP** - based on the X.500 specification, lists data like a phonebook.
- **X.500** - allows attributes to be assigned to people, e.g. OU=marketing, L=London.
- **SAML** - grants tokens to a device as proof of authentication.
- **TACACS** - older authentication method originally for dial lines to ARPANET. Used by Cisco.
- **TOTP (Time-based One-Time Password)** - used in MFA. Text message codes, authenticator apps.

### Security technologies and risk vocabulary

- **Honeypot** - attracts attackers with a virtual server for them to explore. The bait.
- **Honeynet** - a real network acting as the bait. A much larger deception network.
- **Risk** - the exposure to something bad. How likely it is that something bad happens.
- **Vulnerability** - a weakness in a system or software. Some are never discovered.
- **Exploit** - someone taking advantage of a vulnerability. Something bad actually happening.
- **Threat** - the thing an attacker uses to exploit the vulnerability. Can also be physical, like a fire or flood in a data center.
- **CIA triad** - confidentiality, integrity, availability.

### Regulatory compliance

- **Compliance** - meeting the rules, policies, and regulations around your infrastructure and data.
- **Data localization** - data collected in a region must stay in that region.
- **GDPR** - EU rules for how individuals' data must be managed and protected.
- **PCI DSS** - standard for protecting payment card data.
- **Network segmentation** - improves performance, security, or compliance. Done with VLANs, physical separation, and other methods.
- **SCADA / ICS** - industrial control systems, segmented from the rest of the network.
- **OT (Operational Technology)** - the technology behind industrial equipment: power plants, traffic lights. Good segmentation gives these better redundancy and backups.

---

## 4.2 Common Attacks

### Denial of service

- **Network DoS** - a layer 2 loop without STP. Often unintentional.
- **DDoS** - an army of systems or bots attacking a server or network to take it down.
- **DDoS reflection and amplification** - turns a small attack into a large one, using protocols with weak security checks such as NTP, ICMP, and DNS. A small request to a service like DNS is redirected so the heavy response lands on the victim.

### VLAN hopping

1. **Switch spoofing** - pretend to be a switch, obtain a trunk link, then send and receive on any configured VLAN.
2. **Double tagging** - attach two VLAN tags to a crafted packet so the message reaches another VLAN. Send-only; you cannot receive back.

### MAC flooding

Exploits the fact that the MAC table has a finite size. Flood it with MAC addresses and:

- The switch starts forwarding traffic from unknown MACs out all ports.
- The attacker can capture network traffic, because everything is being flooded to every interface.

### Spoofing and poisoning

- **Spoofing** - an attacker presents information belonging to someone they are not.
- **ARP poisoning** - an attacker between two devices answers ARP requests with false IP and MAC information.
- **DNS poisoning** - sending fake responses to valid DNS requests, or altering the DNS database.
- **On-path attack** - the attacker sits in the middle of a conversation between two valid devices to read or alter the exchange. Formerly called man-in-the-middle.

### Rogue services

- **Rogue DHCP server** - DHCP has no built-in security. **DHCP snooping** only allows responses from legitimate servers.
- **Rogue APs** - countered with 802.1X on networked switches, so everyone authenticates before being allowed on.
- **Wireless evil twin** - mimics an existing access point by copying the SSID and captive portal, often trying to overpower the legitimate AP.

---

## 4.3 Device and Network Hardening

- **MAC filtering** - restricts access to listed MAC addresses. Easy to work around by observing MACs leaving the network and spoofing one.
- **ACL (Access Control List)** - rules for what is allowed on your network. Can restrict by IP, port, time, location, or a combination.
- **URL filtering** - blocks specific URLs or categories of site.
- **Screened subnet** - a public subnet adding a layer of separation between public-facing resources and the internal network.
