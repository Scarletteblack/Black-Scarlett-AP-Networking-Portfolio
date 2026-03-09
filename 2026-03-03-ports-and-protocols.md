# Ports and Protocols

**Initial setup in packet tracer**

<img width="402" height="121" alt="Screenshot 2026-03-03 at 1 28 46 PM" src="https://github.com/user-attachments/assets/11448903-be67-4912-bcc3-e90aa07da861" />


**PC1 pinging PC2**

<img width="282" height="179" alt="Screenshot 2026-03-03 at 1 29 53 PM" src="https://github.com/user-attachments/assets/773c500d-9f94-4a17-90ad-a24593735ce4" />

PARA - what layer is responsible for this ping, is the ping using tcp or udp, does successful ping prove tcp reliability

Short PARA what are the key differences between TCP and UDP

---

## Observing TCP Behavior

**Before the data is sent:**

<img width="806" height="353" alt="Screenshot 2026-03-03 at 1 42 59 PM" src="https://github.com/user-attachments/assets/fdc2dc29-6a4f-453e-a0e6-16df11225ef0" />

There were six total steps in the packet traveling to PC2 and the acknowlagement that is sent back to PC1. 
- what flags have apeared, what flags appear in the second
- what confirms the connection is established

  **Acknowledgement and Ordering**


| Packet Location | Acknowlagement Number |
| -------- | -------- |
| PC 1| 0 | 
| Switch| 0|
| PC2| 1 |
| Switch| 1 |
| PC1| 1 |

**TCP Header Feilds**


---

**ICMP vs TCP vs UDP**


Note: IP exists on layer 3 of the OSI model. TCP and UDP exist on layer 4 of the OSI model. ICMP does not exist on the OSI model.

<img alt="Screenshot 2026-03-04 at 2 32 59 PM" src="https://github.com/user-attachments/assets/dd3d6d3f-d406-44f7-a790-1e4dafa92df3" />

1. What layer is responsible for this ping?
2. Is ping using TCP or UDP?
3. Does successful ping prove TCP reliability?

**Observing TCP Behavior**

<img width="437" height="136" alt="Screenshot 2026-03-04 at 2 43 55 PM" src="https://github.com/user-attachments/assets/b4f99f0e-4ccd-40d6-860d-a2e9a0ce4f0b" />

<img width="232" height="129" alt="Screenshot 2026-03-04 at 2 44 48 PM" src="https://github.com/user-attachments/assets/6e553a32-9bd6-4392-aefa-a0c459c1068f" />

**Investigation 1 — Connection Establishment**

<img width="380" height="248" alt="Screenshot 2026-03-04 at 2 46 58 PM" src="https://github.com/user-attachments/assets/8bcfa129-4807-4ed6-99e1-bd80214c9c55" />

![F4404DA1-836F-41C4-BB88-93BBC2C7C5B6_4_5005_c](https://github.com/user-attachments/assets/d51babb9-af70-47b5-a530-ec84d491f311)

1. What flag appears in the first packet?
2. What flag(s) appear in the second?
3. What flag appears in the third?
4. After which packet does data begin?


**Investigation 2 — Acknowledgment and Ordering**


|Step | Sequence Number| Acknowkedgement Number |
|---|---|---|
| PC1| 0 | 0 |
| Switch | 0 | 0 |
| PC2 | 0 | 0 |

1. Do sequence numbers increase?
2. Do acknowledgment numbers increase?
3. Does the sender transmit additional data before receiving acknowledgment?
4. What does this imply about how TCP ensures delivery?

**Investigation 3 — Header Fields and Error Detection**

<img width="535" height="247" alt="Screenshot 2026-03-04 at 2 55 53 PM" src="https://github.com/user-attachments/assets/084943ad-fc49-4aa5-af13-fbbad6e06f5f" />

- Checksum:
- Header Length:

1. What is the purpose of the checksum?
2. If the checksum failed, would the receiver accept the data?
3. If data were rejected, what would logically happen next?
4. 
**Observing UDP Behavior**

---

**TCP vs UDP — Comparing Transmission Types**
**Predict Before Testing**


1. What makes TCP “connection-oriented”?
2. What makes UDP “connectionless”?
3. If you send data using UDP and it never arrives, what happens?
4. Which protocol do you believe consumes more overhead? Why?


**View Listening TCP Ports**

<img width="710" height="150" alt="Screenshot 2026-03-06 at 8 24 22 AM" src="https://github.com/user-attachments/assets/cfcbde2c-e7e1-4317-8564-038d00836e73" />

<img width="712" height="153" alt="Screenshot 2026-03-06 at 8 26 21 AM" src="https://github.com/user-attachments/assets/d255505a-ad1a-4d25-bd90-6afb79b016c8" />

Which process is using port 22 (if visible)?
• If port 22 does not appear, what does that suggest?
• What is the difference between:
o A port existing
o A port listening

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

What evidence shows LISTEN?
• What evidence shows ESTAB?
• What changed between ss -tln and ss -tn?
• Why does this prove TCP is connection-oriented?

After ending the session and running ss -tn again there was nothing to read: 

<img width="712" height="40" alt="Screenshot 2026-03-06 at 8 50 59 AM" src="https://github.com/user-attachments/assets/ad18b475-5d48-44d5-995b-f0a754328b11" />


**UDP Experiment**

Terminal A: 

---

**Layers 5-7**

<img width="585" height="98" alt="Screenshot 2026-03-09 at 9 21 09 AM" src="https://github.com/user-attachments/assets/18fe805c-fc28-4d1d-8fa3-dc2bccd1c580" />

<img width="726" height="342" alt="Screenshot 2026-03-09 at 9 21 32 AM" src="https://github.com/user-attachments/assets/36aa821a-c77d-4d1f-adb8-c51f1a0b081b" />


1. What protocol is being used?
2. What transport protocol is underneath it?
3. How do you know?
4. Which layer is responsible for interpreting “200 OK”?
Do not define HTTP yet—just describe what you observe.

<img width="696" height="358" alt="Screenshot 2026-03-09 at 9 28 05 AM" src="https://github.com/user-attachments/assets/355253e6-a197-4932-9257-9c64b5cbf915" />

1. What changed?
2. What additional protocol must now be involved?
3. Does HTTP itself provide encryption?
4. Where does encryption logically occur?

<img width="721" height="74" alt="Screenshot 2026-03-09 at 9 30 00 AM" src="https://github.com/user-attachments/assets/8d927771-ff25-46b8-adfe-2109bf7c3de4" />


1. What is being exchanged before data transfer?
2. Is this Layer 4 behavior?
3. What problem is this solving?
4. Why must this occur before application data is sent?


<img width="721" height="184" alt="Screenshot 2026-03-09 at 9 30 26 AM" src="https://github.com/user-attachments/assets/0f535c6e-ca29-4266-8dde-36675a902f44" />

1. Is the connection still active?
2. What state is it in?
3. When does the session end?
4. Who decides that?
5. If you log into a website with a username and password:
• Is that TCP managing your login?
• Or is that handled at a higher layer?

| Protocol | Layer | Purpose |
|----------|-------|---------|
| HTTP | Application Layer | Transfers web pages and resources between a web server and a browser. |
| HTTPS | Application Layer | Secure version of HTTP that encrypts web traffic using TLS to protect data. |
| TLS | Transport/Security Layer | Encrypts data to provide secure communication over a network. |
| DNS | Application Layer | Translates domain names (like example.com) into IP addresses used by computers. |
| TCP | Transport Layer | Provides reliable, ordered, and error-checked delivery of data between devices. |


1. Why does encryption not occur at Layer 3?
2. Why does TCP not handle user authentication?
3. Why separate:
• Transport reliability
• Encryption
• Application logic
4. What would break if all of this were collapsed into one layer?

---

B. Write a structured paragraph explaining:
• What role Layer 5 plays in managing communication state
• What role Layer 6 plays in formatting and encryption
• What role Layer 7 plays in application behavior
• Why Layer 4 alone is insufficient

Your explanation must:
• Reference at least one curl command
• Reference the TLS handshake observation
• Distinguish between TCP reliability and TLS encryption
Avoid vague phrases such as: “Layer 7 is the top layer.”
