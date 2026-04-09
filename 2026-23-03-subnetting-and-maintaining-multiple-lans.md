# Design and Planning

<img width="1376" height="360" alt="image" src="https://github.com/user-attachments/assets/7bbbe379-0c33-467b-8098-c6eb19653e16" />
* First number of the IPv4 must be the same

<img width="1310" height="370" alt="image" src="https://github.com/user-attachments/assets/f8d02c61-e61e-4b0c-b2e9-80ffb3f0873a" />
* First two sets of numbers in the IPv4 should be the same

<img width="1310" height="315" alt="image" src="https://github.com/user-attachments/assets/601e4c19-150e-458d-89bc-b9e738afd8c7" />
* First three numbers must match and the last must fall in the same range: 210.58.24.__

<img width="1310" height="187" alt="image" src="https://github.com/user-attachments/assets/2b8228ee-debb-40c4-80ab-08d7bb02f0ad" />
* Must all start with 1s in binary 

<img width="1310" height="244" alt="image" src="https://github.com/user-attachments/assets/6b5b9d66-dadc-487c-b682-39438067a1cb" />
* Their binary form is such that there is an uninterrupted string of 1s only at the beginning of the string

---

**PC0 &rarr; PC1**
<img width="285" height="177" alt="Screenshot 2026-03-26 at 8 23 47 AM" src="https://github.com/user-attachments/assets/39dbf787-524f-4fb6-a4b5-a43b759fbfe2" />

**PC0 &rarr; PC2**
<img width="310" height="169" alt="Screenshot 2026-03-26 at 8 25 08 AM" src="https://github.com/user-attachments/assets/6921fd47-d032-4fdb-8d02-54032145fa72" />

- PC0 to PC1 was sucsessful while PC0 to PC2 failed.


After changing the subnet mask of PC2 to 255.255.0.0 the ping from PC0 to PC2 still failed:

<img width="341" height="178" alt="Screenshot 2026-03-26 at 8 27 29 AM" src="https://github.com/user-attachments/assets/7923be78-8ddc-4dc4-8fec-7561b28d755b" />

#### Scenario A:

**PC0 &rarr; PC1**

<img width="275" height="158" alt="Screenshot 2026-03-26 at 8 31 59 AM" src="https://github.com/user-attachments/assets/1c1cf133-8c54-4839-b983-feca73658c31" />


**PC0 &rarr; PC2**

<img width="312" height="155" alt="Screenshot 2026-03-26 at 8 32 57 AM" src="https://github.com/user-attachments/assets/64f8c596-5023-4e54-a524-1c7bc0feb1f6" />

**All pings were successful**

#### Scenario B:

Both PCs are on the same network. The first two parts of the subnet mask are the same meaning they are on the same network. 

<img width="642" height="197" alt="Screenshot 2026-03-26 at 8 36 17 AM" src="https://github.com/user-attachments/assets/5cb52ca6-3807-4ae1-bb43-c1f0b13d66d4" />

<img width="631" height="187" alt="Screenshot 2026-03-26 at 8 37 10 AM" src="https://github.com/user-attachments/assets/6e76a654-883a-4324-977f-b8296451d0b3" />

#### Scenario C:

Similar but not the same: 

<img width="638" height="189" alt="Screenshot 2026-03-26 at 8 41 24 AM" src="https://github.com/user-attachments/assets/d070dd9e-5621-4729-a91c-e955aec029a2" />

<img width="637" height="193" alt="Screenshot 2026-03-26 at 8 42 19 AM" src="https://github.com/user-attachments/assets/62585d23-46be-46a4-af16-bc2512757784" />

A device determines if another device is on the same network by using its subnet mask to compare the network portion of both IP addresses. If they match, the devices are on the same network. Two IPs can look similar but be on different networks, such as 192.168.1.10 and 192.168.1.130 with a subnet mask of 255.255.255.192, which separates them into different ranges. Two IPs can look different but be on the same network, like 10.0.1.5 and 10.0.2.8 with a 255.255.0.0 mask, which groups them together. A router is needed when devices are on different networks because it directs data between those networks and ensures it reaches the correct destination.

---

# Tecnical Development


Scenario B: School Network
Designing a network for a school with two different user groups:
• Teachers (mix of wired desktops and wireless laptops)
• Students (primarily wireless laptops)
• Access to shared files
• Internet access

<img width="728" height="521" alt="Screenshot 2026-03-30 at 10 23 10 AM" src="https://github.com/user-attachments/assets/60c5b59f-18fa-4fee-953d-6e14e5f50dc7" />

The network is designed using a router, switch, access point, server, and multiple end point devices. The switch connects the office PCs and access point, allowing reliable and high-speed communication within the local network, while the router is used to connect different networks and manage traffic between them, including access to the server. A dedicated server is included to support a client-server model, which centralizes file storage and management, improving security and making it easier to control access compared to a peer-to-peer setup. Wired connections are used for the office PCs and server to provide stable, fast, and consistent performance for critical tasks, while wireless connectivity is provided through the access point for the laptop to allow mobility and convenience without needing physical cables. 

<img width="567" height="384" alt="Screenshot 2026-03-30 at 10 31 47 AM" src="https://github.com/user-attachments/assets/0a24e147-5f9d-4822-a766-d6bab741884b" />

--- 

Set ups with two LANs:

<img width="667" height="361" alt="Screenshot 2026-03-30 at 10 43 03 AM" src="https://github.com/user-attachments/assets/318adf77-12d3-4fad-96ab-90e84b2627bc" />

Router after configuring interfaces: 

<img width="316" height="102" alt="Screenshot 2026-03-30 at 10 48 59 AM" src="https://github.com/user-attachments/assets/22578c03-afa6-486f-9fb9-10a4f153e579" />

<img width="343" height="98" alt="Screenshot 2026-03-30 at 10 49 15 AM" src="https://github.com/user-attachments/assets/af792bed-1be2-4440-8d4e-742c95710bf8" />

PC in LAN1:

<img width="635" height="191" alt="Screenshot 2026-03-30 at 10 58 16 AM" src="https://github.com/user-attachments/assets/79727a0c-2fb0-4b11-b56d-c9aa5b2af3e6" />

PC in LAN2:

<img width="643" height="197" alt="Screenshot 2026-03-30 at 10 57 42 AM" src="https://github.com/user-attachments/assets/e15c7ee3-e55f-4afc-bec7-041df0486392" />

# When Networks Break: Diagnosing and Fixing Problems

Initial set up: 

<img width="774" height="420" alt="Screenshot 2026-03-31 at 12 24 22 PM" src="https://github.com/user-attachments/assets/fa246712-67d2-4568-a517-5f5a1e00e0f0" />

As seen above, the connection between Router 7 and Switch 1 fails. 

Failed ping between Switch 1 and Router 7
<img width="347" height="76" alt="Screenshot 2026-03-31 at 12 43 48 PM" src="https://github.com/user-attachments/assets/c64bfbd1-1398-4aa2-b9a9-b1be0e9fc0a5" />

On Router 7, the Port Status is not checked ON. 
<img width="501" height="407" alt="Screenshot 2026-03-31 at 12 41 03 PM" src="https://github.com/user-attachments/assets/41d997f5-0933-4e4d-a8bd-bd505a6e742e" />


After turning on the Port: 

<img width="507" height="407" alt="Screenshot 2026-03-31 at 12 45 14 PM" src="https://github.com/user-attachments/assets/6ee72dbf-9e80-4a6c-bf42-724b3eeb8650" />


<img width="769" height="431" alt="Screenshot 2026-03-31 at 12 45 37 PM" src="https://github.com/user-attachments/assets/a6b85916-3680-4fa9-80a8-7d9e43bb873a" />

Successful Ping

<img width="278" height="140" alt="Screenshot 2026-03-31 at 12 48 11 PM" src="https://github.com/user-attachments/assets/bfd5b474-fcff-4c50-b9cd-d80bfac2792b" />
