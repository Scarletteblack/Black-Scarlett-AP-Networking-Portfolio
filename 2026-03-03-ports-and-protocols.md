# Ports and Protocols

# Design and Planning

**Initial setup in packet tracer**

<img width="402" height="121" alt="Screenshot 2026-03-03 at 1 28 46 PM" src="https://github.com/user-attachments/assets/11448903-be67-4912-bcc3-e90aa07da861" />


**PC1 pinging PC2**

<img width="282" height="179" alt="Screenshot 2026-03-03 at 1 29 53 PM" src="https://github.com/user-attachments/assets/773c500d-9f94-4a17-90ad-a24593735ce4" />

Ping operates at the network layer and uses the ICMP, not TCP or UDP. Because ping does not use TCP, a successful ping shows that a device is reachable and responding to ICMP requests, it does not prove TCP reliability or confirm that TCP-based services are functioning correctly. The key difference between TCP and UDP is that TCP is connection-oriented and ensures reliable data delivery. On the other hand, while UDP is connectionless and sends data without guaranteeing delivery. This makes TCP more reliable but slower, while UDP is faster and more efficient but less relaible.

---

## Observing TCP Behavior

**Before the data is sent:**

<img width="806" height="353" alt="Screenshot 2026-03-03 at 1 42 59 PM" src="https://github.com/user-attachments/assets/fdc2dc29-6a4f-453e-a0e6-16df11225ef0" />

The six steps described represent the TCP three-way handshake and acknowledgment process. In the first step, the flag appears as PC1 initiates the connection, and in the second step, both flags appear as PC2 responds and acknowledges the request. The final step includes the flag from PC1, confirming the response. The connection is considered established, completing the three-way handshake and allowing data transfer to begin.


  **Acknowledgement and Ordering**

| Packet Location | Acknowlagement Number |
| -------- | -------- |
| PC 1| 0 | 
| Switch| 0|
| PC2| 1 |
| Switch| 1 |
| PC1| 1 |


**ICMP vs TCP vs UDP**


Note: IP exists on layer 3 of the OSI model. TCP and UDP exist on layer 4 of the OSI model. ICMP does not exist on the OSI model.

<img alt="Screenshot 2026-03-04 at 2 32 59 PM" src="https://github.com/user-attachments/assets/dd3d6d3f-d406-44f7-a790-1e4dafa92df3" />

A ping operates on layer 3, the network layer. It uses ICMP to send requests and replies between devices. It does not use TCP or UDP. Instead, it relies on the ICMP. A successful ping does not prove TCP reliability, since TCP includes sequencing, acknowledgments, and retransmission as well.

**Observing TCP Behavior**

<img width="437" height="136" alt="Screenshot 2026-03-04 at 2 43 55 PM" src="https://github.com/user-attachments/assets/b4f99f0e-4ccd-40d6-860d-a2e9a0ce4f0b" />

<img width="232" height="129" alt="Screenshot 2026-03-04 at 2 44 48 PM" src="https://github.com/user-attachments/assets/6e553a32-9bd6-4392-aefa-a0c459c1068f" />

**Investigation 1 — Connection Establishment**

<img width="380" height="248" alt="Screenshot 2026-03-04 at 2 46 58 PM" src="https://github.com/user-attachments/assets/8bcfa129-4807-4ed6-99e1-bd80214c9c55" />

![F4404DA1-836F-41C4-BB88-93BBC2C7C5B6_4_5005_c](https://github.com/user-attachments/assets/d51babb9-af70-47b5-a530-ec84d491f311)

Before any data is sent, three steps occur. First, a packet is sent from PC1 with the **SYN** flag. Next, PC2 responds with a packet containing both **SYN and ACK** flags. Finally, PC1 sends back a packet with the **ACK** flag. The connection is confirmed as established when this final ACK is sent.



**Investigation 2 — Acknowledgment and Ordering**


|Step | Sequence Number| Acknowkedgement Number |
|---|---|---|
| PC1| 0 | 0 |
| Switch | 0 | 0 |
| PC2 | 0 | 0 |

**Investigation 3 — Header Fields and Error Detection**

<img width="535" height="247" alt="Screenshot 2026-03-04 at 2 55 53 PM" src="https://github.com/user-attachments/assets/084943ad-fc49-4aa5-af13-fbbad6e06f5f" />

Checksum: 0x0000

Header Length: 20 bytes 

The checksum is used to detect errors in the TCP header and data during transmission. If the checksum fails, the receiver will not accept the data. Instead, the data is discarded, and the sender will retransmit the missing data after not receiving an acknowledgment.


---
# Tecnical Development

**TCP vs UDP — Comparing Transmission Types**
**Predict Before Testing**

TCP is connection-oriented because it establishes a connection using a handshake and maintains it with acknowledgments and sequencing. UDP is connectionless because it sends data without setting up a connection or tracking delivery. If UDP data never arrives, nothing happens automatically since there is no acknowledgment. TCP consumes more overhead because it requires connection setup, acknowledgments, and error-checking.



**View Listening TCP Ports**

<img width="710" height="150" alt="Screenshot 2026-03-06 at 8 24 22 AM" src="https://github.com/user-attachments/assets/cfcbde2c-e7e1-4317-8564-038d00836e73" />

<img width="712" height="153" alt="Screenshot 2026-03-06 at 8 26 21 AM" src="https://github.com/user-attachments/assets/d255505a-ad1a-4d25-bd90-6afb79b016c8" />


<img width="717" height="149" alt="Screenshot 2026-03-06 at 8 30 31 AM" src="https://github.com/user-attachments/assets/4a904729-a9db-42a6-b2d1-750d7122e712" />

- Status: UNCONN means that the status is unconnected

**Live TCP vs UDP Experiment**

Terminal A: 

<img width="257" height="56" alt="Screenshot 2026-03-06 at 8 39 38 AM" src="https://github.com/user-attachments/assets/5934d877-01ab-4ca1-bfae-34e26b10a437" />

Terminal C: 

<img width="713" height="168" alt="Screenshot 2026-03-06 at 8 40 51 AM" src="https://github.com/user-attachments/assets/4809a4c2-1f3f-4269-a981-ec6e7edd0575" />

Terminal B: 

<img width="319" height="23" alt="Screenshot 2026-03-06 at 8 43 10 AM" src="https://github.com/user-attachments/assets/925b82f3-f56d-4969-b197-36358b88f579" />

Terminal C: 

<img width="715" height="73" alt="Screenshot 2026-03-06 at 8 43 39 AM" src="https://github.com/user-attachments/assets/03fe07d4-beb1-4142-91c5-1a4e5cab5dce" />


The LISTEN state is shown in the ss -tln output where port 5000 appears with the state LISTEN, meaning it is waiting for a connection. The ESTAB state is shown in the ss -tn output, where both 127.0.0.1:5000 and the port are connected, indicating an active session. The change between ss -tln and ss -tn is that the first shows a listening socket with no connection, while the second shows an actual established connection between two endpoints. This proves TCP is connection-oriented because it requires a connection to be established before data can be exchanged.

After ending the session and running ss -tn again there was nothing to read: 

<img width="712" height="40" alt="Screenshot 2026-03-06 at 8 50 59 AM" src="https://github.com/user-attachments/assets/ad18b475-5d48-44d5-995b-f0a754328b11" />


---

**Layers 5-7**

<img width="585" height="98" alt="Screenshot 2026-03-09 at 9 21 09 AM" src="https://github.com/user-attachments/assets/18fe805c-fc28-4d1d-8fa3-dc2bccd1c580" />

<img width="726" height="342" alt="Screenshot 2026-03-09 at 9 21 32 AM" src="https://github.com/user-attachments/assets/36aa821a-c77d-4d1f-adb8-c51f1a0b081b" />

The command uses HTTP/1.1 protocol identified by the header. It runs TCP at the transport layer to ensure data arrives reliably and in the correct order. While the network moves the data, the application layer is responsible for interpreting specific status codes like "200 OK," serving as the final translator for the software.


<img width="696" height="358" alt="Screenshot 2026-03-09 at 9 28 05 AM" src="https://github.com/user-attachments/assets/355253e6-a197-4932-9257-9c64b5cbf915" />

Switching to https introduces HTTP/2 and the TLS protocol. Since HTTP is naturally plain-text, encryption must occur at a higher "presentation" sub-layer to secure the data before it hits the wire. The TLS handshake seen in the output establishes trust, a mandatory step that must finish before any actual application data can be safely sent.


<img width="721" height="74" alt="Screenshot 2026-03-09 at 9 30 00 AM" src="https://github.com/user-attachments/assets/8d927771-ff25-46b8-adfe-2109bf7c3de4" />

The ss -tn command monitors the transport layer. This indicates the  current attempt at a TCP three-way handshake. The application or the OS decides when to end this session, but the underlying TCP layer remains indifferent to the data.


<img width="702" height="131" alt="Screenshot 2026-03-09 at 9 46 07 AM" src="https://github.com/user-attachments/assets/5f6a9e7f-824b-4ca2-b764-6dce058d4eb0" />

<img alt="Screenshot 2026-03-09 at 9 46 36 AM" src="https://github.com/user-attachments/assets/ddf8dd98-22be-4af5-8829-e139ef66cc0c" />



| Protocol | Layer | Purpose |
|----------|-------|---------|
| HTTP | Application Layer | Transfers web pages and resources between a web server and a browser. |
| HTTPS | Application Layer | Secure version of HTTP that encrypts web traffic using TLS to protect data. |
| TLS | Transport/Security Layer | Encrypts data to provide secure communication over a network. |
| DNS | Application Layer | Translates domain names (like example.com) into IP addresses used by computers. |
| TCP | Transport Layer | Provides reliable, ordered, and error-checked delivery of data between devices. |

---

The transport layer is insufficient because it only ensures TCP reliability—the technical delivery of packets—without understanding what the data is or if it is secure. In contrast, Layer 5 manages the communication state, determining when a dialogue begins and ends beyond the simple packet-level handshake. Layer 6 handles formatting and the TLS handshake observed in the OpenSSL output; this is where TLS encryption occurs to transform plain text into a secure format that TCP then carries. Finally, the application layer governs behavior by interpreting specific instructions. This allows the network to reliably move data layer 4 while the upper layers ensure it is private layer 6 and meaningful to the user layer 7.



---

No connectivity issues: 

<img width="581" height="166" alt="Screenshot 2026-03-11 at 12 35 15 PM" src="https://github.com/user-attachments/assets/2b820845-f05c-4864-83de-d2c9dd215cd8" />


<img width="1020" height="104" alt="Screenshot 2026-03-11 at 12 43 45 PM" src="https://github.com/user-attachments/assets/14fbc158-0ec2-4914-bcb6-255344605d5c" />


<img width="1092" height="90" alt="Screenshot 2026-03-11 at 12 46 05 PM" src="https://github.com/user-attachments/assets/da47108a-293e-4977-a40e-c96df4dda0eb" />

At the application layer, traffic changes from HTTP to HTTPS, meaning data is now encrypted instead of sent in plain text. At the transport layer, TCP is still used, but with added overhead from the TLS handshake. The connections use port 80 for HTTP and port 443 for HTTPS. The additional protocol that appears is TLS, which sits between HTTP and TCP to provide encryption. TLS does not replace TCP. It operates above it, so the full path becomes Application (HTTP) → Encryption (TLS) → Transport (TCP) → IP.

<img width="420" height="463" alt="Screenshot 2026-03-11 at 12 53 55 PM" src="https://github.com/user-attachments/assets/61aeef90-cecf-4fdb-8054-9b2fad780648" />

DNS typically uses port 53 and usually operates over UDP because it is fast and has low overhead. It does not require guaranteed delivery in most cases since DNS queries are small, quick lookups that can simply be retried if a response is lost. However, DNS may switch to TCP when responses are too large for UDP (such as zone transfers or DNSSEC responses) or when reliability becomes necessary.

<img width="906" height="296" alt="Screenshot 2026-03-11 at 12 56 11 PM" src="https://github.com/user-attachments/assets/e51553d7-cd0e-43e6-bed1-dddb5de16fdc" />


<img width="633" height="506" alt="Screenshot 2026-03-11 at 12 59 47 PM" src="https://github.com/user-attachments/assets/66da8919-3829-4c08-b34d-0902cf2f37a6" />

<img width="714" height="76" alt="Screenshot 2026-03-11 at 1 00 03 PM" src="https://github.com/user-attachments/assets/d35ec61b-59c6-4a55-9d94-4ef9d763c784" />

SSH is using port 22, as shown by the connection 127.0.0.1:22. It runs over the TCP transport protocol, which is indicated by the ss -tn command (the -t shows TCP connections). Yes, the connection is encrypted, since SSH automatically encrypts all data during the session. Evidence of this includes the SSH key fingerprint verification and the secure login process requiring authentication. The OSI layers involved are the application layer (SSH), transport layer (TCP), and network layer (IP), working together to establish and maintain the remote session.

<img width="713" height="75" alt="Screenshot 2026-03-11 at 1 02 41 PM" src="https://github.com/user-attachments/assets/0d9a62e6-8855-4a9f-8aab-12cd2bfac77d" />


1. What protocol does SCP rely on?
2. Does SCP require TCP?
3. Is the file encrypted?
4. What would happen if TCP reliability were removed?
5. Which layers are involved in this transfer?
Map the stack explicitly.

<img width="563" height="266" alt="Screenshot 2026-03-23 at 1 29 00 PM" src="https://github.com/user-attachments/assets/f12ff49b-f672-453f-8cea-d3828b610b1e" />

<img width="587" height="245" alt="Screenshot 2026-03-23 at 1 30 42 PM" src="https://github.com/user-attachments/assets/70a9ff30-c1b9-4ade-91c1-9841fca102bf" />

<img width="1084" height="106" alt="Screenshot 2026-03-23 at 1 44 20 PM" src="https://github.com/user-attachments/assets/95612553-5d49-4a5e-913f-8782eae24a3c" />
