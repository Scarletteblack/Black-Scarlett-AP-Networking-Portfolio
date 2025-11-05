---
title: "Types of Networks & Connections and Devices"
last_modified_at: 2025-11-04T22:20:30-22:35:00

---

## Design and Planning

### Shared Mode 
In Shared mode the **internal** IP address was: inet 192.168.64.2/24

**External** (public) IP address: 
<img width="1178" height="338" alt="shared-mode0  " src="https://github.com/user-attachments/assets/1bedb508-60c0-4cc4-9f2e-7c86d550285a" />

#### Reflection - Shared Mode
1. Are your internal and external IP addresses the same or different?
2. Which IP belongs to your local network?
3. Which IP belongs to the internet?
4. Why might a virtual machine use Network Address Translation (NAT) when
connecting to the internet?
5. How does Shared mode make it easier to connect multiple virtual machines on one
computer?
--- 
### Bridged Mode

In Bridged mode the **internal** IP address was: inet 192.168.64.2/24

**External** (public) IP address: 

#### Reflection - Bridged Mode
1. How did your internal IP address change when you switched to Bridged mode?
2. Did your external IP address change or remain the same?
3. In Bridged mode, does your virtual machine act more like a separate computer or a
computer behind another device?
4. Why might an organization choose Bridged mode instead of Shared (NAT) mode?
5. What security or management challenges could come with using Bridged mode?
---

### Shared Mode VS Bridged Mode

| Mode | Internal (Private) IP | External (Public) IP | Notes |
| :------------------- | :----------: | ----------: | ----------: |
| Shared           | 192.168.64.2/24      | 173.95.44.210       |        |
| Bridged              |       |      |        |

