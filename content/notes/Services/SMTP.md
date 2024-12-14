---
title: "SMTP"
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


- Open relay : 
```sh
nmap <IP> -p25 --script smtp-open-relay -v
```

- try to send mail : 
```sh
swaks --from '<EMAIL>' --to '<EMAIL>' --server <IP> --header "Subject: Test d'intrusion AlgoSecure" --body "Bonjour, ceci est un message d'AlgoSecure. Si vous recevez cet email, votre serveur de messagerie est mal configuré. Pourriez-vous nous transmettre une copie de cet email lorsque vous le recevrez ? Merci d'avance. Cordialement."
```