# Understanding Physical and Logical Addressing


## Planning & Conceptual Understanding

A MAC address is a unique identifier in a device’s Network Interface Card (NIC). It is considered a physical address because it is  directly connected to the hardware of the NIC. Instead of changing from network to network, the MAC stays the same no matter where the device goes. This allows devices on the same local network to identify each other at the data-link layer. A MAC address identifies the device on a local network, while an IP address identifies a device across the entire internet.


![IMG_2457](https://github.com/user-attachments/assets/637f2536-a098-4538-9445-fe319051444d)
A NIC showing the Ethernet port, main controller chip, and PCIe connector.


![IMG_2458](https://github.com/user-attachments/assets/31825deb-0540-48f6-9159-e10e172b9d69)
A NIC showing its PCIe connector, Ethernet port, main chip area, and printed MAC address label.

* The Ethernet port (RJ-45 jack) is where the network cable plugs in
* The PCIe connector is connected to the motherboard, providing power and allowing data transfer
* The Controller chip is the IC that handles network processing
* The MAC address label is the printed sticker with the MAC value


### Physical vs. Logical Address Comparison** 
**Physical Address (MAC Address)**
* Set by the manufacturer and stored in the NIC hardware
* Stays the same no matter what network the device joins
* Used for communication inside a local network (Layer 2)
* Written in hexadecimal 
* Identifies the specific hardware of the device

**Logical Address (IP Address)**
* Assigned by a network and can change depending on where the device connects
* Used for communication between networks and across the internet (Layer 3)
* Written in IPv4 or IPv6 format
* Helps routers send data to the correct destination
* Identifies the location of a device on a network

**Both**
* Used to identify devices on a network
* Work together so data can move locally and globally
* Are required for sending and receiving packets

### IPv4 vs. IPv6

**IPv4**
IPv4 is the older version of the Internet Protocol that uses 32-bit addresses—numbers. It allows about 4 billion unique addresses, which isn’t enough for the number of devices.

**IPv6**
IPv6 is the newer version of the Internet Protocol that uses 128-bit addresses—longer, hex-based numbers. It was created because of the limited IPv4 addresses. IPv6 includes improvements such as better routing efficiency and built-in security features.

## Technical Development


o Screenshot of student’s VM MAC address
o Completed OUI lookup table for seven MAC addresses
o Manufacturer identification + comparison of physical vs. virtual MACs
• Logical Addressing (Lesson 2)
o Screenshot of ip addr show with IPv4 + IPv6 link-local highlighted
o Student-created IPv4 vs IPv6 comparison table
o Paragraph on why logical addressing exists
• Dynamic vs Static Addressing (Lesson 3)
o DHCP analysis from both VMs
o Screenshots of each VM’s configuration outputs
o Completed scenario decision table with two-sentence justification per device
• Static IP Configuration on VM #2 (Lesson 4)
o Screenshot of edited Netplan YAML file
o Screenshots of: 
§ ip addr show
§ ip route show
§ ping -c 4 8.8.8.8
o Evidence that the student attempted troubleshooting if errors occurred




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

### Ubuntu VM

<img width="733" height="345" alt="Screenshot 2025-12-02 at 2 53 15 PM" src="https://github.com/user-attachments/assets/7308c6fb-c928-4da3-bc43-9f83cbed09ea" />

<img width="531" height="168" alt="Screenshot 2025-12-02 at 2 54 06 PM" src="https://github.com/user-attachments/assets/be7bf655-9393-463c-be8e-d86d23c4204f" />


### Linux 
<img width="649" height="288" alt="Screenshot 2025-12-02 at 2 27 00 PM" src="https://github.com/user-attachments/assets/effb3d14-0f9d-49e9-9577-b2e3389c5154" />

<img width="556" height="258" alt="Screenshot 2025-12-02 at 2 33 41 PM" src="https://github.com/user-attachments/assets/4de11aae-6c86-42c5-af59-24924e2cbe2e" />
* Putting sudo after the first command - result: ran successfully

<img width="628" height="311" alt="Screenshot 2025-12-02 at 2 30 31 PM" src="https://github.com/user-attachments/assets/c6f32475-b2b4-43ab-be6b-56e5b5d37aad" />

<img width="611" height="171" alt="Screenshot 2025-12-02 at 2 31 05 PM" src="https://github.com/user-attachments/assets/8b3abbc7-db19-46d7-8b9f-b420dae747cc" />

<img width="642" height="378" alt="Screenshot 2025-12-02 at 2 41 38 PM" src="https://github.com/user-attachments/assets/17228ea7-87bb-48c8-b76e-fa74aa1cadc2" />

The VM uses network manager and netplan 



## 4 

<img width="331" height="287" alt="Image 12-4-25 at 8 24 AM" src="https://github.com/user-attachments/assets/756b6bcc-07c5-41a4-80da-105ab00ebd44" />


<img width="648" height="363" alt="Screenshot 2025-12-04 at 8 39 23 AM" src="https://github.com/user-attachments/assets/b53b40cf-eb0f-4fc3-820a-1befe9e5daee" />


<img width="635" height="63" alt="Screenshot 2025-12-04 at 8 48 36 AM" src="https://github.com/user-attachments/assets/bcb70201-6380-43a1-9ac4-acbd8d60185c" />


<img width="530" height="185" alt="Screenshot 2025-12-04 at 8 49 11 AM" src="https://github.com/user-attachments/assets/06d1a957-b077-4834-a965-881224986d8f" />

