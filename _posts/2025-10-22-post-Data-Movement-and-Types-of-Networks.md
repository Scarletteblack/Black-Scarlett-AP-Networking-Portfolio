---
title: "Data Movement and Types of Networks"
last_modified_at: 2025-11-06

---

## **Design and Planning**

### Networking Analogy

Here is an analogy to help conceptualize the Networking and the relationship between devices:  
First, think of the Local Area Network (LAN) — the LAN is like a neighborhood.
![Photo9](https://github.com/user-attachments/assets/dc048686-200a-44e9-94d3-1ea76b2aa143)
![Photo10](https://github.com/user-attachments/assets/00bbf36a-f015-4a92-bcc7-8bee4038b57a)
![Photo11](https://github.com/user-attachments/assets/b3840411-b8f5-4da8-b9b4-d27c7d833a9c)
![Photo12](https://github.com/user-attachments/assets/324e17a1-277a-4afb-986f-3d7d6d228b60)

Below are diagrams of OSL Models, definitions, and examples: 
![mymodel](https://github.com/user-attachments/assets/4b7b4853-6b1e-4be3-a1c1-fb85cb390f66)
This is the initial diagram

This diagram is corrected and from the class:
<img width="710" height="858" alt="classmodel" src="https://github.com/user-attachments/assets/1145faeb-cfb3-4cab-9053-3148c7f828b0" />

### Roadmap
* project due Nov 11

## **Technical Development**

Using the ifconfig command, the IP Address was identified as **192.168.64.2** as shown below:
![Photo1](https://github.com/user-attachments/assets/b28b730d-5997-4fe3-9587-cb82e6fe5f67)

**Switch to MAC terminal**

Then, using the **ping** command, connectivity was checked, and a successful connection was established:
<img width="480" height="290" alt="Untitled" src="https://github.com/user-attachments/assets/726a92a1-aedb-401c-8e87-cbc6bf2013ce" />

Next, the ports were checked using **netstat -a**, and a few of the active ports are shown below:
<img width="408" height="342" alt="active" src="https://github.com/user-attachments/assets/a3ba0a1e-7aa8-423b-98ec-e87f5b87c5b1" />

Next, two MACs were connected to send and receive messages. The receiving MAC used the command **nc -1 4444**, meaning it was open to receive notifications. The sender then used the command **nc <receiving_IP> 4444**, inserting the receiving MAC IP address to connect to it. The 'hi' typed from the sending MAC appeared on the receiving end. 

<img width="295" height="30" alt=" connecting" src="https://github.com/user-attachments/assets/f6b222e5-28cb-4eb1-a8ea-b98ee652ba44" />

### Reflection
The ifconfig displays details about the computer's network interface. Information like IP Address, MAC Address, and Broadcast Address. By using the ping command and receiving a successful reply, it was determined that the network was working. TCP established a reliable connection between two hosts and simplified it. All OSL layers were present, but mainly the **Transport layer**.

## **Test and Evaluation**

Ping:
The ping command sends small data packets to an IP address and measures how long it takes to get a response, checking connectivity.
![Photo3](https://github.com/user-attachments/assets/99005a6f-3780-460b-94b9-4d344663a5cf)
The command above (ping 8.8.8.8) only tests the connectivity

![Photo2](https://github.com/user-attachments/assets/612eec40-cf83-4fff-ba35-4033a6f1e00f)
This command, however, (ping google.com) tests both connectivity and DNS


Traceroute: 
The traceroute command follows the path data takes and shows all of the hops.
![Photo5](https://github.com/user-attachments/assets/734c36b1-d5c3-4e5b-8f7f-1a3e634d4600)

Latency Hops: the delay introduced when a data packet passes through a single network device

### Binary and Hexadecimal

Notes on denary, binary, and hexadecimal conversions:  
![binary-denary-hex-notes](https://github.com/user-attachments/assets/bcf32a0b-dd3a-42f1-be9d-17cba6d9c013)

Practice conversions: 
![binary-denary-hex-practice](https://github.com/user-attachments/assets/da26e74a-e1bb-4851-b8bf-018877471aea)


**Converting in Ubuntu VM**

ipcalc, as seen below, first displays the IP address in denary (blue). It is followed by the IP address in binary (orange/brown)

![Image 10-28-25 at 10 05 AM](https://github.com/user-attachments/assets/f4ed2115-3582-4923-939c-3d9d0f4921c0)

printf, as seen below, displays the IP address in hexadecimal after inputting it in denary.
![Image 10-28-25 at 10 09 AM (1)](https://github.com/user-attachments/assets/80475447-d186-47e4-9e8a-c51232b877ec)

###### An additional way of converting hexadecimal to denary: 
Take the first part of the hexadecimal number and multiply it by 16. This is because hexadecimal is base 16. Then the second number is just multiplied by 1. Then add the two values to find the number in denary. 
The reverse would be to see how many times 16 goes into the number in denary, that number becomes the first hexadecimal number and the remainder is the second part.

## **Reflection and Analysis**

This project taught about Local Area Network (LAN) connections and communication, using analogies like neighborhoods. The OSI and TCP/IP models helped teach how data travels in layers, from the physical signals all the way up to the applications we use every day. When using the Ubuntu VM, commands like ifconfig, ping, netstat, and nc are used to observe how devices can be identified, test connectivity, and exchange data across the network. Seeing the ‘hi’ message appear between two MACs demonstrated how TCP ensures reliable communication between hosts. The ping and traceroute commands also revealed the path and latency of data packets, showing how real networks experience hops. Converting IP addresses between binary, denary, and hexadecimal taught how computers process and represent data. Together, these skills connected theory with practice and showed how each OSI layer plays a role in transmitting information. 

