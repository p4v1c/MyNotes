---
title: "Android Emulation"
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
## Emulation + Burp

- Setup Genymotion & install Gapp . 
```
adb devices
adb connect 127.0.0.1:6555
adb shell settings put global http_proxy localhost:3333
adb reverse tcp:3333 tcp:6767
```

- Generate a new certificate with burp and apply this command on it  : 
```sh
openssl x509 -inform DER -in burp.der -out burp.pem
```

```sh
openssl x509 -inform PEM -subject_hash_old -in burp.pem | head -1
```

- Name of certificate must a the same value from the last command plus `.0` :
```sh
mv burp.pem 9a5ba575.0
adb root && adb remount
adb push 9a5ba575.0 /sdcard/
adb shell
mv /sdcard/9a5ba575.0 /system/etc/security/cacerts/
chmod 644 /system/etc/security/cacerts/9a5ba575.0
```

- Bypass SSL pinning  :
https://codeshare.frida.re/@akabe1/frida-multiple-unpinning/
https://github.com/frida/frida

- Place the frida-server into the target :
```sh
adb push frida-server-16.5.7-android-x86 /data/local/frida-new-server
chmod +x frida-new-server && ./frida-new-server
```
- Install frida : 
```sh
sudo pip3 install frida frida-tools objection
```

- Create a file to place the js script that frida will run and run this command : 
```sh
frida -U -f package_name_target -l fridascript.js
frida -U -f com.some.appdiscovery -l fridascript.js 
```
- Example : https://play.google.com/store/apps/details?id=com.some.appdiscovery&hl=fr&pli=1

##  App to apk

- Check is devices detected :
```sh
adb shell pm list packages
```

- List package on the device : 
```sh
adb shell pm list packages
```

- Get the path of the package :
```sh
adb shell pm path com.example.someapp-2.apk
```

- Download the apk : 
```
adb pull /data/app/com.example.someapp-2.apk
```