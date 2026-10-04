# Step-by-Step

## 1. Project etup

I created a small business network in Cisco Packet Tracer.

The network includes:
- 1 Router
- 2 Switches
- 6 PCs
- 1 Server

The PCs were divided into three departments:
- Admin
- Sales
- IT

## 2. VLAN Configuration

I created the follwing VLANs:

- VLAN 10 - ADMIN
- VALN 20 - SALES
- VLAN 30 - IT

I assigned the correct switch ports to each VLAN.

## 3. Router Configuration

I configured router subinterfaces for each VLAN:

- 192.168.10.1 for ADMIN
- 192.168.20.1 for SALES
- 192.168.30.1 for IT

## 4. Static IP Configuration

I manually configured IP addresses on the PCs.

## 5. Testing

I tested connectivity using ping commands btween devices in the same VLAN and VLAN and across different VLANs.

## 6. Troubleshooting

At first, the ADMIN VLAN could not communicat with other networks.

The router interface GigabitEthernet0/0 was administartively down.

I fixed the issue using:

no shutdown

After this change,the ping tests were successful

## 7. DHCP Configuration

I configured DHCP pools on the router for the ADMIN, SALES and IT VLANs.

The router automaticlly assifhned IP addresses on the PCs in each deapartment.

## 8. DHCP Testing

After enabling DHCP, I tested connectivty between the VLANs using ping commands.

The first ping lost one packet while AP information was being learned.

The follwing testes were successful with 4 packets sent and 4 packets received.

# 9. Access Control List (ACL)

I configured an extended ACL to improve network security.

The sales network was blocked from accessing the ADMIN network.

Sales can still communicate with the IT network.

ACL rule used:

access-list 100 deny ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
access-list 100 permit ip any any

The ACL was applied inbound on the SALES VLAN interface.

## 10. ACL Testing

I tested the ACL using ping commands.

- SALES to ADMIN: Blocked successfully
- SALES to IT: Allowed successfully

The first ping to the IT network lost one packet while ARP information was being learned.

The second test was successful with 4 packets sent and 4 packets received.