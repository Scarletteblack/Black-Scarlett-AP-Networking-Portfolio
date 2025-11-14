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

Internal and external IP addresses differ because the internal IP address belongs to your local network, while the external IP is the address the internet sees. The internal (private) IP address is used only within the home or virtual network, and the external (public) IP address is assigned by the ISP. A virtual machine uses NAT because it lets the VM access the internet through the host’s IP while staying secure and hidden behind it. Shared mode makes it easier to connect multiple VMs because it puts them on the same virtual network, giving each one its own private IP so they can communicate with each other while still sharing the host’s internet connection.

--- 
### Bridged Mode

In Bridged mode the **internal** IP address was: 10.32.1.32/23

<img width="727" height="286" alt="Screenshot 2025-11-05 at 10 27 23 AM" src="https://github.com/user-attachments/assets/00ec1032-0528-4c1c-a11e-1d5266cde0a0" />

**External** (public) IP address: 

<img width="1178" height="338" alt="shared-mode0  " src="https://github.com/user-attachments/assets/1bedb508-60c0-4cc4-9f2e-7c86d550285a" />

#### Reflection - Bridged Mode

When switched to Bridged mode, the internal IP address changes because the virtual machine receives its own IP directly from the same network as the physical computer. The external IP address remains the same, since both the VM and the host still access the internet through the same router. In Bridged mode, the VM behaves like a completely separate computer on the network rather than a device hidden behind another one. Organizations choose Bridged mode when they want virtual machines to function as independent systems—useful for servers, testing environments, or situations where other devices on the network need to reach the VM directly. However, Bridged mode can introduce security and management challenges because each VM becomes visible on the network, requires its own firewall rules, and increases the number of devices that must be monitored and protected.

---

### Shared Mode VS Bridged Mode

| Mode | Internal (Private) IP | External (Public) IP |
| :------------------- | :----------: | ----------: |
| Shared           | 192.168.64.2/24      | 173.95.44.210       |
| Bridged              |  10.32.1.32/23     |  173.95.44.210    |
| Notes              | Both private IP Addresses| Same |


Bridged mode made the virtual machine appear as its own device on the local network because it received an IP address directly from the network, just like a physical computer. Shared (NAT) mode provided a safer and more controlled environment by keeping the VM behind the host computer and isolating it from other devices. NAT helps manage limited IPv4 addresses by allowing many private devices to share a single public IP, while also improving security by hiding internal devices from the outside world. This experiment showed that data from a device first travels through the local network using a private IP, then passes through a router or host system before reaching the internet with a public IP. It also demonstrated that network modes change how visible a device is and how its traffic is routed.


Switching between Shared and Bridged mode changed the virtual machine’s IP addresses by giving it a private, isolated address in Shared (NAT) mode and a full, separate address in Bridged mode. This experiment shows that devices can either hide behind a single public IP or act as independent machines on a local network, depending on how they are connected. It also highlights how local networks use private IP addresses internally while sharing one public IP when reaching the internet. IT professionals choose different configurations because home networks value simplicity and safety, business networks often require full device visibility, and lab environments need flexibility for testing. For classroom use, Shared mode is generally the best because it is safer, easier to manage, and prevents students’ virtual machines from interfering with the wider network.

---

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
<img width="723" height="127" alt="Screenshot 2025-11-11 at 1 27 56 PM" src="https://github.com/user-attachments/assets/4b462f49-aa73-4e66-b09d-57b9bdeb8543" />

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

This small office network connects all devices through a central router (192.168.50.1), which manages IP addresses and internet access. The switch (192.168.50.3) distributes wired connections to the two Ubuntu VMs (192.168.50.10 and 192.168.50.11) and the NAS (192.168.50.3) for reliable, high-speed data transfer. The access point connects wirelessly to the router, allowing the phone (using DHCP) to join the network through Wi-Fi. This setup provides both wired and wireless access, ensuring that devices needing stable connections use cables, while mobile devices connect flexibly through Wi-Fi.

### Testing in Ubuntu

Computer A - in Ubuntu:

<img width="724" height="276" alt="image" src="https://github.com/user-attachments/assets/bbdb7946-a618-4f48-b6da-4c0f91fea123" />

Computer B - in MAC terminal: 

<img width="832" height="859" alt="0-3" src="https://github.com/user-attachments/assets/df828aba-7a99-4f69-8639-55bdcfd80e39" />

Computer A successful ping: 

<img width="720" height="326" alt="0-1" src="https://github.com/user-attachments/assets/9ef2ae7b-52cf-41a0-8dcf-a1775ac087fc" />

Computer B successful ping:

<img width="448" height="154" alt="0-2" src="https://github.com/user-attachments/assets/8efeca64-4a90-4e6b-9c1b-4748ad257b77" />

**Firewall**

<img width="501" height="162" alt="Screenshot 2025-11-14 at 8 20 49 AM" src="https://github.com/user-attachments/assets/4197996f-8c76-4229-a72c-d20e4bacd5c9" />

* Firewalls protect from malware

### Creating a new VM 

<img width="635" height="149" alt="Screenshot 2025-11-14 at 8 41 56 AM" src="https://github.com/user-attachments/assets/46120607-15c7-4e03-beac-34fef5e42bf2" />

<img width="587" height="333" alt="Screenshot 2025-11-14 at 8 48 21 AM" src="https://github.com/user-attachments/assets/5d2a5132-4b35-444e-b277-d1cf22753e87" />

<img width="560" height="463" alt="Screenshot 2025-11-14 at 8 51 13 AM" src="https://github.com/user-attachments/assets/85aa22a8-44be-479e-8de9-c2bbb977e5ee" />

The traceroute results show that data travels through several routers, or hops, before reaching its destination. Each hop represents a different device or network along the path, showing how data moves step-by-step across the internet

### Running a Simple Web Server

<img width="524" height="78" alt="Screenshot 2025-11-14 at 8 54 53 AM" src="https://github.com/user-attachments/assets/fc7862b0-b7b7-4756-9a86-c24c34427d24" />
<img width="562" height="280" alt="Image 11-14-25 at 8 55 AM" src="https://github.com/user-attachments/assets/5c947654-70c5-4651-a359-266a4037b582" />

One system transferring files to another, as seen above, using HTTP, illustrates how the Application Layer works.
