---
title: Pwn
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
## Format string

Leaking address:

```sh
for i in $(seq 1 20); do ./ch5 %$i\$x;printf "\n";done
```

Show the content : 
```sh
for i in $(seq 1 20); do ./ch5 %$i\$x |rax2 -s |tr -cd "[:print:]" |rev;printf "\n";done
```

##  Heap Overflow

