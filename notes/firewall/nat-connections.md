---
icon: shield
---

# NAT Connections

<figure><img src="../../.gitbook/assets/Screenshot From 2025-04-01 19-33-28.png" alt=""><figcaption><p>Network Topology</p></figcaption></figure>



## Static NAT

The below NAT is configured to the Management PC in the ASA2

```
enable
conf t
object network mng-out-host
host 192.168.1.2
nat (MGNT,OUTPUT) static 187.15.0.10
```

## Dynamic NAT&#x20;

The below NAT is configured to the INSIDE network in the ASA1

```
enable
conf t

object network dmz-pool
range 10.10.2.100 10.10.2.150

object network internal-subnet
subnet 192.168.8.0 255.255.255.0

nat (INSIDE,DMZ) dynamic dmz-subnet-pool
```

To check whether the IP addresses are mapped properly use the below command

```
show xlate
```

## PAT ( NAT Overload )

The below&#x20;

```
enable
conf t

object network allow-inside-subnet
range 5.5.5.1 5.5.5.5

# I created loopback IPs in the INSIDE Router

nat (DMZ,OUTPUT) dynamic interface
```

This can also be checked by the below command

```
show xlate
```
