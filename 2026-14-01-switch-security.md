# Switch Security

## Common LAN Threats & Why Switches Are Vulnerable

Which device inside a LAN do you believe would be the easiest for an attacker to
compromise, and why?
• Does being “inside” the network make a device safer or more dangerous than being
outside the network?
• How much do you think a typical device can see or learn by default inside a
switched LAN?

### Scenario Assessment

| Scenario | Symptoms (summary) | Your Hypothesis (what you think is happening) | Your Justification (evidence and reasoning) |
|---------|--------------------|-----------------------------------------------|---------------------------------------------|
|    A     |      Several devices report connectivity/speed issues despite being connected to the switch. The default gateway is different from what was expected.              |                                               |                                             |
|    B    |     A switch begins to display increased CPU usage, resulting in the network performance becoming inconsistent. The switch logs reveal that hundreds of MAC addresses are appearing on a single switch port over a short window.                |                                               |                                             |
|    C    |          The switch is assigning IP addresses to devices but placing them in the wrong subnet. Some users report being unable to access the internet, while others experience DNS issues.           |                                               |                                             |
|    D    |        An unregistered device appears on the LAN and is communicating with other hosts. The device was never approved to be on the LAN, and logs show that activity began from a wall jack in a public, lightly monitored area.              |                                               |                                             |
|    E   |         A student workstation is recorded communicating with internal systems that should not be accessible to students. No firewall alerts were triggered, and traffic appears to be internal           |                                               |                                             |


### VM Evidence

<img width="1378" height="510" alt="arping" src="https://github.com/user-attachments/assets/9763e3a4-d3b9-41cd-ab91-7fcc789bcebe" />
<img width="650" height="310" alt="tcpdump" src="https://github.com/user-attachments/assets/90ab0051-0f8e-496c-a941-fde16b11276c" />


Written Reflection (2–3 sentences)
Respond to the following question:
How could an attacker misuse this information?
Your response should:
• Refer directly to what is visible in your screenshot(s)
• Explain why this information is valuable, not just what it shows

--- 

### Reflection

Which threat scenario from today felt the most realistic, and why?
• What surprised you about how much information a normal device can see inside a
switched LAN?


### From Observations to Decisions

#### Definitions


- Threat &rarr; any potential event, action, or circumstance—intentional or unintentional—that has the potential to cause harm to a network, system, or data
- Vulnerability &rarr; a flaw, weakness, or loophole in a system, application, network, or even its security procedures, which a threat actor (like a hacker) can exploit to gain unauthorized access, disrupt operations, or steal data
- Control &rarr; refers to managing network traffic, security, and resources, often through Access Control (who/what connects, Network Access Control - NAC), Controlled Access Protocols (how devices share the medium, avoiding collisions like Polling/Token Passing), and Network Control (regulating data flow for efficiency/reliability
- Prevent vs. Mitigate &rarr; Prevent: Actions taken to decrease the likelihood that a security incident or network disruption will occur, Mitigate: Actions taken to minimize the impact or reduce the damage of a security threat that has already occurred or cannot be fully prevented


#### Visualizing Switch Security with Packet Tracer

| Senario | Evidence | Explination |
|-----------------|------------------------------------|--------------------------------------------------------|
| A - Flat Network (No Security Controls |                                    | What this network allows by default? Why this design assumes trust between devices? How this could create security risk?                                               |
| B - VLAN Segmentation (Visual Separation)|                   |                                    |  How VLANs change what devices can see? Why VLANs reduce broadcast visibility? VLANs alone do not enforce full security?                                                |
| C - Port Security (Limiting Physical Access)|                                    | How port security relates to physical access? What type of risk it helps mitigate? What it cannot protect against on its own |
| D - Conceptual View of DHCP Snooping, DAI, and ACLs|                                    | Which devices should be trusted? Which devices should be restricted? Where should the switch enforce rules?      |


| VM Evidence |Vulnerability | Control | Why This Control
Mitigates Risk |
|---------|--------------------|----------------------------------------|---------------------------------------------|
|        |             |                                               |   

## Task C - Mini-Threat Simulation

The attacker already has access to the network after the teacher opens the phishing email while connected to school network. In this situation, the network traffic itself is most directly targetted.

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


