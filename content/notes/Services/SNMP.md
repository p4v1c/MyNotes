---
title: "SNMP"
description: ""
summary: ""
date: 2023-09-07T16:06:50+02:00
lastmod: 2023-09-07T16:06:50+02:00
draft: false
weight: 800
toc: true
sidebar:
  collapsed: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  robots: "" # custom robot tags (optional)
  noindex: false # false (default) or true
---


- Be patient it take time to scan your target with UDP

Enumeration with nmap :
```sh
sudo nmap -sU --script "snmp* and not snmp-brute" -T5 10.10.11.248
```

It checks if your are able to write and at the same that enumerate snmp:
```sh
snmp-check -p 161 -c <community-string> -w <ip> -d
```
By default community string is public and the default is port 161.

Enumerate smnp:
```sh
snmpwalk -v <version> -c public <ip>
```

Brute force snmp string community : 

```sh
onesixtyone -c dict.txt 10.129.42.254
```

Enumerate User :

```sh
snmpwalk -c public -v1 192.168.50.151 1.3.6.1.4.1.77.1.2.25
```

Query all the software

```sh
snmpwalk -c public -v1 192.168.50.151 1.3.6.1.2.1.25.6.3.1.2
```

Tcp listening port : 

```sh
snmpwalk -c public -v1 192.168.50.151 1.3.6.1.2.1.6.13.1.3
```

