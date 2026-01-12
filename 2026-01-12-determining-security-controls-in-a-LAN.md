# Determining Security Controls In A LAN

## Common Security Controls in a LAN
### LAN Threat Scenario Rotation
| Scenario Letter | Symptoms (summary) | Your Hypothesis (what’s happening) | Your Justification (why you think that,<br>your evidence) |
|-----------------|-----------------------|----------------------------------------|-------------------------------------------------------------|
|   A |                       |                                        |                                                             |
|                 |                       |                                        |                                                             |
|                 |                       |                                        |                                                             |


---

## Appropriate Security Controls/Common Vulnerabilities Within Simple LAN
### Linux:
<img width="852" height="348" alt="ipaddrroute" src="https://github.com/user-attachments/assets/f3038865-9ef0-4078-9e8e-7a6356e57955" />
<img width="1162" height="520" alt="sudotcpdump" src="https://github.com/user-attachments/assets/1449bc34-d13e-4308-a92b-66ac6cdbc2fa" />

### Ubuntu:
<img width="1380" height="514" alt="sudoarping" src="https://github.com/user-attachments/assets/663f2016-3222-4d67-a052-07408d0d6794" />

### Reflection: 

1. What information does ARP reveal about devices on a LAN?
2. Why does ARP assume devices are trustworthy?
3. How does this make ARP vulnerable to spoofing?
4. Why was Bridged mode required for this lab to work?
5. Include evidence from commands used

### LAN Attack Path Diagram (Homework) 

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

## Physical Security Controls for Network Devices and Physical Spaces

### Enterprise Physical Threats Analysis

- Six physical vulnerabilities relevant to a pharmaceutical research environment. Each vulnerability must be written as a clear weakness, not a solution.
- Each vulnerability should include: What the vulnerability is, Where it exists in the facility, Why it presents serious risk in this industry

### Physical Security Plan - Pharmaceutical Research Facility

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


### Diagram: 
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

### Risk Justification and Priority Controls

Write 1–2 paragraphs explaining:
• Which physical controls are the highest priority and why
• How these controls reduce the likelihood and impact of:
o Theft
o Sabotage
o Data compromise
o Regulatory violations
• How physical security supports technical controls such as:
o Network segmentation
o Access control lists
o Monitoring systems

Write this as if addressing executive leadership at the company.

---



