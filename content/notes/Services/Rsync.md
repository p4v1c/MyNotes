---
title: "Rsync"
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


```sh
#Enumeration
nc -vn target 873
```

```sh
# Listing a shared folder
rsync -av --list-only rsync://192.168.0.123/shared_name

# Copying files from a shared folder
rsync -av rsync://192.168.0.123:8730/shared_name ./rsyn_shared
```