# Why Can't These Two Computers Talk to Each Other?

## Planning and Design
Working in pairs, partners figured out why two computers connected directly with an Ethernet cable cannot communicate. Both computers are running Ubuntu virtual machines and are connected with a working Ethernet cable. The main layers that could have issues are the physical layer, data link layer, and the network layer. The most likely scenario is that there is an issue in the data link layer or the network layer. 





## Checking Layer 1 - The Physical Layer

The ethernet cable was plugged into both MACs and the connection checked to be firm and secure. In each Ubuntu VM Terminal **ip a** was used to find the MAC address where it says **link/ether <MAC address>** by **enp0s1**

If the interface shows state DOWN, that means Layer 1 (physical) is not active.

Both Partners VMs: 


Both partners' VMs displayed UP by the 

At Layer 1, both Ethernet interfaces show state UP, which confirms that the physical link between the machines is active. This means the Ethernet cable is functioning, the NICs are enabled, and Ubuntu recognizes a valid electrical connection. Since the physical layer is operational, the communication problem must be occurring at Layer 2 or Layer 3.

## PART 2 — Data Link Layer Check (Layer 2)
To communicate directly, both VMs must be on the same Layer 2 network.
1. Compare the MAC addresses on each VM:
• They should be different.
• If identical: the VMs are using duplicated virtual NICs → communication will
fail.

2. Try to ping each other using MAC broadcast behavior:
• Find your partner’s IP address (you will fix this in the next part).
• Try:
ping <partner_IP>

3. If you get:
Destination Host Unreachable
that usually means Layer 2 cannot find the partner’s MAC address.
Digital Portfolio Evidence #2
Screenshot your ping attempt AND write one sentence explaining what Layer 2 behavior you
observed.
<img width="638" height="235" alt="Screenshot 2025-11-18 at 3 12 40 PM" src="https://github.com/user-attachments/assets/1e9b43e5-49cc-4362-9a99-7ea6c97905f4" />

Explanation 

The ping resulted in “Destination Host Unreachable,” which shows that Layer 2 was unable to discover the partner computer’s MAC address and therefore could not forward any frames across the link.

## PART 3 — Network Layer Check (Layer 3: IP Addressing)
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
