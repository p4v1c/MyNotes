---
title: "Keygen-Me"
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


- Function : 

_start:  main function
sub_400135: Calculates the length of the input
sub_400146: Performs certain operations:
            --> Takes each character of our input - i + 0x14
            --> Then compares it to the file .m.key


- Exploit: 
```python
python3 -c "import sys; sys.stdout.buffer.write(b'\x86\x82\x81\x85\x3d\x7c\x73\x3b\x7b\x7d\x71')" > .m.key
```

- Important Breakpoints : 
```sh
break *0x0040014f
break *0x00400166
```

- Python Code : 

```python

import hashlib

login = input("Type your username:\n ")
charset = list(login.encode('utf-8'))

i = 0
for idx, char in enumerate(charset):
    charset[idx] = char + 0x14 - i
    i += 1
print(charset)

hashed_bytes = hashlib.sha256(bytes(charset)).hexdigest()

print("Hash SHA-256 of the transformed bytes:", hashed_bytes)
```