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
