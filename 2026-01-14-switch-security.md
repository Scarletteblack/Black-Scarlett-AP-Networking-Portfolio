# Switch Security

# Design and Planning

## Definitions
- Threat &rarr; any potential issue that has the potential to cause harm to a network, system, or data
- Vulnerability &rarr; weakness in a system/network which can be exploited
- Control &rarr; refers to managing network traffic, security, and resources, all helping to protect against threats
- Prevent vs. Mitigate &rarr; Prevent: eliminate the possibility of a security incident or network disruption, Mitigate: minimize the impact and likelihood of a security threat 


## Common LAN Threats & Why Switches Are Vulnerable

Inside a LAN, endpoint devices would be the easiest to compromise as they often have low security. Being "inside" the network makes a device more dangerous as it already bypassed the external network security and only has to deal with the internal controls. On a typical LAN, devices can see the broadcast traffic, like the DHCP and ARP, allowing devices to see live hosts and MAC/IP addresses. 

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

| VM Evidence |Vulnerability | Control | Why This Control Mitigates Risk |
|---------|--------------------|----------------------------------------|---------------------------------------------|
|  <img alt="aandb" src="https://github.com/user-attachments/assets/cb148cb3-c870-4ace-bee6-508857ec0fc6" />  |     Flat Network        |  Adding separiations to the network | This separations prevents unuthorised device communication |
|  <img width="504" height="217" alt="10" src="https://github.com/user-attachments/assets/4ab254d1-1556-4a2f-b2ae-664b269af779" />   |  No Network Segmentation  |  Adding VLANs to the Network |   The addition of separation would ensure that devices do not have access to the full network   |   
|   <img width="667" height="540" alt="unnamed-1" src="https://github.com/user-attachments/assets/28fd1666-f108-4309-8ef1-b3474cd5f492" />  | Lack of Joining Restrictions |   Adding Port Security |   The addition of port security midigates the risk of rogue devices joining the network   | 
|    <img width="719" height="720" alt="unnamed" src="https://github.com/user-attachments/assets/625d3ef0-b945-436d-bdb0-7c95a0b950c1" /> | Unrestricted Network  |  Adding an ACL |   This would ensure that only allowed devices (baseed on IP addresses) could access sensitive material  |   


# Testing and Evaluation

## Task C - Mini-Threat Simulation

The attacker would need to discover the network information, like IP address, default gateway, and live hosts, which are all discoverable via observing the LAN traffic. In this scenario, the network traffic is most directly targeted, so the attacker can collect information in order to further take over the network. Legitimate users would likely notice little to no changes in the network behavior, aside from slightly slower responses. The Ubuntu Desktop VM best matches the attacker's point of view because it behaves like a regular endpoint device on the network but has visibility into the local network behavior.



<img width="795" height="446" alt="Screenshot 2026-01-20 at 2 02 12 PM" src="https://github.com/user-attachments/assets/396c155a-0f29-4f11-9e1b-771ad8b153c7" />

### Define Trust and Restrictions

**Students &rarr; Server** - Restricted: Sensitive data on the servers should not be accessable to students, however, speciffic student records on the servers should be accessable to indivisual students. 

**Students &rarr; Teachers** - Restricted: Access should be restricted to protect teachers files and other sensitive data, however, monitered pathways of communication should be accessible to students.

**Students &rarr; Administration** - Denied: There is no reason that students need to comunicate directly with Administrative workstations and if there are extrenuation sercumstances in which a student might need to, they should go through monitered chanels with an advisor or counciler. 

**Teachers &rarr; Servers** - Restricted: Teachers require access to update information stored on the servers such as grades, incedents, and notes, though they do not need full access as personal student information should not be made avalible to teachers unless deamed neccessary. 

**Administration &rarr; Servers** - Restricted: While administrators need more access to the servers, unrestricted access is not a good idea in order to keep all sensitive data safe. 

Student VLANs and Guest VLANs should be trusted least as there are the most students thus the highest volume of devices and often lack security. Server VLANs should be the most secured as they contain private and sensitive data for everyone at the school. The switch should be strictest at the access layer where devices are connecting in order to ensure that unauthorized devices don't join the network.



## Professional Security Rationale

You have designed a VLAN-based switched LAN and made intentional decisions about trust,
visibility, and communication. Now, you will step back from the diagram and explain your
reasoning the way a network professional would.

justify why controls must work together and to recognize what risks still remain.


### Residual Risk and Detection Limits

Even well-designed networks are not perfectly secure.
Reflect on the following:
Which internal LAN threat would be hardest for a network administrator to detect — and
why?
Your reflection must:
• Reference evidence from your virtual machines
• Describe relevant switch behavior
• Address trust assumptions inside a switched network
