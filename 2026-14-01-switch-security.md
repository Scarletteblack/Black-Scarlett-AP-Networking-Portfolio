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
