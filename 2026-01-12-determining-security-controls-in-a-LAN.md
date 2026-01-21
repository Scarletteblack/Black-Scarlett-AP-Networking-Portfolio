# Determining Security Controls In A LAN

# Planning & Conceptual Understanding 

---

## Security Controls

### Port Security

**Limiting MAC Addresses** is a form of port security that allows only a specific number of approved devices to connect, blocking any others. This mitigates the risk of attackers plugging in a rogue device and accessing the network without authorization.

**Sticky MACs** allow a switch to automatically learn and permanently store approved MAC addresses on a port. This simplifies configuration while preventing new or unauthorized devices from connecting to the network.

**Violation Modes** define how a switch responds when a port security rule is broken. It limits damage by blocking traffic, alerting administrators, or disabling compromised ports.

### VLAN Segmentation

**Limiting Broadcast Domains** ensures broadcast traffic is separated into various and specific VLANs. This reduces unnecessary and unwanted traffic, restricting how much information devices can observe.

**Isolating Sensitive Systems** ensures that critical devices are in separate VLANs with controlled access. This prevents attackers from easily reaching sensitive systems after compromising a less secure device.

### DHCP Snooping

**DHCP Snooping** designates ports as trusted or untrusted and blocks unauthorized devices on the network. A DHCP Snooping table is used to record valid MAC addresses as well as devices that are not allowed on the network. This prevents attackers from assigning malicious IP configurations that enable traffic interception.


## Five Common Internal LAN Threats

**ARP Spoofing** is when a device pretends to be another by sending false ARP replies, exploiting the fact that LAN devices accept ARP messages without verifying identity. This can redirect traffic or intercept sensitive data.

**MAC Flooding** occurs when an attacker floods a switch with fake MAC addresses, overloading its table. Switches trust MAC learning on each port by default, which can force the switch into a vulnerable “fail-open” mode.

**Rogue DHCP Server** is when an unauthorized device provides IP addresses to clients. LAN devices automatically accept DHCP offers, which can allow attackers to control network configuration, redirect traffic, or launch man-in-the-middle attacks.

**Unauthorized Plug-In Device** occurs when an unknown device connects to the network through an open port. Because LAN ports often allow devices to join without authentication, this can provide attackers with direct access to sensitive systems or introduce malware.

**Lateral Movement** is an attacker moving from one internal system to another within the LAN. Internal devices often trust each other by default, making it easier for attackers to escalate privileges and access sensitive data across the network.



## Risks Involving Flat LANs 

Flat LANs pose significant security risks because all devices share the same broadcast domain, allowing attackers to easily see, intercept, or manipulate traffic from any other device. Additionally, one compromised device can spread laterally across the network, since there is no segmentation to isolate various systems.

## Internal Trust 

Internal trust is the assumption that devices and users inside a network are safe and behave correctly without malicious intent. Its risk is that if this trust is misplaced, compromised devices or insider threats can freely access and exploit the network.

## Physical vs Technical Security

**Physical security** protects the tangible components of a network, such as servers, switches, and wiring, with locked doors, security guards, and cameras. **Technical security** protects the network and its data through software and hardware controls, such as firewalls, ACLs, VLANs, and encryption, preventing unauthorized access to the network.

---


# Technical & Security Development 

## VM-Based Evidence

TO BE COMPLETED ON TUESDAY

----

## Physical Security Controls for Network Devices and Physical Spaces

### Enterprise Physical Threats Analysis

In a pharmaceutical research facility, there could be several physical vulnerabilities that pose serious threats. Unrestricted access to research laboratories would allow unauthorized individuals into sensitive areas, leaving the company's intellectual property exposed and allowing for contamination. Drug storage areas are often inadequately secured, making controlled substances and experimental compounds vulnerable to theft or diversion. Poor separation between public, administrative, and research spaces increases the chance of people entering areas that they do not have the authority to be in. After-hours access may be weakly monitored, enabling potential tampering or removal of materials when there is less security. Critical environmental systems, such as cleanroom controls, lack sufficient protection, putting experiments and drugs that need to be climate-controlled at risk. Lastly, data centers are not always secured properly, meaning that the systems can be accessed easily.


### Physical Security Plan - Pharmaceutical Research Facility

A layered physical security strategy in a pharmaceutical research facility includes environmental controls, access control, surveillance, hardware security, and personnel procedures. Environmental systems maintain strict temperature, humidity, and air quality while using fire suppression to protect labs, experiments, and network equipment. Access is restricted through badges, biometrics, and zoning, ensuring only authorized personnel can enter labs, clean rooms, and server rooms. Surveillance cameras, motion detectors, alarms, and security personnel work to monitor all areas and prevent any unauthorized movement. Hardware is secured by using locks, badges, and port protection to prevent tampering with equipment and data. Personnel procedures include gated entry, visitor escorts, and regular staff trainings to reinforce security, reduce insider risk, and ensure compliance. By combining all of these security policies, research materials, sensitive data, and network infrastructure will be more secure. 

### Diagram: 
<img alt="Screenshot 2026-01-16 at 11 16 18 PM" src="https://github.com/user-attachments/assets/cc085847-1d32-4f8c-ab6c-2c239ccbf41f" />

**Key:**
* Grey areas - buildings
* Yellow outlines - monotered public areas
* Red outlines - high security area
* Bold red outline - very high security area
* Dark grey paths - secured walkways that restrict movement between rooms.


### Risk Justification and Priority Controls

In a pharmaceutical research environment, the highest priority physical controls are access control, environmental monitoring, and surveillance. Restricting entry to labs, clean rooms, and data centers with badges and biometrics ensures only authorized personnel have access to sensitive materials. Environmental monitoring and fire suppression prevent accidental or deliberate damage to samples and equipment, mitigating the risk of sabotage to servers, products, or research evidence. Surveillance, such as cameras and alarms, provides detection of unauthorized activity, reducing the likelihood and impact of theft and sabotage as well as regulatory violations. These physical controls also reinforce technical measures, such as network segmentation, access control lists, and monitoring systems, by limiting physical access to critical systems and enabling quick detection of incidents. These controls make up a layered defense that protects intellectual property, ensures data integrity, and maintains regulatory compliance.

---

## LAN Security Investigation

| Scenario Letter | Symptoms |  Hypothesis  |  Justification |
|-----------------|-----------------------|----------------------------------------|-------------------------------------------------------------|
|   A  |  Default gateway does not match router    |   There is an issue with the DHCP server   |     Connectivity issues and network behavior changes |
|       B       |   Switch CPU spikes and thousands of MACs appear on one port     |       MAC Flooding Attack    |        Multiple MACs show up on one port and switch CPU spikes   |
|    C     |       Receives network settings from an unknown DHCP source   |    Misconfigured Router  |    Unknown DHCP source and conectivity issues        |
|    D   |    New device appears inside the broadcast domain and communicates broadly  |      Administrative Issue       |  Communicate broadly and new devices appearing     |
|    E  |  A host reaches internal systems it should not access |Security Policy Bypass|   Fire walls and other encryptions are not working |

### Reflection: 

The MAC Flooding Attack was the easiest conclusion to come to and the one that the group felt most confident in initially. This is due to the straightforward and very evident symptoms regarding MAC Flooding Attacks. Scenario C was the most difficult to identify, as initially the group was not thinking about the router, but instead the rogue device. Talking over the initial conclusions with another group solidified both groups' answers, ensuring everyone was confident regarding the scenarios. General patterns include abnormal network behavior, detection after the attacks have occurred, and a lack of security where the attacks are occurring. 

---

# Testing, Observation & Risk Evaluation


## Appropriate Security Controls/Common Vulnerabilities Within Simple LAN

The photo below displays the output of the **ip addr** and **ip route** commands, which is information about the network interface and the route the data takes.

<img width="852" height="348" alt="ipaddrroute" src="https://github.com/user-attachments/assets/f3038865-9ef0-4078-9e8e-7a6356e57955" />


The **sudo tcpdump -i enp0s1 arp** shows the various ip addresses of devices on the network. This command displays the lack of a VLAN and how accessible this data is to attain.
<img width="1162" height="520" alt="sudotcpdump" src="https://github.com/user-attachments/assets/1449bc34-d13e-4308-a92b-66ac6cdbc2fa" />

The **sudo arping -c 5 -I enp0s1 10.12.17.123** command allows the first VM to be pinged from a different VM on the network, highlighting once again the unsegmented LAN. 
<img width="1380" height="514" alt="sudoarping" src="https://github.com/user-attachments/assets/663f2016-3222-4d67-a052-07408d0d6794" />

### Reflection: 

The ARP reveals the IP to MAC address mappings of other devices on the LAN. ARP assumes devices are trustworthy because it accepts replies without authentication and bases its trust on the idea that all devices operating on the idea that all devices connected to the network are trustworthy. This lack of authentication makes the ARP vulnerable to spoofing, as a rogue device can send a fake ARP reply to associate its own MAC address with another device's IP address. Additionally, this lab required bridged mode so the two VMs would be on the same layer but have different IP addresses. 

---


## LAN Attack Path Diagram - Unauthorized Plug-In Device

<img alt="Screenshot 2026-01-19 at 3 45 07 PM" src="https://github.com/user-attachments/assets/5c6028cf-f335-4d62-b2cd-ecad6c32ae51" />


### Reflection:

This attack succeeds due to the switch's trust in any device that is physically plugged in. This means that the switch treats all devices as legitimate endpoints that can communicate freely with other devices, send DHCP requests, and impact broadcast traffic. Due to the lack of security checks, physical access gives devices full access to the network, which allows the attacker to spoof MAC or ARP information and tamper with the local network. Port security would help mitigate the risk of this attack because it would restrict which MAC addresses are permitted on a switch port and block the port when unauthorized devices attempt to access it. If the port security was bypassed, VLAN segmentation would prevent the rogue device from communicating with restricted devices, DHCP snooping would prevent rogue DHCP responses anda stop attacks from progressing in the LAN.

---


# Professional Integration 

## [Switched LAN Security Controls Report](https://docs.google.com/document/d/e/2PACX-1vQnK0U0c5t3UXuoHlh1Vlx0YkpLQGElYG0Mjka2JinEu0iKzmfN7vlz6MFYnahnNF1-qFzcKMkvWVVW/pub)


 ---
