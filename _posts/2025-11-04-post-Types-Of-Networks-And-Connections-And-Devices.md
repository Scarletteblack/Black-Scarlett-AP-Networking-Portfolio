---
title: "Types of Networks & Connections and Devices"
last_modified_at: 2025-11-04T22:20:30-22:35:00

---

## Design and Planning



### Shared Mode 
In Shared mode the **internal** IP address was: 192.168.64.2/24
<img width="719" height="356" alt="Image 11-5-25 at 10 25 AM" src="https://github.com/user-attachments/assets/3b97b973-2472-4cf0-bae1-aae3f429f0c6" />

**External** (public) IP address: 
<img width="1178" height="338" alt="shared-mode0  " src="https://github.com/user-attachments/assets/1bedb508-60c0-4cc4-9f2e-7c86d550285a" />

#### Reflection - Shared Mode
1. Are your internal and external IP addresses the same or different?
2. Which IP belongs to your local network?
3. Which IP belongs to the internet?
4. Why might a virtual machine use Network Address Translation (NAT) when
connecting to the internet?
5. How does Shared mode make it easier to connect multiple virtual machines on one
computer?
--- 
### Bridged Mode

In Bridged mode the **internal** IP address was: 10.32.1.32/23
<img width="727" height="286" alt="Screenshot 2025-11-05 at 10 27 23 AM" src="https://github.com/user-attachments/assets/00ec1032-0528-4c1c-a11e-1d5266cde0a0" />

**External** (public) IP address: 
<img width="1178" height="338" alt="shared-mode0  " src="https://github.com/user-attachments/assets/1bedb508-60c0-4cc4-9f2e-7c86d550285a" />

#### Reflection - Bridged Mode
1. How did your internal IP address change when you switched to Bridged mode?
2. Did your external IP address change or remain the same?
3. In Bridged mode, does your virtual machine act more like a separate computer or a
computer behind another device?
4. Why might an organization choose Bridged mode instead of Shared (NAT) mode?
5. What security or management challenges could come with using Bridged mode?
---

### Shared Mode VS Bridged Mode

| Mode | Internal (Private) IP | External (Public) IP |
| :------------------- | :----------: | ----------: |
| Shared           | 192.168.64.2/24      | 173.95.44.210       |
| Bridged              |  10.32.1.32/23     |  173.95.44.210    |
| Notes              | Both private IP Addresses| Same |


Write a short paragraph (5–7 sentences) beneath your table addressing the following:
• Which mode made your VM appear as its own device on the local network?
• Which mode provided a safer, more controlled environment?
• How does NAT help manage limited IPv4 addresses and improve security?
• What did you learn about how data travels from a device to the internet?

Step 1: Add Screenshots
Take screenshots of the following and insert them into your digital portfolio:
• The output of ip a in Shared (NAT) mode
• The output of ip a in Bridged mode
• The WhatIsMyIPAddress.com page results for both modes
Step 2: Reflection Writing
Write a short reflection (1 paragraph, 5–8 sentences) below your screenshots that answers these:
• How did your IP addresses change between Shared and Bridged mode?
• What did this experiment teach you about how local and public networks communicate?
• Why might IT professionals use different network configurations for home, business, or
lab environments?
• Which mode do you think is best for classroom use, and why?

---

**Analogy**
Imagine a group of friends passing notes in a classroom. The way they choose to pass the notes
— in a circle, in a line, or everyone handing notes to one central person — represents different
network topologies. Each method affects how quickly messages travel, how easy it is to add
more friends, and what happens if someone stops passing notes.

How Devices Connect in a Network
Every network includes devices that either send, receive, or direct data. Here’s how they connect
and communicate:
• End Devices: These are the computers, smartphones, printers, and other tools people use.
They send and receive data.
• Networking Devices: These control or manage traffic between devices.
o Switch: Connects multiple devices on the same local network (like in a classroom
or office).
o Router: Connects different networks (like your home network to the internet).
o Access Point: Allows wireless devices to connect using Wi-Fi.
• Cables or Wireless Connections: The “roads” that data travels along.
o Examples include Ethernet cables, fiber optic cables, or radio waves (for Wi-Fi).



Part 1: Digital Drawing Activity
Instructions:
1. Create one labeled drawing for each topology below.
Each drawing should include:
• 3 computers or laptops, 1 networking device(servers, routers, or access point) (use
simple icons or shapes) and 1 server printer or IoT device (for example, a smart
TV, NAS, or phone).
• Lines showing how devices are connected.
• A label naming each device type and the topology name.
• Add the drawings to the right-hand column on the next two pages. You will then
add the screenshots to your digital portfolio. Neatness and Clarity

• Use different colors for cables, devices, and labels.
• Ensure text is legible and aligned.
• Organize each topology on its own section of the page.
• Your diagrams should look professional and technical, not rough sketches.
Digital Portfolio Submission
1. Take screenshots of each completed topology drawing. Do not just take a picture of
your entire table—each drawing needs to have its own screenshot.
2. Upload the screenshots to your digital portfolio under Lesson 2: Network Topologies.
3. Title each image clearly (e.g., Star Topology, Bus Topology, etc.).

4. Below your images, write a well-written reflection paragraph that answers all
questions below.
Reflection Paragraph (on digital portfolio)
Write one complete, well-structured paragraph that answers the following:
1. Which topology would be easiest to set up for a small business, and why?
2. Which topology would be the most reliable if one connection fails?
3. Which topology would be most expensive to implement, and why?
4. Which topology do you think your school uses? Provide reasoning.
5. How does the physical layout of a topology affect speed and reliability?


| Topography Type | Description | Sketch |
| :------------------- | :----------: | ----------: |
| Star Topology |  • One central switch or hub in the middle • All computers connect to that central point • Example label: “Central Switch” in the middle with arrows to each “Computer" • Common use: Office networks and home Wi-Fi routers.|        |
| Bus Topography | • A single straight line (“backbone cable”) with all computers branching off • Add short perpendicular lines for each device • Common use: Early Ethernet networks (now outdated)|   |
| Ring Topography |• Devices form a circle with connections between neighbors • Data travels one way (or both in dual-ring) •Common use: Some legacy fiber networks and token ring systems |  |
| Mesh Topography |• Every device connects to multiple others (use 4–5 devices for clarity) • Show redundancy — if one path breaks, another can still carry data • Common use: Data centers and IoT or wireless mesh networks |  |
| Hybrid Topography |• Combine two or more types (for example, multiple Star networks connected in a Bus layout) • Common use: Large organizations with multiple departments or floors |  |

