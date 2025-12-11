# LAN Security Investigation

---

## Introduction

**Questions:**
1. Which device inside a LAN would be the easiest to compromise, and why?  
2. Does proximity equal safety?  
3. How much can a device ‘see’ inside a LAN?

**Response:**  
*(Write your paragraph here.)*

---

## LAN Threat Scenario Rotation

| Scenario Letter | Symptoms |  Hypothesis |  Justification  |
|-----------------|-----------------|----------------|-------------------------------|
| A | Default gateway does not match router| there is an issue with the DHCP server| connectivity issues and network behavior changes|
| B | Switch CPU spikes and thousands of MACs appear on one port| MAC flooding attack | Multiple MACs show up on one port and switch CPU spikes|
| C | Receives network settings from an unknown DHCP source | misconfigured router|Unknown DHCP source and conectivity issues |
| D | New device appears inside the broadcast domain and communicates broadly| Administrative issue | communicate broadly and new devices appearing|
| E | A host reaches internal systems it should not access| security policy bypass | Fire walls and other encryptions are not working|

**Reflection (5–7 sentences):**  
*(Discuss confidence, difficulty, group discussion insights, and patterns noticed.)*

---

## Task A — LAN Observation

<img width="726" height="554" alt="Screenshot 2025-12-11 at 2 55 55 PM" src="https://github.com/user-attachments/assets/094276de-7caa-4f79-99b0-dad269770198" />

All commands on the Ubuntu VM

identify:
• Your subnet
• Your default gateway
• Any visible hosts your device is aware of
• Any ARP or neighbor table entries
• Any patterns that suggest how your device learns about others on the LAN

**Reflection (2–3 sentences):**  
“How could an attacker misuse this information?”
Think about:
• What the attacker could learn
• How this information might help them impersonate a device
• How it might help them redirect or intercept traffic
Be specific—use the data from your VM as evidence.

---

## Task B — Evidence-to-Threat Analysis

| Evidence from Your VM | Possible Threat Enabled | Why? (Explanation) |
|----------------------|----------------------|-------------------|
| | | |
| | | |

---

## Task C — Threat Mini-Simulation

**Chosen Threat:** *(e.g., ARP Spoofing)*

**1. Attacker Requirements:**  
*(What the attacker needs to know first.)*

**2. Target Devices:**  
*(Which devices would be targeted.)*

**3. Victim Impact:**  
*(What changes or errors would the victim notice.)*

**4. VM Impersonation Choice:**  
*(Which VM the attacker would impersonate and why.)*

**Summary (3–4 sentences):**  
*(Explain how the threat exploits normal LAN behavior.)*

---

## Final Wrap-Up

### Part 1 — Screenshots from Both VMs

**VM #1 (Ubuntu Desktop):**  
*(Insert screenshot)*  
**Explanation:** Why would this information be valuable to an attacker?  

**VM #2 (Linux Server):**  
*(Insert screenshot)*  
**Explanation:** Why would this information be valuable to an attacker?  

---

### Part 2 — Five Common Internal LAN Threats

- **ARP Spoofing:**  
  1. *(Plain-language explanation)*  
  2. *(How it abuses trust inside the LAN)*

- **MAC Flooding:**  
  1.  
  2.  

- **Rogue DHCP Server:**  
  1.  
  2.  

- **Unauthorized Plug-In Device:**  
  1.  
  2.  

- **Lateral Movement:**  
  1.  
  2.  

---

### Part 3 — Final Reflection (3–4 sentences)

*(Which internal LAN threat is most difficult to detect and why? Include VM evidence, scenario patterns, and normal LAN behavior that can hide malicious activity.)*




# Connecting Networks in Packet Tracer
