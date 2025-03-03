# Network Infrastructure and Management

## Introduction 
This report presents the design and implementation of a network for a company with four branches offices located in different cities. Each branch office has 4 departments and a total of 30PCs per branch that is 120 hosts in total. The company has been assigned the Class C IP address 210.0.10.0/24. The project involves designing a scalable and efficient network using sub netting and implementing it in Cisco Packet Tracer.

## Network Requirements and Designs
The company’s network requirements are:
•	Four branch offices located in different cities.
•	Each office has a specific number of computer.
   City 1: 40 computers
   City 2: 30 computers
   City 3: 30 computers
   City 4: 20 computers
•	Communication between branches is required.
•	Efficient utilization of the provided IP address, 210.0.10.0/24.

![image](https://github.com/user-attachments/assets/e799390d-4d36-4724-9e4a-c21f2c71ff31)

## Design:
For Physical design, each branch office is equipped with a router to connect the branch to other cities, switch to connect all computers within the office, the number of computers as per the office size and lastly for cabling Ethernet cables are used for local connections and fiber optic cables for inter-city connections.
For Logical design, the network is divided into subnets to efficiently allocate the IP addresses:
•	City 1: Subnet with 62 usable IPs (for 40 computers).
•	City 2: Subnet with 30 usable IPs (for 30 computers).
•	City 3: Subnet with 30 usable IPs (for 30 computers).
•	City 4: Subnet with 30 usable IPs (for 20 computers).

## IP Addressing and Subnetting
       Subnet Mask is calculated according to the given IP address 210.0.10.0

## Subnetting Details:
• City 1: 
	Subnet: 210.0.10.0/26 
	Usable IPs: 210.0.10.1 - 210.0.10.62 
	Router: 210.0.10.1 
	Broadcast Address: 210.0.10.63 
	Number of Hosts: 40 
• City 2: 
	Subnet: 210.0.10.64/27 
	Usable IPs: 210.0.10.65 - 210.0.10.94 
	Router: 210.0.10.65 
	Broadcast Address: 210.0.10.95 
	Number of Hosts: 30 
• City 3: 
	Subnet: 210.0.10.96/27 
	Usable IPs: 210.0.10.97 - 210.0.10.126 
	Router: 210.0.10.97 
	Broadcast Address: 210.0.10.127 
	Number of Hosts: 30 

• City 4: 
	Subnet: 210.0.10.128/27 
	Usable IPs: 210.0.10.129 - 210.0.10.158
	Router: 210.0.10.129 
	Broadcast Address: 210.0.10.159 
	Number of Hosts: 20

## Network Implementation in Cisco Packet Tracer
The network was implemented using Cisco Packet Tracer. The devices and connections are as follows: 
• Routers: One router per city (4 total). Each router is configured with the first usable IP address from the branch’s subnet.
• Switches: One switch per city (4 total). Switches are used to connect computers within the branch.
• PCs: 40 in City 1, 30 in City 2, 30 in City 3 and 20 in City 4. Assigned every PCs with the IP addresses within the usable range for each subnet in each city.

The routers were connected via serial links to form a WAN. Each city’s router was assigned an IP address for its respective subnet. The switches were connected to PCs, and the routers provided the default gateway. 
Routing was configured using dynamic routing approach. It was set up using RIP v2 on each router, enabling automatic route updates across all cities.

## Diagrams
•	Physical Topology:
A physical layout showing routers in each city connected via WAN, with switches and PCs connected locally in a star topology.

•	Logical Topology:
The logical topology diagram shows that each branch office is assigned a unique subnet and IP range, such as 210.0.10.0/26 for City 1 and 210.0.10.64/27 for City 2. Routers in each branch connect their local subnet to a WAN for inter-branch communication. The diagram also highlights connections between devices like PCs, switches, and routers, ensuring efficient and organized data flow within and between branches.

## Testing and Verification

Testing was carried out by sending messages from a PC connected to the router in City 1 to PCs connected to routers in other cities. This verified that the network allowed seamless communication between branches. Routing was checked using the show ip route command on routers to confirm that all routes were correctly configured and advertised. Traceroute commands were used to monitor the packet path between cities, ensuring accurate and efficient routing. Subnet validation confirmed that each city operated within its allocated IP range with no address conflicts. WAN links between routers were tested for stability, confirming that inter-city connections were functioning without packet loss or delays. Debugging tools such as traceroute and router-specific commands were used to resolve any detected issues, ensuring the network met the required specifications.
 
## Testing Results 

The testing confirmed that the network was successfully configured and operational. Messages sent from PCs connected to the router in City 1 were successfully delivered to PCs connected to routers in City 2, City 3, and City 4. Similarly, messages from PCs in City 2, City 3, and City 4 were sent and received successfully by PCs in other cities.  

Each router accurately routed packets based on its routing table, ensuring proper communication between subnets. The results demonstrated that:  

1. PCs within the same branch communicated seamlessly with their local router.  
2. PCs in different branches successfully communicated through their respective routers over the WAN.  
3. There was no packet loss or significant delay during message transmission.  

The network testing verified that the designed infrastructure and routing configurations were correctly implemented, allowing smooth and reliable communication between all branch offices.

## Conclusion 

The network setup for the company’s four cities was successfully designed and implemented. The correct IP addressing and subnetting were applied, ensuring that each branch office has sufficient hosts and communication is possible across all locations.  Routing was configured using both static and dynamic methods. After thorough testing, the network is operational and meets all the specified requirements.
