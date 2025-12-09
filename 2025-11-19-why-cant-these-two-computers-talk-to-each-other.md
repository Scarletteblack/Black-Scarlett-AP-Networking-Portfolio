# Why Can't These Two Computers Talk to Each Other?

## Planning and Design
Working in pairs, partners figured out why two computers connected directly with an Ethernet cable cannot communicate. Both computers are running Ubuntu virtual machines and are connected with a working Ethernet cable. The main layers that could have issues are the physical layer, data link layer, and the network layer. The most likely scenario is that there is an issue in the data link layer or the network layer. 

---

## Checking Layer 1 - The Physical Layer

The ethernet cable was plugged into both MACs and the connection was checked to be firm and secure. In each Ubuntu VM Terminal ip a was used to find the MAC address where it says link/ether <MAC address> by enp0s1. Then, looking next to the enp0s1 tag, the interface showed UP, meaning the ethernet cable allowed for a stable connection, the NICs and enabled and the Ubuntu VM is recognizing the connection. If the interface displayed DOWN, that would have indicated that the physical layer is not active. Because the issue is not physical, it means the issue is happening in the data link or network layer.

**Both Partners VMs:**

<img width="644" height="365" alt="516960731-66861367-47ca-45fa-a1b2-e18e679554ca" src="https://github.com/user-attachments/assets/72d1ea85-66c1-4ff5-bf5b-abcf909cfc36" />

IP of VM 1

<img width="639" height="356" alt="unnamed-11" src="https://github.com/user-attachments/assets/4d6e614b-eabc-45ec-9b8c-3fe514a171f3" />

IP of VM 2

---

## Checking Layer 2 -The Data Link Layer

The two VMs were on the same network in order to communicate directly; however, the two VMs have different MAC addresses. Using the ping command and inserting the other VM's IP, the reachability of the other MAC was tested. If the ping was successful and the packet was able to reach the other MAC, it would have shown the time it took the packet to travel between the two. However, the ping failed and both partners got the message Destination Host Unreachable. This is evident that Layer 2 cannot find the partner’s MAC address and thus cannot send any packets through the data link. 


**Both partners' VM pings**

<img width="1074" height="440" alt="unnamed" src="https://github.com/user-attachments/assets/7c679641-284c-4e2d-bc5e-ded8fc444c45" />

VM #1 ping unsuccessful 

<img width="641" height="236" alt="516961369-8b1cdc4c-8ea0-432d-80ac-67f4adfdc1ad" src="https://github.com/user-attachments/assets/1a99164a-f2de-40f8-921c-76bc390c0d52" />

VM #2 ping unsuccessful 

---

## Checking Layer 3 - Network Layer 

<img width="347" height="44" alt="Screenshot 2025-12-08 at 1 38 34 PM" src="https://github.com/user-attachments/assets/8af30c4d-9ccf-4472-ac63-dc1e5af91d83" />

IP 1

<img width="277" height="47" alt="Screenshot 2025-12-08 at 1 39 06 PM" src="https://github.com/user-attachments/assets/2e30d61c-3a94-4b9b-be85-819a525642ca" />

IP 2

**Explanation**

Although both virtual machines show very similar IP addresses, they are not part of the same Layer 3 network. UTM assigns each VM to its own isolated host-only network, complete with a separate virtual switch and its own DHCP server. This makes the IPs appear related, but the machines are actually in different broadcast domains and cannot receive each other’s ARP messages. Since ARP cannot operate across two distinct virtual switches, the VMs are unable to communicate at Layer 3 despite having matching IP ranges. Therefore, Layer 3 connectivity is not possible in this setup.

## Making it Work

<img width="1288" height="404" alt="unnamed-10" src="https://github.com/user-attachments/assets/fa65f93b-bcf4-4196-b663-154ce03e1f8d" />

Changing VM 1 to bridged mode

<img width="1652" height="684" alt="unnamed-12" src="https://github.com/user-attachments/assets/3c1d4817-3368-489b-8124-3ca8a59d5df7" />

<img width="1052" height="530" alt="unnamed-13" src="https://github.com/user-attachments/assets/80f2d8fd-7ef1-4c52-89a3-32dc2206adf9" />

Successful ping on VM 1

<img width="711" height="210" alt="unnamed-5" src="https://github.com/user-attachments/assets/e0b82156-768a-44b8-b693-dc0bf6e53f34" />

Changing VM 2 to bridged mode

<img width="647" height="327" alt="unnamed-15" src="https://github.com/user-attachments/assets/15a28482-64b3-4baf-95c5-f957191bf11d" />



<img width="613" height="230" alt="unnamed-14" src="https://github.com/user-attachments/assets/0f75861a-7b48-4927-bf20-b18b84c48416" />

Successful ping on VM 2


The VMs needed to be placed in bridged mode rather than shared mode so they could exchange Layer 2 frames over the same virtual network. After switching to bridged mode, static IP addresses had to be assigned using nmcli, because two computers connected directly do not have access to any DHCP server that could automatically provide network configuration.


## Reflection 

Even though the two computers were linked with a functioning Ethernet cable at Layer 1, communication failed because the systems were placed in separate virtual Layer 2 broadcast domains within UTM. Each VM was assigned to its own isolated virtual switch and DHCP service, so ARP messages could not reach the other machine. Since no MAC resolution was possible, Layer 2 communication broke down, which also prevented any Layer 3 exchange between the two different IP networks. UTM enforces this separation in Host-Only mode to provide sandboxing, security, and controlled traffic flow between virtual machines. To allow communication, both VMs would need to be attached to the same virtual network—such as a shared Host-Only interface, a bridged adapter, or a custom virtual LAN created inside UTM. In real SOHO networks, switches maintain a shared Layer 2 broadcast domain for devices that should communicate locally, while routers connect different IP subnets and forward traffic only when networks are properly configured.
