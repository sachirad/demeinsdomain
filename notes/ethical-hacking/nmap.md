---
icon: eye
---

# Nmap

## **Basic Commands**

### **Ping Scan (Subnet)**

```bash
sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
```

### **Netcat Command**

```bash
nc -nv -p 53 10.129.14.207 50000
```

## **Advanced Scans**

### **Full Port Scan with Version Detection**

```bash
nmap -sV -p- -v -n -Pn --disable-arp-ping --source-port 53 -oX nmapEnumHardfff.xml 10.129.14.207 --min-rate 400
```

### **ACK Scan**

```bash
nmap -sA
```

### **SYN Scan**

```bash
nmap -sS
```

### **TCP Connect Scan**

```bash
nmap -sT
```

### **UDP Scan**

```bash
nmap -sU
```

## **Port Scanning Options**

### **Scan All Ports**

```bash
-p-
```

### **Scan Specific Port (e.g., 54)**

```bash
-p54
```

## **Evasion Techniques**

### **Decoy Scan (Generate 5 Random Decoys)**

```bash
-D RND:5
```

### **Change Source IP**

```bash
-S 192.169.16.5
```

### **Change Source Port (e.g., 53)**

```bash
--source-port 53
```

### **Adjust Timing (1=Slow, 5=Fast)**

```bash
-T5
```

### **Set Minimum Packet Rate**

```bash
--min-rate 300
```

## **Best Scan Command**

### **Vulnerability Scan**

```bash
nmap -sV --script vulners --script-args mincvs=5.0 10.10.11.35 -p- -Pn -n --disable-arp-ping
```

## **Firewall/IPS/IDS Bypass Techniques**

1. Perform a **slow scan** to avoid detection.
2. Conduct a **full UDP port scan**.
3. Use a **TCP ACK scan** to probe open ports.
4. Utilize **decoys** to obscure the real source.
5. Leverage a **VPS** for scanning.
6. Experiment with different **source IP addresses** or **source ports**.
