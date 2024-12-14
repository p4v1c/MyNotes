---
title: "Upgrade"
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

- Upgrade 1:
```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
echo $TERM
stty -a
#speed 38400 baud; rows 46; columns 174; line = 0;


export SHELL=bash
export TERM=xterm256-color
stty rows 46 columns 174
```