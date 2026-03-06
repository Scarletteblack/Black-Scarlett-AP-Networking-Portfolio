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
