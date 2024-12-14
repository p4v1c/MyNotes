---
title: "Git"
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


#git 
- Tools : 
```sh
wget https://github.com/arthaud/git-dumper
```

- Run git dumper : 
```sh
./git_dumper.py http://website.com/.git ~/website
```

- Recover files : 
```sh
git status 
git restore --staged <files>
git restore <file>
```

- Get logs :
```sh
git checkout
git log
git show a8673b295eca6a4fa820706d5f809f1a8b49fcba`
```