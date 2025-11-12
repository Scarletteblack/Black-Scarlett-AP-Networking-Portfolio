---
title: "Types of Networks & Connections and Devices"
last_modified_at: 2025-11-04T22:20:30-22:35:00

---

# Design and Planning

## Topography Activity
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





• Use different colors for cables, devices, and labels.
• Ensure text is legible and aligned.
• Organize each topology on its own section of the page.
• Your diagrams should look professional and technical, not rough sketches.


**Reflection**
A star topology would be the easiest to set up for a business because all devices connect to a central switch or hub. This makes it simple to add or remove devices and easy to manage. A mesh topology is the most reliable if a connection fails because every device is connected to multiple other devices. If one cable or connection fails, the data can still travel through another path. The most expensive topology is the mesh topology because every device is connected to every other device, requiring more cables and hardware than other topologies. I think our school uses a hybrid or star topology, because many computers in different rooms probably connect back to central switches and servers, making it easier to manage and repair. The physical layout of a topology affects speed and reliability because shorter and more direct connections allow data to travel faster, while more intricate layouts make it easier to avoid collisions and reduce delays.

---

| Topography Type | Description | Sketch |
| :------------------- | :----------: | ----------: |
| Star Topology |  • One central switch or hub in the middle • All computers connect to that central point • Example label: “Central Switch” in the middle with arrows to each “Computer" • Common use: Office networks and home Wi-Fi routers.|![startopology](https://github.com/user-attachments/assets/5fc69c1d-425a-489b-875a-5d6360d44894)|
| Bus Topography | • A single straight line (“backbone cable”) with all computers branching off • Add short perpendicular lines for each device • Common use: Early Ethernet networks (now outdated)| ![bus](https://github.com/user-attachments/assets/a3989fbb-b8a5-4be4-b035-fcddace16a5c) |
| Ring Topography |• Devices form a circle with connections between neighbors • Data travels one way (or both in dual-ring) •Common use: Some legacy fiber networks and token ring systems |![ring](https://github.com/user-attachments/assets/62981fbe-6765-48b2-8e76-baeba741365e)|
| Mesh Topography |• Every device connects to multiple others (use 4–5 devices for clarity) • Show redundancy — if one path breaks, another can still carry data • Common use: Data centers and IoT or wireless mesh networks | ![mesh](https://github.com/user-attachments/assets/6187b53c-c3c8-4697-89fd-387c2bbf66e8) |
| Hybrid Topography |• Combine two or more types (for example, multiple Star networks connected in a Bus layout) • Common use: Large organizations with multiple departments or floors | <img width="471" height="637" alt="Note Nov 6, 2025" src="https://github.com/user-attachments/assets/bb8ce3fc-47df-4d4a-aa51-94b84571fd17" />
 |

---

## Cable Constructing and Testing

### Making the Cable (T568B)

**T568B cables are more common in commercial installations**

Using the crimping tool to strip the wire: 
![strippedwire](https://github.com/user-attachments/assets/3fd808f0-dad8-46e7-ae12-5cdfae4916d1)

This is a photo of the cables after being split and separated from one another:
![splitandseparatedwires](https://github.com/user-attachments/assets/a0356ec8-bb84-4bfa-a99d-aaca4f8cf9ab)

This displays the wires straightened and ordered:
![orderedwires](https://github.com/user-attachments/assets/3f9fc3fc-18a1-496f-a963-d5c133e6af0a)
T568B wire order: White/Orange, Orange, White/Green, Blue, White/Blue, Green, White/Brown, Brown

Then the wires were inserted into the RJ45 connector:
![beforecrimpingb](https://github.com/user-attachments/assets/ade0de35-eef7-41ce-a80e-0078b8279284)

For ease, the wires were left long and inserted individually and then cut once all were in the correct order.

RJ45 connector after crimping: 
![finishedb](https://github.com/user-attachments/assets/f257a757-1258-4a47-8ae9-b6b9da5d9c15)

The same process is repeated for the other side of the cable; both finished sides of the cable are pictured below: 
![bothsides](https://github.com/user-attachments/assets/b5a5eaaa-c5b8-44e6-ab89-6925b1af86d9)

### Stripping Demonstration Video

### Testing the Cable
![workingpic](https://github.com/user-attachments/assets/f45be748-e0d1-4dd7-8a9e-c1d6d5942150)

### Cable Testing Demonstration

### T568A Cable 

**T568A cables perform basically the same electrically as the T568B and are commonly used in government and residential installations in the U.S**
The order for T568A cables is slightly different: White/Green, Green, White/Orange, Blue, White/Blue, Orange, White/Brown, Brown

### Comparison and Reflection

Below are the side-by-side labeled cables. On the left is the T568A and on the right is the T568B.

![comparingab](https://github.com/user-attachments/assets/0c8e6c90-6bb5-4618-82f6-fd54a0a3f8ad)
![labeledback](https://github.com/user-attachments/assets/ead2d765-9242-445c-87ae-77789954f828)
![labeledfront](https://github.com/user-attachments/assets/d0c86b44-e72c-49b5-8dc9-0189e667e158)

**Reflection**
The most challenging step in building the cable was inserting the wires into the RJ45 connector in the correct order. Ensuring that all of the wires are in the correct order is  important because if they are not, the signal won’t go to the right place and the cable will not work. This connects to the Physical Layer of the OSI Model because it is the layer responsible for all physical elements, such as cables. If a cable is made incorrectly and not tested, it would mess up the rest of the network and due to not testing the cable, it may seem like there is an issue elsewhere in the network. Labeling the cable and using tools like crimpers and testers mimics the real processes that people in the industry must go through to stay organized and make sure everything works correctly.

---

## OSI & TCP/IP — Layers 1 and 2
sudo eth<img width="723" height="127" alt="Screenshot 2025-11-11 at 1 27 56 PM" src="https://github.com/user-attachments/assets/4b462f49-aa73-4e66-b09d-57b9bdeb8543" />

<img width="424" height="329" alt="Screenshot 2025-11-11 at 1 29 12 PM" src="https://github.com/user-attachments/assets/b461a58a-8c8a-4af9-bd34-2802586bb524" />

<img width="722" height="268" alt="Screenshot 2025-11-11 at 1 33 29 PM" src="https://github.com/user-attachments/assets/5b24bde7-aa04-4419-a1d8-49f85bf71f1c" />
RX packets: 239846
TX packets: 35940
There were no errors.


<img width="457" height="326" alt="Screenshot 2025-11-11 at 1 39 01 PM" src="https://github.com/user-attachments/assets/55ba9454-89f0-49bd-802f-9ae00b48ba0e" />
* Speed (Mb/s): Unknown
* Duplex: Unknown
* Link detected: Yes

<img width="728" height="276" alt="Screenshot 2025-11-11 at 1 57 44 PM" src="https://github.com/user-attachments/assets/22a78311-d1fa-42d6-ab80-a005beb1a4bc" />
* MAC Address: 18:57:03.221977* Destination MAC Address: 1a:63:23:39:a4:2c
* Protocols used: (like ARP, IP, or ICMP)

## Building and Testing a Small Office / Home Office (SOHO) Network
### SOHO Network
<img width="1080" height="650" alt="Note Nov 12, 2025 (2)" src="https://github.com/user-attachments/assets/b0a6b4e3-3931-41a1-b7a1-fce588068960" />
