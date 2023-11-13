Tech Stack: Cisco Packet tracer 

download cisco packet tracer:

https://www.packettracernetwork.com/download/download-packet-tracer.html

The purpose of this exercise is to configure EIGRP on all the devices and test for ping and trace commands.

The router eigrp 0 or eigrp 1 command given in the lab below selects EIGRP as the routing protocol.

The network command assigns a major network number that the router is directly connected to.

Instructions:

1) Assign the IP address of all the devices as given below

Device	Interface	IP Address	Mask
R1	
S0/0
S0/1	
192.168.1.1
192.168.3.1	
255.255.255.0
255.255.255.0
R2	
S0/0
S0/1	
192.168.1.2
192.168.2.1	
255.255.255.0
255.255.255.0
R3	
S0/0
S0/1	
192.168.3.2
192.168.2.2	
255.255.255.0
255.255.255.0

2) Bring all the interfaces to up

3) Configure EIGRP on all the Devices,Use Autonomous System number 0 or 1

4. From R1 issue ping and trace command to R2-S0/1 and R3-S0/1 interfaces and check the connectivity

Commands:

On R1

R1>enable
R1#configure terminal
R1(config)#interface serial 0/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)#exit
R1(config)#interface serial 0/1
R1(config-if)#ip address 192.168.3.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)#exit
R1(config)#router eigrp 0
R1(config-router)#network 192.168.1.0
R1(config-router)#network 192.168.3.0


On R2

R2>enable
R2#configure terminal
R2(config)#interface serial 0/0
R2(config-if)#ip address 192.168.1.2 255.255.255.0
R2(config-if)# no shutdown
R2(config-if)#exit
R2(config)#interface serial 0/1
R2(config-if)#ip address 192.168.2.1 255.255.255.0
R2(config-if)# no shutdown
R2(config-if)#exit
R2(config)#router eigrp 0
R2(config-router)#network 192.168.1.0
R2(config-router)#network 192.168.2.0

On R3

R3>enable
R3#configure terminal
R3(config)#interface serial 0/0
R3(config-if)#ip address 192.168.3.2 255.255.255.0
R3(config-if)# no shutdown
R3(config-if)#exit
R3(config)#interface serial 0/1
R3(config-if)#ip address 192.168.2.2 255.255.255.0
R3(config-if)# no shutdown
R3(config-if)#exit
R3(config)#router eigrp 0
R3(config-router)#network 192.168.3.0
R3(config-router)#network 192.168.2.0

On R1

R1#ping 192.168.2.2
R1#ping 192.168.2.1
R1#trace 192.168.2.2
R1#trace 192.168.2.1

if all the ping and trace commands are successful, then the connection is established.