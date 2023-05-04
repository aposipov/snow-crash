## level01
```
flag00@SnowCrash:~$ su level01
Password: x24ti5gi3x0ol2eh4esiuxias
level01@SnowCrash:~$
```
you need install [Kali Linux](https://www.kali.org/) image for [VB](https://www.kali.org/get-kali/#kali-virtual-machines)  
research /etc/passwd /etc/shadow
```
level01@SnowCrash:~$ cat /etc/passwd
[...]
level14:x:2014:2014::/home/user/level14:/bin/bash
flag00:x:3000:3000::/home/flag/flag00:/bin/bash
flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
flag02:x:3002:3002::/home/flag/flag02:/bin/bash
[...]
```
`42hDRfypTqqnw` use `john` in Kali Linux on your PC
```
┌──(kali㉿kali)-[~/snowcrash]
└─$ echo 42hDRfypTqqnw > passwd
```
```
┌──(kali㉿kali)-[~/snowcrash]
└─$ john passwd 
Using default input encoding: UTF-8
Loaded 1 password hash (descrypt, traditional crypt(3) [DES 256/256 AVX2])
Will run 2 OpenMP threads
Proceeding with single, rules:Single
Press 'q' or Ctrl-C to abort, almost any other key for status
Almost done: Processing the remaining buffered candidate passwords, if any.
Proceeding with wordlist:/usr/share/john/password.lst
abcdefg          (?)     
1g 0:00:00:00 DONE 2/3 (2023-05-01 08:49) 33.33g/s 409600p/s 409600c/s 409600C/s 123456..Herman1
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```
```
level01@SnowCrash:~$ su flag01 
Password: abcdefg
Don't forget to launch getflag !
flag01@SnowCrash:~$ getflag 
Check flag.Here is your token : f2av5il02puano7naaf6adaaf
```
