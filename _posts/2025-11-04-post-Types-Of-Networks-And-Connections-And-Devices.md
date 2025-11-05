---
title: "Types of Networks & Connections and Devices"
last_modified_at: 2025-11-04T22:20:30-22:35:00

---

## Design and Planning



### Shared Mode 
In Shared mode the **internal** IP address was: 192.168.64.2/24
<img width="727" height="286" alt="Screenshot 2025-11-05 at 10 27 23 AM" src="https://github.com/user-attachments/assets/00ec1032-0528-4c1c-a11e-1d5266cde0a0" />

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

In Bridged mode the **internal** IP address was: 10.32.1.32/23
<img width="719" height="356" alt="Image 11-5-25 at 10 25 AM" src="https://github.com/user-attachments/assets/3b97b973-2472-4cf0-bae1-aae3f429f0c6" />

**External** (public) IP address: 
<img width="1178" height="338" alt="shared-mode0  " src="https://github.com/user-attachments/assets/1bedb508-60c0-4cc4-9f2e-7c86d550285a" />

#### Reflection - Bridged Mode
1. How did your internal IP address change when you switched to Bridged mode?
2. Did your external IP address change or remain the same?
3. In Bridged mode, does your virtual machine act more like a separate computer or a
computer behind another device?
4. Why might an organization choose Bridged mode instead of Shared (NAT) mode?
5. What security or management challenges could come with using Bridged mode?
---

### Shared Mode VS Bridged Mode

| Mode | Internal (Private) IP | External (Public) IP |
| :------------------- | :----------: | ----------: |
| Shared           | 192.168.64.2/24      | 173.95.44.210       |
| Bridged              |  10.32.1.32/23     |  173.95.44.210    |
| Notes              | Both private IP Addresses| Same |


Write a short paragraph (5–7 sentences) beneath your table addressing the following:
• Which mode made your VM appear as its own device on the local network?
• Which mode provided a safer, more controlled environment?
• How does NAT help manage limited IPv4 addresses and improve security?
• What did you learn about how data travels from a device to the internet?

Step 1: Add Screenshots
Take screenshots of the following and insert them into your digital portfolio:
• The output of ip a in Shared (NAT) mode
• The output of ip a in Bridged mode
• The WhatIsMyIPAddress.com page results for both modes
Step 2: Reflection Writing
Write a short reflection (1 paragraph, 5–8 sentences) below your screenshots that answers these:
• How did your IP addresses change between Shared and Bridged mode?
• What did this experiment teach you about how local and public networks communicate?
• Why might IT professionals use different network configurations for home, business, or
lab environments?
• Which mode do you think is best for classroom use, and why?
