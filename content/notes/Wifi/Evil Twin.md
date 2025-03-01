---
title: Evil Twin
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
airmon-ng start wlp0s20f3
airmon-ng check kill
```

- Capture mac address with AiroDump : 
```sh
airodump-ng wlp0s20f3 
```

- Capture mac address with AiroDump : 
```sh
airodump-ng --bssid WIFI -c 11 --write capture wlp0s20f3
```


```
