## level00
Hint in [video](https://elearning.intra.42.fr/notions/snow-crash/subnotions/snow-crash/videos/snow-crash)  
FIND this first file who can run only as flag00...  
```
level00@SnowCrash:~$ find / -user flag00 2>/dev/null
/usr/sbin/john
/rofs/usr/sbin/john
```
```
level00@SnowCrash:~$ cat /usr/sbin/john 
cdiiddwpgswtgt
```
use [dcode.fr](https://www.dcode.fr/caesar-cipher) result `nottoohardhere` is your password
```
level00@SnowCrash:~$ su flag00
Password: nottoohardhere
Don't forget to launch getflag ! 
flag00@SnowCrash:~$ getflag 
Check flag.Here is your token : x24ti5gi3x0ol2eh4esiuxias
```
