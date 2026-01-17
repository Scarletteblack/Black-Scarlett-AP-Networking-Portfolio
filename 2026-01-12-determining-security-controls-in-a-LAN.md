# Determining Security Controls In A LAN

## Planning & Conceptual Understanding 

Clear evidence of planning and conceptual understanding. Portfolio includes
notes or explanations distinguishing threats, vulnerabilities, and controls;
demonstrates understanding of flat LAN risk, internal trust, and physical vs
technical security.

#### Security Controls

##### Port Security

**Limiting MAC Addresses** is a form of port security that allows only a specific number of approved devices to connect, blocking any others. This mitigates the risk of attackers plugging in a rogue device and accessing the network without authorization.

**Sticky MACs** allow a switch to automatically learn and permanently store approved MAC addresses on a port. This simplifies configuration while preventing new or unauthorized devices from connecting to the network.

**Violation Modes** define how a switch responds when a port security rule is broken. It limits damage by blocking traffic, alerting administrators, or disabling compromised ports.


##### VLAN Segmentation

**Limiting Broadcast Domains** ensures broadcast traffic is separated into various and specific VLANs. This reduces unnecessary and unwanted traffic, restricting how much information devices can observe.

**Isolating Sensitive Systems** ensures that critical devices are in separate VLANs with controlled access. This prevents attackers from easily reaching sensitive systems after compromising a less secure device.

##### DHCP Snooping

**DHCP Snooping** designates ports as trusted or untrusted and blocks unauthorized devices on the network. A DHCP Snooping table is used to record valid MAC addresses as well as devices that are not allowed on the network. This prevents attackers from assigning malicious IP configurations that enable traffic interception.

##### Dynamic ARP Inspection (DAI)
Type: Control
Definition: DAI validates ARP messages against trusted DHCP Snooping data before allowing them on the LAN.
Prevents/Impact: It blocks ARP spoofing attacks that could redirect or intercept network traffic.

b. ARP Validation
Type: Control
Definition: ARP validation checks whether ARP messages match known, legitimate IP–MAC bindings.
Prevents/Impact: It prevents forged ARP replies from reaching other devices.



##### Access Control Lists (ACLs) on Switches
Type: Control
Definition: ACLs are rule sets that permit or deny traffic based on defined criteria such as IPs and ports.
Prevents/Impact: They restrict lateral movement within the LAN, limiting attacker access even after compromise.
a. Restricting East–West Traffic
Type: Control
Definition: Restricting east–west traffic limits communication between internal devices or VLANs.
Prevents/Impact: It prevents unauthorized access between internal systems, such as students reaching servers.
b. Traffic Inspection Rules
Type: Control
Definition: ACL rules inspect traffic based on source, destination, protocol, and port number.
Prevents/Impact: They enforce precise network security policies controlling who can communicate.
c. ACLs vs. Firewalls
Type: Control (Conceptual Comparison)
Definition: ACLs control internal LAN traffic, while firewalls typically filter traffic between networks.
Prevents/Impact: ACLs reduce internal attack spread where perimeter firewalls provide no protection.




#### Threats 

**Rogue DHCP Server** is an unauthorized device that distributes incorrect IP settings to devices. It can enable man-in-the-middle attacks by redirecting traffic through a gateway that the attacker controls.


**ARP-Based Attacks** manipulate ARP messages to intercept or redirect traffic. These attacks can lead to session hijacking, data theft, and man-in-the-middle attacks.


#### Vulnerabilities 

ARP Trust Weakness occurs because ARP lacks built-in authentication and blindly trusts received ARP replies. This vulnerability allows attackers to tamper with ARP tables and impersonate other devices.


#### Risks Involving Flat LANs 

Flat LANs pose significant security risks because all devices share the same broadcast domain, allowing attackers to easily see, intercept, or manipulate traffic from any other device. Additionally, one compromised device can spread laterally across the network, since there is no segmentation to isolate various systems.

#### Internal Trust 

Internal trust is the assumption that devices and users inside a network are safe and behave correctly without malicious intent. Its risk is that if this trust is misplaced, compromised devices or insider threats can freely access and exploit the network.

#### Physical vs Technical Security

**Physical security** protects the tangible components of a network, such as servers, switches, and wiring, with locked doors, security guards, and cameras. **Technical security** protects the network and its data through software and hardware controls, such as firewalls, ACLs, VLANs, and encryption, preventing unauthorized access to the network.

---


### LAN Security Investigation



| Scenario Letter | Symptoms |  Hypothesis  |  Justification |
|-----------------|-----------------------|----------------------------------------|-------------------------------------------------------------|
|   A  |  Default gateway does not match router    |   There is an issue with the DHCP server   |     Connectivity issues and network behavior changes |
|       B       |   Switch CPU spikes and thousands of MACs appear on one port     |       MAC Flooding Attack    |        Multiple MACs show up on one port and switch CPU spikes   |
|    C     |       Receives network settings from an unknown DHCP source   |    Misconfigured Router  |    Unknown DHCP source and conectivity issues        |
|    D   |    New device appears inside the broadcast domain and communicates broadly  |      Administrative Issue       |  Communicate broadly and new devices appearing     |
|    E  |  A host reaches internal systems it should not access |Security Policy Bypass|   Fire walls and other encryptions are not working |

#### Reflection: 

The MAC Flooding Attack was the easiest conclusion to come to and the one that the group felt most confident in initially. This is due to the straightforward and very evident symptoms regarding MAC Flooding Attacks. Scenario C was the most difficult to identify, as initially the group was not thinking about the router, but instead the rogue device. Talking over the initial conclusions with another group solidified both groups' answers, ensuring everyone was confident regarding the scenarios. General patterns include abnormal network behavior, detection after the attacks have occurred, and a lack of security where the attacks are occurring. 

---

### VM Threat Evidence

TO BE COMPLETED ON TUESDAY

---

### Appropriate Security Controls/Common Vulnerabilities Within Simple LAN
#### Linux:
<img width="852" height="348" alt="ipaddrroute" src="https://github.com/user-attachments/assets/f3038865-9ef0-4078-9e8e-7a6356e57955" />
<img width="1162" height="520" alt="sudotcpdump" src="https://github.com/user-attachments/assets/1449bc34-d13e-4308-a92b-66ac6cdbc2fa" />

#### Ubuntu:
<img width="1380" height="514" alt="sudoarping" src="https://github.com/user-attachments/assets/663f2016-3222-4d67-a052-07408d0d6794" />

#### Reflection: 

1. What information does ARP reveal about devices on a LAN?
2. Why does ARP assume devices are trustworthy?
3. How does this make ARP vulnerable to spoofing?
4. Why was Bridged mode required for this lab to work?
5. Include evidence from commands used

#### LAN Attack Path Diagram (Homework) 

1. The Devices Involved
• VM #1 (workstation)
• VM #2 (server-like device)
• The switch
• The default gateway or router

2. One Internal LAN Threat
Choose one of the following to illustrate:
• ARP Spoofing
• MAC Flooding
• Rogue DHCP Server
• Unauthorized Plug-In Device
• Lateral Movement

3. A Sequence of Events
Use arrows or numbered steps to show how the attack unfolds. Include at least three to five
steps that show:
• What the attacker sends
• How the switch responds
• How victim devices are affected
• Where the LAN’s trust assumptions fail


4. Annotations
Label each major component and step with brief, clear explanations.
Your diagram should make sense to someone who did not complete the lab.


paragraph reflection
Why this attack succeeds when no internal security controls are present
• Which security control introduced in today’s reading would stop this attack
• How that control prevents the attack from progressing
Your explanation should connect directly to concepts from today’s reading (Port Security,
VLAN segmentation, DHCP Snooping, Dynamic ARP Inspection, ACLs).

---

### Physical Security Controls for Network Devices and Physical Spaces

#### Enterprise Physical Threats Analysis

- Six physical vulnerabilities relevant to a pharmaceutical research environment. Each vulnerability must be written as a clear weakness, not a solution.
- Each vulnerability should include: What the vulnerability is, Where it exists in the facility, Why it presents serious risk in this industry

#### Physical Security Plan - Pharmaceutical Research Facility

- Describe a layered physical security strategy that includes all five categories:
- Required Categories (Must All Be Addressed)
1. Environmental Controls
• Temperature, humidity, air quality, fire suppression
2. Access Control
• Badges, biometrics, mantraps, zoning
3. Surveillance and Detection
• Cameras, monitoring rooms, alarms, logging
4. Hardware Security
• Locked racks, secured network closets, port protection
5. Personnel and Procedures
• Visitor handling, escort policies, access reviews, training

For each category:
• Describe specific controls
• Explain how they protect research, data, and network infrastructure
• Reference ideas or examples seen in the videos


#### Diagram: 
requirements: 
• Facility perimeter
• Entry points
• Security zones (public, restricted, highly restricted)
• Data center and network spaces
• Labs and clean rooms
• Monitoring and control areas

Diagram Requirements:
• Clearly labeled layers of security
• Icons or symbols for:
o Cameras
o Access control points
o Locked areas
o Environmental protections
• Arrows or boundaries showing restricted movement

#### Risk Justification and Priority Controls

Write 1–2 paragraphs explaining:
• Which physical controls are the highest priority and why
• How these controls reduce the likelihood and impact of:
o Theft
o Sabotage
o Data compromise
o Regulatory violations
• How physical security supports technical controls, such as:
o Network segmentation
o Access control lists
o Monitoring systems

Write this as if addressing executive leadership at the company.

---

### [Switched LAN Security Controls Report](https://docs.google.com/document/d/e/2PACX-1vQnK0U0c5t3UXuoHlh1Vlx0YkpLQGElYG0Mjka2JinEu0iKzmfN7vlz6MFYnahnNF1-qFzcKMkvWVVW/pub)

 ---
