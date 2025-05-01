---
icon: shield
---

# Advance NAT Senario 1



<figure><img src="../../.gitbook/assets/Screenshot From 2025-04-30 15-45-21.png" alt=""><figcaption><p>Network Design</p></figcaption></figure>

So in this senario is this is what is going to happen. This is all about static mapping. So when the outside pc try to access the below IP address it should route the the relevant server.

* 192.168.10.10 -> 10.10.10.10
* 192.168.10.20 -> 10.10.10.20
* 192.168.10.30 -> 10.10.10.30

So let's get started !!!

## Configure IP adresses in ASA

```
ena
conf t

inter gig 0/0
nameif outside
ip add 192.168.10.100 255.255.255.0
no shut

inter gig 0/1
nameif inside
ip add 10.10.10.1 255.255.255.0
no shut

```

























































































