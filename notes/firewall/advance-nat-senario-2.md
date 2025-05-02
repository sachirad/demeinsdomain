---
icon: shield
---

# Advance NAT Senario 2



<figure><img src="../../.gitbook/assets/Screenshot From 2025-04-30 15-45-21.png" alt=""><figcaption><p>Network Design</p></figcaption></figure>

> By mistake the ASA firewall port IP is set 192.168.10.100 it needs to change as 192.168.10.1 !!!

{% hint style="info" %}
Make sure to get the VM IPs and Gateways right. It is the most common error that could occur
{% endhint %}

So in this senario is this is what is going to happen. This is all about port forwarding for specific services. So when the outside pc try to access the below ports of the IP address it should route the the relevant server.

* 192.168.10.1:80 -> 10.10.10.10:82
* 192.168.10.1:2121 -> 10.10.10.20:21
* 192.168.10.1:2222 -> 10.10.10.30:22

So let's get started !!!

## Configure IP adresses in ASA

```
ena
conf t

inter gig 0/0
nameif outside
ip add 192.168.10.1 255.255.255.0
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

So this would translate the internal 10.10.10.0/24 address into 192.168.10.1 address. This would provide outside access for internal systems.&#x20;

### Configure Default Route

I added a default router to the outside machine&#x20;

```
route outside 0.0.0.0 0.0.0.0 192.168.10.100
```

### Add ICMP for Inspection

But after doing all of this you cannot ping to the outside machine that is because the firewall does not inspect the ICMP Ping requests. So you need to add it for inspection.

<pre><code>configure terminal
<strong>policy-map global_policy
</strong>class inspection_default
inspect icmp
inspect http
inspect ftp
exit
</code></pre>

Now the Ping should work perfectly fine !!!

You can check the network translation by typing the following command in the firewall.

> You can see translation if you run a ping or some service through&#x20;

```
show xlate
```

## Outside to Inside Access Configuration

### Web-Server-1 Access

So when the external user request for the 192.168.10.1:80 it should be directed to the 10.10.10.10:82 Web-Server-1 to only access the _**Web Service**_. Here is how we can do it

```
object network WEB_SERVER
host 10.10.10.10
nat (inside,outside) static interface service tcp 82 80
```

### FTP-Server-1 Access

So when the external user request for the 192.168.10.1:2121 it should be directed to the 10.10.10.20:21 FTP-Server-1 to only access the _**FTP Service**_. Here is how we can do it

```
object network FTP_SERVER
host 10.10.10.20
nat (inside,outside) static interface service tcp 21 2121
```

### SSH-Server-1 Access

So when the external user request for the 192.168.10.1:2222 it should be directed to the 10.10.10.30:22 SSH-Server-1 to only access the _**SSH Service**_. Here is how we can do it

```
object network SSH_SERVER
host 10.10.10.30
nat (inside,outside) static interface service tcp 22 2222
```

### ACL for Inbout Access

ACL to allow externla access for that host and only to access the **`ssh, web, ftp`** services

```
access-list ALLOW-IN-SERVICES permit tcp any host 10.10.10.30 eq 22
access-list ALLOW-IN-SERVICES permit tcp any host 10.10.10.10 eq 82
access-list ALLOW-IN-SERVICES permit tcp any host 10.10.10.20 eq 21
access-group ALLOW-IN-SERVICES in interface outside
```

## Test Connection

You can try to connect with the service itself if you need a simple way try telnet

```
telnet 192.168.10.1 80
telnet 192.168.10.1 21
telnet 192.168.10.1 22
```

it should show as open and it should tell the service that is running.&#x20;
