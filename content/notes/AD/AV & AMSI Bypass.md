---
title: "AV & AMSI Bypass"
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

Ressources: 

https://amsi.fail/
https://github.com/0xb11a1/yetAnotherObfuscator/releases

- Disable AV :
```sh
Set-MpPreference -DisableRealtimeMonitoring $true
```

- Shellter:

https://github.com/Hanrikusvz/Powershell-to-shellcode

https://www.microsoft.com/en-us/security/blog/2018/03/01/finfisher-exposed-a-researchers-tale-of-defeating-traps-tricks-and-complex-virtual-machines/