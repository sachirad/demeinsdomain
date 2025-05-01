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

## Inside to Outside Access Configuration&#x20;

### Configure PAT&#x20;

This to make sure that inside network has access to the outside network.

```
object network inside-net
subnet 10.10.10.0 255.255.255.0
nat (inside,outside) dynamic interface
```

So this would translate the internal 10.10.10.0/24 address into 192.168.10.1 address. This would provide outside access for internal systems. You can check the network translation by typing the following command in the firewall.

```
show xlate
```

### Configure Default Route

I added a default router to the outside machine&#x20;

```
route outside 0.0.0.0 0.0.0.0 192.168.10.100
```

### Add ICMP for Inspection

But after doing all of this you cannot ping to the outside machine that is because the firewall does not inspect the ICMP Ping requests. So you need to add it for inspection.

```
configure terminal
policy-map global_policy
class inspection_default
inspect icmp
exit
```

Now the Ping should work perfectly fine !!!

## Outside to Inside Access Configuration









































































