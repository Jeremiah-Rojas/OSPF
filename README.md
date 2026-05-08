# OSPF

# Network Topology
<img width="582" height="351" alt="image" src="https://github.com/user-attachments/assets/8a71155f-4203-49de-8702-7f91f9c8aba6" />

<br>OSPF (Open Shortest Path First) is a protocol on routers that dynamically routes traffic to find the shortest path to a given destination. This protocol using link-state as a cost metric meaning that it will always choose the fastest cable because the faster the cable, the lower the cost. The slower the cable, the higher the cost. For this lab, all cables are gigabit and have the same cost of 1. It essentialy enables traffic to reach its destination as quickly and efficiently.

This lab demonstrates OSPF's functionality.

### Devices Used:
- Cisco IOSvL2 15.2.1 switch
- GNS3 Software
- Ubuntu Container (running on VMware machine)

## Configurations

__Note: It is recommended to copy and paste these commands into the routers. Because of the limited width of the table, some commands, which should be treated as one line, are broken into two lines and entering these commands as two lines will throw an error.__

| R1 | R2 | R3 | R4 |
|----|----|----|----|
| conf t<br>hostname R1<br>end<br><br>conf t<br>interface loopback0<br>ip address 1.1.1.1 255.255.255.255<br>exit<br>interface g0/0<br>ip address 10.0.12.1 255.255.255.0<br>no shutdown<br>exit<br>interface g0/1<br>ip address 10.0.41.1 255.255.255.0<br>no shutdown<br>exit<br><br>router ospf 1<br>router-id 1.1.1.1<br>network 10.0.12.0 0.0.0.255 area 0<br>network 10.0.41.0 0.0.0.255 area 0<br>network 1.1.1.1 0.0.0.0 area 0<br>end<br>wr | conf t<br>hostname R2<br>end<br><br>conf t<br>interface loopback0<br>ip address 2.2.2.2 255.255.255.255<br>exit<br>interface g0/0<br>ip address 10.0.12.2 255.255.255.0<br>no shutdown<br>exit<br>interface g0/1<br>ip address 10.0.23.2 255.255.255.0<br>no shutdown<br>exit<br><br>router ospf 1<br>router-id 2.2.2.2<br>network 10.0.12.0 0.0.0.255 area 0<br>network 10.0.23.0 0.0.0.255 area 0<br>network 2.2.2.2 0.0.0.0 area 0<br>end<br>wr | conf t<br>hostname R3<br>end<br><br>conf t<br>interface loopback0<br>ip address 3.3.3.3 255.255.255.255<br>exit<br>interface g0/0<br>ip address 10.0.34.3 255.255.255.0<br>no shutdown<br>exit<br>interface g0/1<br>ip address 10.0.41.3 255.255.255.0<br>no shutdown<br>exit<br><br>router ospf 1<br>router-id 3.3.3.3<br>network 10.0.34.0 0.0.0.255 area 0<br>network 10.0.41.0 0.0.0.255 area 0<br>network 3.3.3.3 0.0.0.0 area 0<br>end<br>wr | conf t<br>hostname R4<br>end<br><br>conf t<br>interface loopback0<br>ip address 4.4.4.4 255.255.255.255<br>exit<br>interface g0/0<br>ip address 10.0.34.4 255.255.255.0<br>no shutdown<br>exit<br>interface g0/1<br>ip address 10.0.23.4 255.255.255.0<br>no shutdown<br>exit<br><br>router ospf 1<br>router-id 4.4.4.4<br>network 10.0.34.0 0.0.0.255 area 0<br>network 10.0.23.0 0.0.0.255 area 0<br>network 4.4.4.4 0.0.0.0 area 0<br>end<br>wr |

<br>Addresses such as "1.1.1.1" are loopback addresses.

These images show OSPF fully functional and the configuration details:

<br>Router 1: <img width="875" height="139" alt="image" src="https://github.com/user-attachments/assets/75bf4d7b-9114-42f1-91dc-dacbcaf356dc" />
<br>OSPF Details: <img width="869" height="194" alt="image" src="https://github.com/user-attachments/assets/3604db1b-e244-4a22-89ef-a71182fd031e" />
<br>OSPF route (using “show ip route ospf”): <img width="872" height="240" alt="image" src="https://github.com/user-attachments/assets/b237db59-466d-461a-865b-61bbd88e02d1" />



<br>Router 2: <img width="872" height="140" alt="image" src="https://github.com/user-attachments/assets/448fdfe2-0f8a-4430-a81a-6dfd9fd28706" />
<br>OSPF Details: <img width="873" height="196" alt="image" src="https://github.com/user-attachments/assets/cf91cc3e-e163-4eb0-8a44-249394cda15b" />
<br>OSPF route (using “show ip route ospf”): <img width="873" height="240" alt="image" src="https://github.com/user-attachments/assets/8cf5e206-38d6-494d-8738-dbcda2f86d85" />



<br>Router 3: <img width="874" height="139" alt="image" src="https://github.com/user-attachments/assets/58006ae0-1b2b-4d92-ba6d-5cccbf91d5a4" />
<br>OSPF Details: <img width="872" height="196" alt="image" src="https://github.com/user-attachments/assets/be8e7712-e78f-497d-9dc5-d23048ca8640" />
<br>OSPF route (using “show ip route ospf”): <img width="874" height="233" alt="image" src="https://github.com/user-attachments/assets/6cfd45cf-7bc1-4bfc-8ce5-fcb5f8a8c936" />



<br>Router 4: <img width="874" height="135" alt="image" src="https://github.com/user-attachments/assets/c4dad6fd-a2e7-4b87-8c22-75df0b983ff3" />
<br>OSPF Details: <img width="871" height="195" alt="image" src="https://github.com/user-attachments/assets/58c1ebc7-5ead-4951-acbe-63c02638d1a0" />
<br>OSPF route (using “show ip route ospf”): <img width="872" height="235" alt="image" src="https://github.com/user-attachments/assets/af8f177e-b416-43a3-940f-4264570f2a66" />


## New topology after stopping “breaking” a link:
<img width="524" height="313" alt="image" src="https://github.com/user-attachments/assets/78ec6274-1a68-4e0d-ac06-0a8041d9a256" />

Below are the resulting changes:

<br>Router 1 OSPF details: <img width="874" height="403" alt="image" src="https://github.com/user-attachments/assets/8ea0bda0-c7b5-4cae-b2df-878071312169" />


<br>Router 2 OSPF details: <img width="873" height="398" alt="image" src="https://github.com/user-attachments/assets/13bff3b0-329e-4b6b-becf-8fe45ebbc22e" />


<br>Router 3 OSPF details: <img width="872" height="403" alt="image" src="https://github.com/user-attachments/assets/3764e049-4524-4af0-8a94-1fae4d56be26" />



<br>Router 4 OSPF details: <img width="873" height="410" alt="image" src="https://github.com/user-attachments/assets/db64ad30-ab4f-424d-8682-b88d1578c7d1" />

(DR) Designated Router: the central router responsible for 
- collecting and distributing OSPF link-state updates
- reducing the number of OSPF adjacencies required
(BDR) Backup Designated Router: a standby router that 
- listens to all OSPF updates
- immediately takes over if the DR fails
“Gateway of last resort is not set” means no default gateway is configured. A default gateway is where traffic is sent when the router doesn’t know how to reach a certain address/device.

## Conclusions

__Note: I apologize in advance because the comparison images may be hard to read.__
The changes may be difficult to spot so I am going to explain them briefly:
- The link between R1 and R2 was "broken" on port g0/0 on both devices
- On the Router 1 OSPF details, under the “Neighbor ID” column, the “2.2.2.2” entry is no longer present after the break. Also, the state changes from “BDR” to “DOWN” on the g0/0 interface. On the bottom two images, we see the results: The destination “2.2.2.2” is no longer reachable via ```10.0.12.2``` which is the IP of R2. Now it is only reachable going through ```10.0.41.3``` which is R4.
<img width="1806" height="456" alt="image" src="https://github.com/user-attachments/assets/e77ca46a-d149-4ca6-ad6b-e4aa5133a4fa" />

- We see very similar changes in the same places on Router 2:
<img width="1799" height="455" alt="image" src="https://github.com/user-attachments/assets/0bfb9911-e398-4e5c-9224-e0d906ee535f" />

- For the remaining configuration changes on R3 and R4, the routes under "Gateway of last resort is not set" are altered when attempting to reach "1.1.1.1" and "2.2.2.2". 
