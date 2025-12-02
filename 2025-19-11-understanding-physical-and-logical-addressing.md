# Understanding Physical Addressing


### Comparing the VM digital MAC address to the physical NICs from Part A


Write a short comparison (4–5 sentences) addressing:
1. Where the MAC address came from on the physical NIC images
2. Where the MAC address came from in your VM
3. What is the same between physical and virtual MAC addressesWhat is
different
4. Why a virtual NIC still requires a MAC address


| Full MAC Address        | OUI (first 3 pairs) | Vendor / Company Name | Type of Vendor (physical, virtual, or both) | 
|-------------------------|----------------------|------------------------|----------------------------------------------|
| F0:18:98:AA:BB:CC       | F0:18:98             |      Apple, Inc.      |     Physical Vendor          |                    
| 3C:5A:B4:11:22:33       | 3C:5A:B4             |     Google, Inc.        |      Physical Vendor                    |        
| 60:45:BD:12:34:56       | 60:45:BD             |    Microsoft     |        Physical Vendor             |                          
| A4:BA:DB:22:33:44       | A4:BA:DB             |    Dell Inc.      |     Physical Vendor                |                          
| 04:1A:04:55:66:77       | 04:1A:04             |   WaveIP     |       Physical Vendor            |                           
| 00:50:56:AA:BB:CC       | 00:50:56             |   VMware, Inc.      |     Physical Vendor      |                           
| 52:54:00:12:34:56       | 52:54:00             |   Not Found - Virtual Machine     |    Virtual Vendor                      |                       



### Connecting the Physical and Digital: Interpreting MAC Address Structure

**On Ubuntu VM**

MAC address: 32:9e:41:5a:ae:94
• OUI: 32:9e:41
• Device Identifier: 5a:ae:94


**On MAC Terminal**

MAC address: 14:98:77:6f:58:9d
• OUI: 14:98:77
• Device Identifier: 6f:58:9d



## Understanding Logical Addressing 

<img width="644" height="288" alt="Screenshot 2025-12-01 at 1 39 47 PM" src="https://github.com/user-attachments/assets/e403454f-108f-48ba-aba9-880ee28d4387" />




## 3 
Dynamic vs. Static Addressing & When to Use Each

Addressing: Physical and Logical

### Linux 
<img width="649" height="288" alt="Screenshot 2025-12-02 at 2 27 00 PM" src="https://github.com/user-attachments/assets/effb3d14-0f9d-49e9-9577-b2e3389c5154" />

<img width="556" height="258" alt="Screenshot 2025-12-02 at 2 33 41 PM" src="https://github.com/user-attachments/assets/4de11aae-6c86-42c5-af59-24924e2cbe2e" />
* Putting sudo after the first command - result: ran successfully

<img width="628" height="311" alt="Screenshot 2025-12-02 at 2 30 31 PM" src="https://github.com/user-attachments/assets/c6f32475-b2b4-43ab-be6b-56e5b5d37aad" />

<img width="611" height="171" alt="Screenshot 2025-12-02 at 2 31 05 PM" src="https://github.com/user-attachments/assets/8b3abbc7-db19-46d7-8b9f-b420dae747cc" />

<img width="642" height="378" alt="Screenshot 2025-12-02 at 2 41 38 PM" src="https://github.com/user-attachments/assets/17228ea7-87bb-48c8-b76e-fa74aa1cadc2" />

The VM uses network manager and netplan 
