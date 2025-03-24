# Development

This document details the assigned IP addresses, subnet masks, OSPF areas, and Router IDs (RIDs). Additionally, it includes configuration guidelines for routers, redistribution points, and routing features. The network consists of fourteen routers (R1-R14) running different routing protocols (OSPF, EIGRP, etc.), as shown in the network diagram. The table below summarizes the IP addresses assignments:

| Device | Interface | IP            | Mask            | CIDR | Gateway       | OSPF Area | OSPF RID | EIGRP   |
| ------ | --------- | ------------- | --------------- | ---- | ------------- | --------- | -------- | ------- |
| CA1    | f0/0      | 10.10.4.1     | 255.255.255.240 | /28  | NA            | 0         | 1.1.1.1  | NA      |
|        | s1/0      | 41.41.41.2    | 255.255.255.252 | /30  | NA            | 23        |          |         |
|        | l0        | 1.1.1.1       | 255.255.255.255 | /32  | NA            | 23        |          |         |
| NY1    | f0/0      | 10.10.4.2     | 255.255.255.240 | /28  | NA            | 0         | 2.2.2.2  | NA      |
|        | s1/0      | 52.52.52.1    | 255.255.255.252 | /30  | NA            | 25        |          |         |
|        | l0        | 2.2.2.2       | 255.255.255.255 | /32  | NA            | NA        |          |         |
| TX1    | f0/0      | 10.10.4.3     | 255.255.255.240 | /28  | NA            | 0         | 3.3.3.3  | NA      |
|        | s1/0      | 37.37.37.1    | 255.255.255.252 | /30  | NA            | 51        |          |         |
|        | l0        | 3.3.3.3       | 255.255.255.255 | /32  | NA            | NA        |          |         |
| CA2    | s1/0      | 41.41.41.1    | 255.255.255.252 | /30  | NA            | 23        | 4.4.4.4  | NA      |
|        | f0/0      | 23.23.4.126   | 255.255.255.128 | /25  | NA            | 23        |          |         |
|        | f0/1      | 46.46.46.1    | 255.255.255.252 | /30  | NA            | 23        |          |         |
|        | l0        | 4.4.4.4       | 255.255.255.255 | /32  | NA            | NA        |          |         |
| NY2    | s1/0      | 52.52.52.2    | 255.255.255.252 | /30  | NA            | 25        | 5.5.5.5  | NA      |
|        | f0/0      | 25.25.4.30    | 255.255.255.224 | /27  | NA            | 25        |          |         |
|        | l0        | 5.5.5.5       | 255.255.255.255 | /32  | NA            | NA        |          |         |
| CA3    | f0/0      | 33.33.4.62    | 255.255.255.192 | /26  | NA            | 33        | 6.6.6.6  | NA      |
|        | f0/1      | 46.46.46.2    | 255.255.255.252 | /30  | NA            | 23        |          |         |
|        | l0        | 6.6.6.6       | 255.255.255.255 | /32  | NA            | 23        |          |         |
| TX2    | s1/0      | 37.37.37.2    | 255.255.255.252 | /30  | NA            | 51        | 7.7.7.7  | NA      |
|        | f0/0      | 51.51.4.126   | 255.255.255.128 | /25  | NA            | 51        |          |         |
|        | l0        | 7.7.7.7       | 255.255.255.255 | /32  | NA            | NA        |          |         |
| USA    | f0/0      | 10.10.4.4     | 255.255.255.240 | /28  | NA            | NA        | NA       | 101.123 |
|        | s1/0      | 123.4.123.2   | 255.255.255.252 | /30  | NA            | NA        |          |         |
|        | s1/1      | 101.4.101.2   | 255.255.255.252 | /30  | NA            | NA        |          |         |
| UE     | f0/0      | 123.4.123.6   | 255.255.255.252 | /30  | NA            | NA        | NA       | 123     |
|        | s1/0      | 123.4.123.1   | 255.255.255.252 | /30  | NA            | NA        |          |         |
| SPAIN  | f0/0      | 123.4.123.5   | 255.255.255.252 | /30  | NA            | NA        | NA       | 123     |
|        | f0/1      | 123.4.123.10  | 255.255.255.252 | /30  | NA            | NA        |          |         |
| FRANCE | f0/0      | 123.123.4.2   | 255.255.255.0   | /24  | NA            | NA        | NA       | 123     |
|        | f0/1      | 123.4.123.9   | 255.255.255.252 | /30  | NA            | NA        |          |         |
| MX     | s1/0      | 101.4.101.1   | 255.255.255.252 | /30  | NA            | NA        | NA       | 101     |
|        | f0/0      | 101.4.101.6   | 255.255.255.252 | /30  | NA            | NA        |          |         |
|        | f0/1      | 101.4.101.10  | 255.255.255.252 | /30  | NA            | NA        |          |         |
| MTY    | f0/0      | 101.4.101.9   | 255.255.255.252 | /30  | NA            | NA        | NA       | 101     |
|        | f0/1      | 101.4.101.14  | 255.255.255.252 | /30  | NA            | NA        |          |         |
| GDL    | f0/0      | 101.4.101.5   | 255.255.255.252 | /30  | NA            | NA        | NA       | 101     |
|        | f0/1      | 101.4.101.13  | 255.255.255.252 | /30  | NA            | NA        |          |         |
|        | f1/0      | 101.101.4.126 | 255.255.255.128 | /25  | NA            | NA        |          |         |
| PC1    | e0        | 23.23.4.1     | 255.255.255.128 | /25  | 23.23.1.126   | NA        | NA       | NA      |
| PC2    | e0        | 33.33.4.1     | 255.255.255.192 | /26  | 33.33.1.62    | NA        | NA       | NA      |
| PC3    | e0        | 25.25.4.1     | 255.255.255.224 | /27  | 25.25.1.30    | NA        | NA       | NA      |
| PC4    | e0        | 51.51.4.1     | 255.255.255.128 | /25  | 51.51.1.126   | NA        | NA       | NA      |
| PC5    | e0        | 123.123.4.1   | 255.255.255.0   | /24  | 123.123.4.2   | NA        | NA       | NA      |
| PC6    | e0        | 101.101.4.1   | 255.255.255.128 | /25  | 101.101.4.126 | NA        | NA       | NA      |

In order to configure the routers the following commands must be used:

* **Routers IP**
```shell
conf t 
int [Interface]
no switchport # Only if this is part of a 16 ports expansion 
ip address [IP] [MASK] 
no shutdown
```

* **Configure OSPF Totally Stubby Area (Only applies to Area 51 in this lab)**
```shell
router ospf 100 
area [Area number] stub no-summary
```
>Use this command to define a totally stubby area specifically.

* **Configure OSPF Virtual Links**
```shell
router ospf 100 
area [Area number] virtual-link [RID]
```
>A virtual link is used to connect to the backbone through a non-backbone area.

* **Config BDR/DR**
```shell
int [interface] 
ip ospf priority [0-255]
```
>Default priority (0-255) is 1; highest priority wins and 0 cannot be elected.  
>A designated router (DR) is responsible for establishing and maintaining adjacencies. The backup designated router (BDR) is the backup router for when the DR fails, it assumes the job of DR.

* **Config OSPF area**
```shell
int [interface]
ip ospf 100 area [Area number]
```

* **Config OSPF Area 0**
```shell
router ospf 100
redistribute static subnets
network 10.10.1.0 0.0.0.15 area 0
```

* **Config Loopback**
```shell
interface loopback 0
ip add [IP/RID] [MASK]
```

* **Config RID**
```shell
router-id [RID]
```

* **Configure EIGRP**
```shell
router eigrp [N]
network [IP address] [Wildcard Mask]
no auto summary #only if needed
```

* **EIGRP Redistribution Example
```shell
router eigrp 101
redistribute eigrp 123
redistribute ospf 100 metric 1000 100 255 1 1500
network 101.4.101.0 0.0.0.3
```

* **OSPF Redistribution Example
```
router ospf 100
network 10.10.4.0 0.0.0.15 area 0
redistribute static subnets
redistribute eigrp 123 metric 1 subnets
redistribute eigrp 101 metric 1 subnets
```

And lastly, the configuration for VPCs is the following:
```shell
ip [ip_address]/[mask] [gateway]
```
