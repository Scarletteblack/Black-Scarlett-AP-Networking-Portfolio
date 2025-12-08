# Why Can't These Two Computers Talk to Each Other?

## Planning and Design
Working in pairs, partners figured out why two computers connected directly with an Ethernet cable cannot communicate. Both computers are running Ubuntu virtual machines and are connected with a working Ethernet cable. The main layers that could have issues are the physical layer, data link layer, and the network layer. The most likely scenario is that there is an issue in the data link layer or the network layer. 

---

## Checking Layer 1 - The Physical Layer

The ethernet cable was plugged into both MACs and the connection was checked to be firm and secure. In each Ubuntu VM Terminal ip a was used to find the MAC address where it says link/ether <MAC address> by enp0s1. Then, looking next to the enp0s1 tag, the interface showed UP, meaning the ethernet cable allowed for a stable connection, the NICs and enabled and the Ubuntu VM is recognizing the connection. If the interface displayed DOWN, that would have indicated that the physical layer is not active. Because the issue is not physical, it means the issue is happening in the data link or network layer.

**Both Partners VMs:**

<img width="644" height="365" alt="516960731-66861367-47ca-45fa-a1b2-e18e679554ca" src="https://github.com/user-attachments/assets/72d1ea85-66c1-4ff5-bf5b-abcf909cfc36" />

IP of VM 1

<img width="639" height="356" alt="unnamed-11" src="https://github.com/user-attachments/assets/4d6e614b-eabc-45ec-9b8c-3fe514a171f3" />

IP of VM 2

---

## Checking Layer 2 -The Data Link Layer

The two VMs were on the same network in order to communicate directly; however, the two VMs have different MAC addresses. Using the ping command and inserting the other VM's IP, the reachability of the other MAC was tested. If the ping was successful and the packet was able to reach the other MAC, it would have shown the time it took the packet to travel between the two. However, the ping failed and both partners got the message Destination Host Unreachable. This is evident that Layer 2 cannot find the partner’s MAC address and thus cannot send any packets through the data link. 


**Both partners' VM pings**

<img width="1074" height="440" alt="unnamed" src="https://github.com/user-attachments/assets/7c679641-284c-4e2d-bc5e-ded8fc444c45" />

VM #1 ping unsuccessful 

<img width="641" height="236" alt="516961369-8b1cdc4c-8ea0-432d-80ac-67f4adfdc1ad" src="https://github.com/user-attachments/assets/1a99164a-f2de-40f8-921c-76bc390c0d52" />

VM #2 ping unsuccessful 

---

## Checking Layer 3 - Network Layer 

<img width="347" height="44" alt="Screenshot 2025-12-08 at 1 38 34 PM" src="https://github.com/user-attachments/assets/8af30c4d-9ccf-4472-ac63-dc1e5af91d83" />

IP 1

<img width="277" height="47" alt="Screenshot 2025-12-08 at 1 39 06 PM" src="https://github.com/user-attachments/assets/2e30d61c-3a94-4b9b-be85-819a525642ca" />

IP 2

Explanation Paragraph

Although both virtual machines show very similar IP addresses, they are not part of the same Layer 3 network. UTM assigns each VM to its own isolated host-only network, complete with a separate virtual switch and its own DHCP server. This makes the IPs appear related, but the machines are actually in different broadcast domains and cannot receive each other’s ARP messages. Since ARP cannot operate across two distinct virtual switches, the VMs are unable to communicate at Layer 3 despite having matching IP ranges. Therefore, Layer 3 connectivity is not possible in this setup.

## Making it Work




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
