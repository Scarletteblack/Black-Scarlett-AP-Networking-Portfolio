# Switch Security

# Design and Planning

## Definitions
- Threat &rarr; any potential issue that has the potential to cause harm to a network, system, or data
- Vulnerability &rarr; weakness in a system/network which can be exploited
- Control &rarr; refers to managing network traffic, security, and resources, all helping to protect against threats
- Prevent vs. Mitigate &rarr; Prevent: eliminate the possibility of a security incident or network disruption, Mitigate: minimizing the impact and likelyhood of a security threat 


## Common LAN Threats & Why Switches Are Vulnerable

Inside a LAN, the easiest device to 

Which device inside a LAN do you believe would be the easiest for an attacker to
compromise, and why?
• Does being “inside” the network make a device safer or more dangerous than being
outside the network?
• How much do you think a typical device can see or learn by default inside a
switched LAN?

### Scenario Assessment

| Scenario | Symptoms|  Hypothesis  |  Justification  |
|---------|--------------------|-----------------------------------------------|---------------------------------------------|
|    A     |      Several devices report connectivity/speed issues despite being connected to the switch. The default gateway is different from what was expected.              |      APR Spoofing     |  A rogue device is acting as the default gateway and therefore other devices on the network are experiencing latency issues and the gateway address would be different from expected   |
|    B    |     A switch begins to display increased CPU usage, resulting in the network performance becoming inconsistent. The switch logs reveal that hundreds of MAC addresses are appearing on a single switch port over a short window.                |   MAC Flooding Attack     |  The CPU is overload with fake MAC addresses slowing down the whole network  |
|    C    |          The switch is assigning IP addresses to devices but placing them in the wrong subnet. Some users report being unable to access the internet, while others experience DNS issues.           |   DHCP Issue |   The DHCP is assigning incorrect IP configurations to some devices revealing that while the officail DHCP seems to be functioning normally, there is some inconsistancy  |
|    D    |        An unregistered device appears on the LAN and is communicating with other hosts. The device was never approved to be on the LAN, and logs show that activity began from a wall jack in a public, lightly monitored area.              |     Unauthorized Plug-In     | There is a lack of port security and therefore plugged in devices are implicity trusted and given access to the network  |
|    E   |  A student workstation is recorded communicating with internal systems that should not be accessible to students. No firewall alerts were triggered, and traffic appears to be internal   |      VLAN Misconfiguration   |    The VLAN responsible for the segmentation between student devices and other internal systems did not function properly   |

---

### VM Evidence

<img width="1378" height="510" alt="arping" src="https://github.com/user-attachments/assets/9763e3a4-d3b9-41cd-ab91-7fcc789bcebe" />
<img width="650" height="310" alt="tcpdump" src="https://github.com/user-attachments/assets/90ab0051-0f8e-496c-a941-fde16b11276c" />

An attacker could missuse this information as ARP requests and replies are open and reveal active IPs and hostnames with associated MAC addresses. For instance, the IP 10.12.17.123 responds consistently and numerous hostnames appear in the **tcpdump arp** comand. This vulnerability allows attackers to view live hosts and target speciffic devices for various attacks, exploiting the trusting nature of this LAN.

--- 


# Technical Development

### From Observations to Decisions

### Visualizing Switch Security with Packet Tracer

| Senario | Evidence | Explination |
|-----------------|------------------------------------|--------------------------------------------------------|
| A - Flat Network (No Security Controls |                                    | What this network allows by default? Why this design assumes trust between devices? How this could create security risk?                                               |
| B - VLAN Segmentation (Visual Separation)|                   |                                    |  How VLANs change what devices can see? Why VLANs reduce broadcast visibility? VLANs alone do not enforce full security?                                                |
| C - Port Security (Limiting Physical Access)|                                    | How port security relates to physical access? What type of risk it helps mitigate? What it cannot protect against on its own |
| D - Conceptual View of DHCP Snooping, DAI, and ACLs|                                    | Which devices should be trusted? Which devices should be restricted? Where should the switch enforce rules?      |


| VM Evidence |Vulnerability | Control | Why This Control Mitigates Risk |
|---------|--------------------|----------------------------------------|---------------------------------------------|
|  <img alt="aandb" src="https://github.com/user-attachments/assets/cb148cb3-c870-4ace-bee6-508857ec0fc6" />  |     Flat Network        |  Adding separiations to the network | This separations prevents unuthorised device communication |
|  <img width="504" height="217" alt="10" src="https://github.com/user-attachments/assets/4ab254d1-1556-4a2f-b2ae-664b269af779" />   |  No Network Segmentation  |  Adding VLANs to the Network |   The addition of separation would ensure that devices do not have access to the full network   |   
|   <img width="667" height="540" alt="unnamed-1" src="https://github.com/user-attachments/assets/28fd1666-f108-4309-8ef1-b3474cd5f492" />  | Lack of Joining Restrictions |   Adding Port Security |   The addition of port security midigates the risk of rogue devices joining the network   | 
|    <img width="719" height="720" alt="unnamed" src="https://github.com/user-attachments/assets/625d3ef0-b945-436d-bdb0-7c95a0b950c1" /> | Unrestricted Network  |  Adding an ACL |   This would ensure that only allowed devices (baseed on IP addresses) could access sensitive material  |   

## Task C - Mini-Threat Simulation

The attacker already has access to the network after the teacher opens the phishing email while connected to the school network. In this situation, the network traffic itself is most directly targeted.

1. What must the attacker already know or discover?
2. Which device is most directly targeted?
Choose one and explain why:
• Another end device
• A server
• The switch
• Network traffic itself
3. What would legitimate users likely notice (if anything)?
Be realistic — many attacks are quiet.

4. Which of your virtual machines best resembles the attacker’s perspective?
Choose one:
• Ubuntu Desktop VM
• Linux Server VM
Explain your choice based on visibility and access, not labels.
Important Rules
• Do not name specific attacks
• Do not propose fixes yet
• Do not assume perfect security
• Focus on what is possible, not what is ideal
You are reasoning from assumptions and evidence — just as a real network administrator must.


<img width="795" height="446" alt="Screenshot 2026-01-20 at 2 02 12 PM" src="https://github.com/user-attachments/assets/396c155a-0f29-4f11-9e1b-771ad8b153c7" />

### Define Trust and Restrictions

**Students &rarr; Server**

**Students &rarr; Teachers**

**Students &rarr; Administration**

**Teachers &rarr; Servers**

**Administration &rarr; Servers**


Answer in 2–3 sentences on your digital portfolio:
• Which VLAN(s) should be considered least trusted?
• Which VLAN(s) require the most protection?
• Where should the switch be most strict?

### Control Layering

Write one short paragraph explaining:
• Why VLANs alone do not fully secure your design
• Why DHCP Snooping is necessary in addition to VLANs
• Why Dynamic ARP Inspection (DAI) depends on DHCP Snooping
• Why ACLs are still needed after segmentation
Don’t forget, use the word mitigate, not prevent.

## Professional Security Rationale

You have designed a VLAN-based switched LAN and made intentional decisions about trust,
visibility, and communication. Now, you will step back from the diagram and explain your
reasoning the way a network professional would.

justify why controls must work together and to recognize what risks still remain.

### Control Interaction and Dependency

Explain how layered switch security controls work together in your design.
Your explanation must address:
• Why VLAN segmentation and DHCP Snooping must be used together to mitigate
internal risk
• Why Dynamic ARP Inspection (DAI) depend on DHCP Snooping to function correctly
• Why Access Control Lists (ACLs) are still required even after VLAN segmentation is in
place
Use:
• Precise security language
• The word “mitigate”, not prevent
• Realistic assumptions about trust and misconfiguration

### Residual Risk and Detection Limits

Even well-designed networks are not perfectly secure.
Reflect on the following:
Which internal LAN threat would be hardest for a network administrator to detect — and
why?
Your reflection must:
• Reference evidence from your virtual machines
• Describe relevant switch behavior
• Address trust assumptions inside a switched network
