# network-sim-cpt
A scalable enterprise network architecture with multiple LANs connected through OSPF-enabled routers.

<img width="1213" height="602" alt="image" src="https://github.com/user-attachments/assets/171a93f8-ef08-4f03-a884-07a941480946" />

### Design choices with explanations
The network contains three separate LANs (10.0.1.0/24, 10.0.2.0/24, 10.0.3.0/24) to logically separate traffic and simplify management; each LAN has a local DHCP server (with a static IP), while OSPF between routers provides dynamic routing and redundancy. 

The router-to-router triangle ensures redundancy and reliability.

 It was not strictly necessary to have a separate DHCP server in each LAN to implement DHCP. A single DHCP server can serve all LANs if DHCP Relay (using the ip helper-address command) is configured on the routers.

 However, in this topology, we chose to place one DHCP server in each LAN because it reduces broadcast traffic from crossing routers and allows each LAN to operate independently. This approach improves reliability; if one DHCP server fails, only its LAN is affected, not the entire network. 
