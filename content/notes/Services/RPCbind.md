---
title: "RPCbind"
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
## rpcbind

Get  some information : 
```sh
showmount -e
```

Mount the directories :
```sh
sudo mount -t nfs -o vers=4 10.10.121.175:/profiles /mntc
```

Clean : 
```sh
sudo umount /mnt
```