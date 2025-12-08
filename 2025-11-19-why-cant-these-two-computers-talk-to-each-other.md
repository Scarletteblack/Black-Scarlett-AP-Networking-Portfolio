# Why Can't These Two Computers Talk to Each Other?

## Planning and Design
Working in pairs, partners figured out why two computers connected directly with an Ethernet cable cannot communicate. Both computers are running Ubuntu virtual machines and are connected with a working Ethernet cable. The main layers that could have issues are the physical layer, data link layer, and the network layer. The most likely scenario is that there is an issue in the data link layer or the network layer. 

---

## Checking Layer 1 - The Physical Layer

The ethernet cable was plugged into both MACs and the connection was checked to be firm and secure. In each Ubuntu VM Terminal **ip a** was used to find the MAC address where it says **link/ether <MAC address>** by **enp0s1**. Then, looking next to the enp0s1 tag, the interface showed UP, meaning the ethernet cable allowed for a stable connection, the NICs and enabled and the Ubuntu VM is recognizing the connection. If the interface displayed DOWN, that would have indicated that the physical layer is not active. Because the issue is not physical, it means the issue is happening in the data link or network layer.

**Both Partners VMs:**

<img width="644" height="365" alt="516960731-66861367-47ca-45fa-a1b2-e18e679554ca" src="https://github.com/user-attachments/assets/72d1ea85-66c1-4ff5-bf5b-abcf909cfc36" />
<img width="639" height="356" alt="unnamed-11" src="https://github.com/user-attachments/assets/4d6e614b-eabc-45ec-9b8c-3fe514a171f3" />


---

## Checking  Layer 2 -The Data Link Layer

The two VMs were on the same network in order to communicate directly; however, the two VMs have different MAC addresses. Using the **ping** command and inserting the other VM's IP, the reachability of the other MAC was tested. If the ping was successful and the packet was able to reach the other MAC, it would have shown the time it took the packet to travel between the two. However, the ping failed and both partners got the message **Destination Host Unreachable**. This is evident that Layer 2 cannot find the partner’s MAC address and thus cannot send any packets through the data link. 


**Both partners' VM pings**

<img width="1074" height="440" alt="unnamed" src="https://github.com/user-attachments/assets/7c679641-284c-4e2d-bc5e-ded8fc444c45" />

VM #1 ping unsuccessful 

<img width="641" height="236" alt="516961369-8b1cdc4c-8ea0-432d-80ac-67f4adfdc1ad" src="https://github.com/user-attachments/assets/1a99164a-f2de-40f8-921c-76bc390c0d52" />

VM #2 ping unsuccessful 

---

## Network Layer Check (Layer 3: IP Addressing)
Now you must determine whether the issue comes from IP configuration.
Direct connections only work if:
Both computers are on the same subnet, for example:
• Computer A: 192.168.10.2/24
• Computer B: 192.168.10.3/24
BUT on virtual machines in UTM, you will likely see something like:
192.168.64.2
on both machines, which looks the same—but they are NOT on the same network.
They are in two separate private host-only networks created automatically by UTM.

That means:
• They look like they share a subnet
• But they are actually behind different invisible switches, so they cannot see each other.
This is the exact failure scenario.
Task
1. On each VM, run:
ip a
2. Compare the IPs.
3. Answer:
• Are the IPs identical?
• If so, what does that suggest?
• Are the VMs actually on the same network even if the IPs match?

(Hint: The answer is no. You should understand the reasoning.)
Digital Portfolio Evidence #3
Insert both IP screenshots and write a paragraph explaining why Layer 3 addressing cannot
work under this configuration.
<img width="158" height="16" alt="Screenshot 2025-11-18 at 3 14 03 PM" src="https://github.com/user-attachments/assets/84762ef3-c0d0-4fde-b974-22970c2370e8" />
<img width="168" height="17" alt="unnamed" src="https://github.com/user-attachments/assets/3c277a77-2c7e-4b94-abf0-0b656ad3247f" />

Explanation Paragraph

Even though both virtual machines appear to have almost identical IP addresses (for example, both showing 192.168.64.x), they are not on the same actual Layer 3 network. UTM automatically places each VM into its own isolated host-only virtual network, each with its own virtual switch and its own DHCP service. This means the IPs may look similar, but the two machines are actually on different broadcast domains and cannot see each other’s ARP requests. Because ARP cannot succeed across two separate virtual switches, Layer 3 communication is impossible, even though the IP addresses look compatible. Therefore, Layer 3 addressing fails under this configuration.

## PART 4 — Test Ping Again (Confirming Failure)
Run:
ping <partner_IP>
Record the result.
You will almost certainly get:
Destination Host Unreachable
Explain why this happens in terms of OSI Layers.
Digital Portfolio Evidence #4
Screenshot your ping failure
AND
Write 2–3 sentences describing which OSI layer is responsible.
<img width="520" height="199" alt="Screenshot 2025-11-18 at 3 17 49 PM" src="https://github.com/user-attachments/assets/6260e93c-87d3-46ca-8b84-a93ee8a825e8" />

Written Explanation 

The ping fails because Layer 2 cannot resolve the partner VM’s MAC address across two separate host-only virtual networks. Without MAC address resolution, Layer 3 cannot deliver IP packets, resulting in a “Destination Host Unreachable” message. Although the physical link is active, communication breaks down at Layer 2 and Layer 3 due to network isolation created by the virtualization environment.


## HOMEWORK PART 5 — Final Reflection Paragraph
Using what you learned about:
• Layer 1 (physical link)
• Layer 2 (MAC addressing & broadcast domain)
• Layer 3 (IP networks, subnets)
• Virtual networking inside UTM
Write a well-structured reflection paragraph answering:
1. Why couldn’t the two computers communicate even though they were connected with a
working Ethernet cable?
2. Which OSI layer(s) caused the failure?
3. Why does UTM prevent two VMs from communicating directly in Host-Only mode?
4. What configuration change would allow communication between the two computers?
5. In a real SOHO network, how do routers and switches prevent similar issues?

Final Reflection Paragraph

Even though the two computers were connected by a working Ethernet cable, they still could not communicate because UTM placed each VM into a different virtual Layer 2 broadcast domain and a separate Layer 3 network—even though the IP addresses looked similar. The failure occurred mainly at Layer 2 (MAC discovery/ARP) and Layer 3 (separate IP networks/subnets) because ARP packets never reached the other machine’s virtual switch. UTM’s Host-Only mode isolates VMs for security, so they cannot talk directly unless they are explicitly configured to share the same virtual network adapter. To allow communication, both VMs would need to be placed on the same bridged adapter or the same internal network so they share the same Layer 2 segment. In a real SOHO network, switches keep devices in the same broadcast domain while routers properly route traffic between different Layer 3 networks, preventing this kind of accidental isolation.
