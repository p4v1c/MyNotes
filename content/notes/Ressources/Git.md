---
title: "Arch-Setup"
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

### Branch :

- Create a branch : 
```sh
git checkout -b feat/login
```

- If Existed branch : 
```sh
git checkout develop
```

- And if the the branch is in remote and note in local : 
```sh
git fetch
git checkout dev
```

- Update the branch before working :
```sh
git pull
```

-  Available branch :
```sh
git branch
git branch -r # in remote
git branch -a # all
```

### SSH

#### Without Config file 

- That means instead of:
```sh
https://github.com/your-user/project.git
```

- You'll use : 
```sh 
git@github.com:your-user/project.git
```

  - Generate an SSH key : 
```sh
ssh-keygen -t ed25519 -C "your.email@example.com"
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"
```

- Add the key to the SSH agent :
```sh
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

- Copy your public key :
```sh
cat ~/.ssh/id_ed25519.pub
```

**Add it to GitHub / GitLab** :

- GitHub: Settings → SSH and GPG keys → "New SSH Key"
- GitLab: Preferences → SSH Keys → "Add Key"

```sh
git clone git@github.com:your-user/project.git
```

#### With a config file 
- Create a config file : 
```sh
nano ~/.ssh/config
```

- add Something like this : 
```sh
# Personal GitHub
Host industry.com
  HostName dev.industry.com
  User p4v1c
  IdentityFile ~/.ssh/id_ed25519
```

- Test ssh connection :
```sh
ssh -T git@github.com
```
#### Work on the code 

- Check the status :
```sh
git status
```

- Stage Change : 
```sh
git add .
git add src/file.js # specific file
```

- Commit : 
```sh
git commit -m "✨ Add awesome feature"
```

- Push : 
```sh
git push
```

- If it's your first time pushing a new branch (you created it) :
```sh
git push -u origin feature/my-new-branch
```