# Design and Planning  

**Ubuntu**

**IP Information**  
<img width="721" height="288" alt="Screenshot 2026-02-24 at 9 22 23 AM" src="https://github.com/user-attachments/assets/52b248ae-7f1d-492f-a630-05d08f0fb190" />

The screenshot above displays the Ubuntu virtual machine’s assigned IPv4 address, subnet mask, and interface configuration. The address shown belongs to one of the RFC1918 private ranges, indicating operation within an internal network rather than direct public internet exposure.

<img width="701" height="132" alt="Screenshot 2026-02-24 at 9 22 38 AM" src="https://github.com/user-attachments/assets/08b2d66d-cb3e-4abf-b0ef-138685d9e8ed" />

This image confirms the active interface and network configuration. The assigned address and default gateway determine how outbound traffic exits the local subnet.

<img width="276" height="37" alt="Screenshot 2026-02-24 at 9 24 12 AM" src="https://github.com/user-attachments/assets/ec5c7b0b-bdd3-4d73-91ff-2d39f8c3d346" />

The routing information identifies the gateway responsible for forwarding traffic outside the local network.

---

## **Linux**

**IP Information**  
<img width="445" height="160" alt="Screenshot 2026-02-24 at 9 22 59 AM" src="https://github.com/user-attachments/assets/2a37f484-d018-48ca-a5c7-ecfdfcf91199" />

This screenshot displays the Linux system’s private IPv4 configuration and confirms Layer 3 addressing within the LAN.

<img width="264" height="87" alt="Screenshot 2026-02-24 at 9 27 23 AM" src="https://github.com/user-attachments/assets/6f195cf5-cf7e-4cd4-b735-285a75a56b84" />

The routing output identifies the default route and interface used to reach external networks.

---

# Tecnical Development  

<img width="283" height="94" alt="Screenshot 2026-02-24 at 9 28 34 AM" src="https://github.com/user-attachments/assets/c00454c8-5c2b-4738-8cdd-abf8c5c9e861" />

<img width="275" height="97" alt="Screenshot 2026-02-24 at 9 29 11 AM" src="https://github.com/user-attachments/assets/d7b78bc2-917d-4ec6-9024-fa4d57da6dff" />

The configuration confirms successful internal communication between devices on the same subnet. When devices share a network ID, traffic remains at Layer 2 and does not require routing.

---

## WHO CAN SEE YOU  

### The purpose of private IPv4 addresses  
Private IPv4 addresses allow internal communication within a LAN without consuming globally unique address space.

### The purpose of public IPv4 addresses  
Public IPv4 addresses uniquely identify networks on the global internet and are routable across ISP and backbone infrastructure.

### Why a device can appear to have two different IP addresses  
A device may have a private internal address and share a translated public address through Network Address Translation (NAT).

### What problem private addressing solves  
Private addressing conserves limited public IPv4 space and allows millions of internal networks to reuse the same address ranges.

### Why this matters when building a WAN  
WAN design requires careful planning of address translation, routing boundaries, and public visibility to ensure scalability and security.

![Untitled design](https://github.com/user-attachments/assets/68e65781-dbbf-4a7a-ad0e-e27375851860)

---

### RFC1918 Address Ranges  

- 10.0.0.0 - 10.255.255.255  
- 172.16.0.0 - 172.31.255.255  
- 192.168.0.0 - 192.168.255.255  

<img width="347" height="42" alt="Screenshot 2026-02-25 at 10 27 23 AM" src="https://github.com/user-attachments/assets/b3a8b280-10ef-4cae-a5e9-0ea581950c13" />

<img width="614" height="174" alt="Screenshot 2026-02-25 at 10 42 55 AM" src="https://github.com/user-attachments/assets/9d7ab59a-ab65-46de-810b-3b0daffa841d" />

These screenshots demonstrate public IP visibility from an external lookup service, contrasting internal private addressing.

---

## Partner Ping  

1. Devices behind the same router typically share the same public IP due to NAT.  
2. Multiple devices appear to share one public IP because NAT translates many private addresses into a single public address for outbound traffic.  
3. If pinging a partner’s public IP fails, firewall rules or ISP filtering may block ICMP responses.  
4. Failure usually indicates filtering rather than nonexistence of the address.

---

### Private Addressing and WAN Design  

1. Private IPv4 addresses are reused because they are not globally routed and can safely exist in isolated networks.  
2. They are not routed publicly to prevent address conflicts across the internet.  
3. If every internal device required its own public IP, IPv4 exhaustion would accelerate dramatically.  
4. Businesses typically use one public IP with many private devices behind NAT to conserve address space.  
5. WAN design must account for NAT boundaries and routing domains.

---

### VLAN and NAT Considerations  

- Internal VLAN IP addresses are translated at the router before leaving the LAN.  
- Segmentation does not eliminate public addressing; it increases reliance on controlled translation.  
- NAT becomes critical for secure and scalable WAN connectivity.

---

### Key Concepts  

- Private IPv4 addresses are essential for scalability.  
- Public IPv4 addresses are required for global routing.  
- One device can appear to have two identities due to NAT translation at Layer 3 boundaries.

---

# Testing and Evaluation  

<img width="694" height="168" alt="Screenshot 2026-02-26 at 12 27 46 PM" src="https://github.com/user-attachments/assets/9b423092-e369-4594-bdb3-fd5c33d826e6" />

<img width="460" height="223" alt="Screenshot 2026-02-26 at 12 41 19 PM" src="https://github.com/user-attachments/assets/8ec434c1-dc7d-4f67-ae61-567441e5c0ae" />

<img width="712" height="194" alt="Screenshot 2026-02-26 at 12 41 57 PM" src="https://github.com/user-attachments/assets/eb5f1481-1c10-416a-acb1-f63f2e5880d0" />

---

<img width="1150" height="591" alt="Screenshot 2026-02-26 at 12 50 45 PM" src="https://github.com/user-attachments/assets/3f2abfdc-fec0-497a-9bde-8eb5b25e7ed7" />

<img width="1073" height="614" alt="Screenshot 2026-02-26 at 12 51 17 PM" src="https://github.com/user-attachments/assets/e91d27d1-5d83-4f84-a0e8-854f4865066a" />

---

<img width="1060" height="575" alt="Screenshot 2026-02-26 at 12 49 47 PM" src="https://github.com/user-attachments/assets/56514b8b-7781-4e51-b52a-18b80baa1ada" />

<img width="1188" height="593" alt="Screenshot 2026-02-26 at 12 48 09 PM" src="https://github.com/user-attachments/assets/d77809ae-5b28-4027-ac82-6941f64d6ce8" />

<img width="1116" height="598" alt="Screenshot 2026-02-26 at 12 49 07 PM" src="https://github.com/user-attachments/assets/40af0a37-0763-43cc-a2a0-77f13c8f7996" />

---

## Layer 2 vs Layer 3 Behavior  

1. Switches never modify IP addresses because they operate at Layer 2 and forward frames based on MAC addresses only.  
2. Routers must modify the MAC address because each hop requires a new Layer 2 frame header.  
3. The source IP remains the same from PC0 to PC1 because IP addresses identify end hosts unless NAT changes them.  
4. The “next hop” refers to the immediate router interface where the packet is forwarded according to the routing table.  
5. The default gateway is necessary to forward traffic destined for networks outside the local subnet.

---

### Communication Failure  

- Communication breaks when no routing entry exists for the destination network.  
- Switches cannot solve this because they lack Layer 3 awareness.  
- The router performs path determination and inter-network forwarding.

---

# IPROUTE SS  

## Other VM  

- Traffic goes directly if on the same subnet.  
- The first hop is the destination device.  
- One hop is expected.  
- Routing is not required within the same LAN.

## 8.8.8.8  

- Traffic goes through the gateway.  
- The first hop is the default gateway shown in the routing table screenshot.  
- Multiple hops are expected due to ISP and backbone traversal.

## google.com  

- Traffic goes through the gateway.  
- The first hop matches the routing-table default route.  
- Hop count varies depending on ISP routing decisions.

---

# Running Traceroute  

## 8.8.8.8  

<img width="584" height="218" alt="Screenshot 2026-03-02 at 9 53 42 AM" src="https://github.com/user-attachments/assets/6ecd61a6-fcf4-4b7b-8a58-db7973dd8809" />

Initial timeouts (`***`) indicate no ICMP response within the given TTL.

<img width="726" height="347" alt="Screenshot 2026-03-02 at 10 04 12 AM" src="https://github.com/user-attachments/assets/ef71b327-c850-4159-a01c-a2a4d7b5f3e6" />

After reboot, traceroute reveals multiple hops through private and public infrastructure.

---

<img width="734" height="599" alt="Screenshot 2026-03-02 at 9 58 10 AM" src="https://github.com/user-attachments/assets/3fe0093f-ca19-4e62-a997-6503ed22ba03" />

- The first hop is consistent and represents the local gateway.  
- Total hop count may differ depending on routing decisions.  
- Paths diverge once traffic leaves ISP infrastructure.

---

## Analysis – 8.8.8.8 (First 5 Hops)  

1. First hop: Private IP — likely the LAN gateway.  
2. Second hop: Private or ISP edge router.  
3–5: Public IPs — ISP aggregation and backbone routers.  

Private IPs appear early in the path because traffic originates inside the LAN before NAT translation.

---

# Validate with Routing Table  

<img width="558" height="58" alt="Screenshot 2026-03-02 at 10 14 10 AM" src="https://github.com/user-attachments/assets/f59433bf-a3b6-42bd-8435-ca04d0d6d857" />

The routing table shows the default route and next hop gateway.

<img width="609" height="61" alt="Screenshot 2026-03-02 at 10 16 50 AM" src="https://github.com/user-attachments/assets/2639a48d-5199-4e0b-93c5-7aa195dc14ec" />

The next hop and interface match the first traceroute hop.

### Why does `ip route get` show one hop, but traceroute shows many?  

- `ip route get` displays the immediate routing-table decision (Layer 3 next hop).  
- Traceroute reveals the full multi-hop Layer 3 path using TTL expiration.

---

# TTL Experiment  

- TTL (Time To Live) limits packet lifespan.  
- Routers decrement TTL at each hop to prevent routing loops.  
- Traceroute works by sending packets with incrementally increasing TTL values.

<img width="823" height="119" alt="Screenshot 2026-03-02 at 10 01 43 AM" src="https://github.com/user-attachments/assets/68e754f2-9758-4fdb-aae5-09847ec5092e" />

---

## Final Concept Questions  

1. The path of data is determined using traceroute and routing-table outputs.  
2. The first hop represents the default gateway.  
3. Private IPs appear early because traffic begins inside the LAN.  
4. Different destinations share initial hops because they use the same gateway and ISP routing path.  
5. A routing-table decision shows the immediate next hop, while traceroute exposes the entire multi-hop journey across routed networks.

---

# Reflection  

This project reinforced understanding of private versus public IPv4 addressing and the necessity of NAT in scalable network design. The distinction between Layer 2 switching and Layer 3 routing became clear through packet simulations and traceroute analysis. Routing tables were shown to determine only the immediate forwarding decision, while traceroute revealed the broader path across ISP and backbone infrastructure. Observing TTL behavior demonstrated how routers prevent loops and enable path discovery. Overall, the project connected theoretical networking concepts with observable command-line evidence and practical troubleshooting techniques.
