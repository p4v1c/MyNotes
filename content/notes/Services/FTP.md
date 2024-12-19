---
title: "FTP"
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

## FTP
- SSH port open + credential   :
Check if your are able to upload files  ,  if you can create a .ssh folder and upload a authorized_keys file in it .

- Unauthenticated enumeration with nmap :

```sh
sudo nmap -sV -p21 -sC -A 10.10.10.10
```

- Anonymous login :
```sh
anonymous : anonymous
anonymous :
ftp : ftp
ftp ftp://anonymous:anonymous@$t/
```

- Download everything : 
```sh
wget -m ftp://anonymous:anonymous@$t
```

