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
1. What information did ifconfig or ip a show about your network? 
It displays details about the computers network interface. Things like IP Address, MAC Address, and Broadcast Address. 

2. What did the ping results tell you about your network connection? 
By using the ping command and receiving a successful reply, I was able to see that the network was working 

3. What role did TCP play when using Netcat? 
TCP established a reliable connection between two hosts and simplified it. 

4. Which OSI Layers were used during this entire activity? 
All of them, but mainly the Transport layer.


## **Test and Evaluation**

## **Reflection and Analysis**

