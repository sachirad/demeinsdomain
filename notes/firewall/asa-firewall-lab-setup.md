---
icon: shield
---

# ASA Firewall Lab Setup



<figure><img src="../../.gitbook/assets/Screenshot From 2025-04-01 19-33-28.png" alt=""><figcaption><p>Practice Setup</p></figcaption></figure>



## Devices

* Outside: Thit is the Outside Network
* ASA2: First Firewall
* PC1: This is a Windows Server
* DMZ: This is theDemilitarized Zone
* ASA1: Second Firewall&#x20;
* Inside: This is the Internal Network .



## Configure IP Addresses

### "INSIDE" Router IP Configuration

```
enable
conf ter
inter fa0/0
ip add 192.168.8.2 255.255.255.0
no shut

inter loopback 0
ip add 4.4.4.4 255.255.255.255
no shut

end
wr memory
```



### "ASA1" Firewall IP Configuration

```
enable
conf t
inter gig0/0
nameif INSIDE
ip add 192.168.8.1 255.255.255.0
no shut

inter gig0/1
nameif DMZ
ip add 10.10.2.1 255.255.255.0
no shut

wr memory
```



### "DMZ" Router IP Configuration

```
enable
conf t
inter fa0/1
ip add 10.10.2.2 255.255.255.0
no shut

inter fa0/0
ip add 10.10.1.2 255.255.255.0
no shut

inter loopback 0
ip add 2.2.2.2 255.255.255.255
no shut

end
wr
```



### "ASA2" Firewall IP Configuration

<pre><code>enable
conf t
<strong>int gig 0/0
</strong>nameif DMZ
ip add 10.10.2.1 255.255.255.0
no shut

int gig 0/1
nameif OUTPUT
ip add 187.15.0.1 255.255.255.0
no shut

int gig 0/2
nameif MGNT
ip add 192.168.1.1 255.255.255.0
security-level 50
no shut

wr memory

</code></pre>



### "OUTSIDE" Router IP Configuration

```
enable
conf ter
inter fa0/1
ip add 187.15.0.2 255.255.255.0
no shut

inter loopback 0
ip add 8.8.8.1 255.255.255.255
no shut

inter loopback 1
ip add 8.8.8.2 255.255.255.255
no shut

end
wr memory
```



## Build Backbone Connectivity

### "ASA1" Firewall

```
enable
conf t
route INSIDE 4.4.4.4 255.255.255.255 192.168.8.2
route DMZ 0.0.0.0 0.0.0.0 10.10.2.2
```
