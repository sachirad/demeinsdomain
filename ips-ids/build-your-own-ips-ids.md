---
description: >-
  Note that we are using an IPS/IDS Open Source Distribution called Snort. We'll
  be working with the source code of this project. I'll be working with Snort
  3.7.2.0
---

# Build Your Own IPS/IDS

Prerequisites

1. Linux OS ( I'm using CentOS )
2. Two Network Cards
3. More than 15GB Storage&#x20;
4. &#x20;At lease 2GB RAM&#x20;

## System Preparation

### Update System

```bash
# RHEL/CentOS
sudo dnf update -y

# Ubuntu/Debian
sudo apt update && sudo apt upgrade -y
```

### Install Dependencies

```bash
# RHEL/CentOS
sudo dnf groupinstall "Development Tools" -y
sudo dnf install cmake make gcc flex bison zlib zlib-devel libpcap libpcap-devel pcre pcre-devel libdnet libdnet-devel xz-devel openssl-devel libuuid-devel luajit luajit-devel -y

# Ubuntu/Debian
sudo apt install -y build-essential cmake flex bison zlib1g-dev libpcap-dev libpcre3-dev libnet1-dev liblzma-dev openssl libssl-dev libnghttp2-dev libdumbnet-dev uuid-dev luajit luajit-5.1-dev
```

## Install DAQ (Data Acquisition Library)

Download this library and unzip it

{% @github-files/github-code-block url="https://github.com/snort3/libdaq/archive/refs/tags/v3.0.19.tar.gz" %}

Unzip the project

```bash
cd path/to/the/file
tar xvzf file
```

OR

Clone the latest GitHub project ( The latest updated project )

{% @github-files/github-code-block url="https://github.com/snort3/libdaq.git" %}

```bash
git clone https://github.com/snort3/libdaq.git
```

then run the below commands,

```bash
cd path/to/unzip/file
./bootstrap
./configure && make && sudo make install
```

## Clone & Install Snort 3

Clone the latest GitHub project ( The latest updated project )

{% @github-files/github-code-block url="https://github.com/snort3/snort3.git" %}

<pre class="language-bash"><code class="lang-bash">git clone https://github.com/snort3/snort3.git
<strong>cd snort3
</strong>./configure_cmake.sh --prefix=/usr/local --enable-tcmalloc
cd build
make -j$(nproc)
sudo make install
</code></pre>

I failed a couple of times because I didn't have some dependencies. Here below,

```bash
sudo yum install hwloc hwloc-devel
sudo yum install pcre2 pcre2-devel
sudo yum install gperftools gperftools-devel
```

### Update Shared Libraries

```bash
sudo ldconfig

# add /usr/local/bin to PATH:
echo 'export PATH=$PATH:/usr/local/bin' >> ~/.bashrc
source ~/.bashrc
```

### Setup Snort Configuration & Directories

```bash
sudo mkdir -p /etc/snort/rules
sudo mkdir -p /var/log/snort
sudo mkdir -p /usr/local/lib/snort_dynamicrules
sudo cp /usr/local/etc/snort/snort.lua /etc/snort/
```

## Download & Add Snort Rules

Download the below Snort Rules

{% embed url="https://www.snort.org/downloads/community/snort3-community-rules.tar.gz" %}
Community Rules
{% endembed %}

```
cd folder/path

# Add the suitable zip file
tar xvzf snort3-community-rules.tar.gz

# Copy rules to the /etc/snort/rules folder
cp snort3-community.rules /etc/snort/rules/
```

Add the rules to the snort configuration file

```
vim /etc/snort/rules/snort3-community.rules
```



search by typing "/ips" then press i to insert the below parts

```
-- Add this to the `ips` section in /etc/snort/snort.lua:
ips =
{
    enable_builtin_rules = true,
    include = "rules/snort3-community.rules"
}

```

press "Esc" then type ":wq!" to save the changes

## Run Snort

```
snort -V
```

it should run without any error snort is installed completely

if any errors occur try below

```
# check for the daq files
ls /usr/local/lib | grep libdaq.so
cd /usr/local/lib    
sudo ldconfig
```

if that doesn't also work

```
sudo ln -s /usr/local/lib/libdaq.so.3 /lib/
```

