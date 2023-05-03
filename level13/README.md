## level13
```
level12@SnowCrash:~$ su level13
Password: g1qKMiRpXf53AWhDaU7FEkczr
level13@SnowCrash:~$
```
```
level13@SnowCrash:~$ ll
total 20
dr-x------ 1 level13 level13  120 Mar  5  2016 ./
d--x--x--x 1 root    users    340 Aug 30  2015 ../
-r-x------ 1 level13 level13  220 Apr  3  2012 .bash_logout*
-r-x------ 1 level13 level13 3518 Aug 30  2015 .bashrc*
-rwsr-sr-x 1 flag13  level13 7303 Aug 30  2015 level13*
-r-x------ 1 level13 level13  675 Apr  3  2012 .profile*
```
```
level13@SnowCrash:~$ ./level13 
UID 2013 started us but we we expect 4242
```
Use ltrace to intercept dynamic library calls and system calls executed by the program.
Program calls getuid(), check the result against 4242 and exits if it don't match.
```
level13@SnowCrash:~$ ltrace ./level13 
__libc_start_main(0x804858c, 1, 0xbffff7e4, 0x80485f0, 0x8048660 <unfinished ...>
getuid()                                                                          = 2013
getuid()                                                                          = 2013
printf("UID %d started us but we we expe"..., 2013UID 2013 started us but we we expect 4242
)                               = 42
exit(1 <unfinished ...>
+++ exited (status 1) +++
```
Run binary under GDB.
```
level13@SnowCrash:~$ gdb ./level13
GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2.1) 7.4-2012.04
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>...
Reading symbols from /home/user/level13/level13...(no debugging symbols found)...done.
```
Disassemble main function to see what's done.
```
(gdb) disassemble main
Dump of assembler code for function main:
   0x0804858c <+0>:	push   %ebp
   0x0804858d <+1>:	mov    %esp,%ebp
   0x0804858f <+3>:	and    $0xfffffff0,%esp
   0x08048592 <+6>:	sub    $0x10,%esp               
   0x08048595 <+9>:	call   0x8048380 <getuid@plt>      # getuid() is called and the result is stored in eax register
   0x0804859a <+14>:	cmp    $0x1092,%eax            # %eax register is compared against 0x1092 (4242)    
   0x0804859f <+19>:	je     0x80485cb <main+63>     # if it equal jump to 0x080485cb
   0x080485a1 <+21>:	call   0x8048380 <getuid@plt>
   0x080485a6 <+26>:	mov    $0x80486c8,%edx
   0x080485ab <+31>:	movl   $0x1092,0x8(%esp)
   0x080485b3 <+39>:	mov    %eax,0x4(%esp)
   0x080485b7 <+43>:	mov    %edx,(%esp)
   0x080485ba <+46>:	call   0x8048360 <printf@plt>
   0x080485bf <+51>:	movl   $0x1,(%esp)
   0x080485c6 <+58>:	call   0x80483a0 <exit@plt>
   0x080485cb <+63>:	movl   $0x80486ef,(%esp)        
   0x080485d2 <+70>:	call   0x8048474 <ft_des>      # call ft_des() function
   0x080485d7 <+75>:	mov    $0x8048709,%edx
   0x080485dc <+80>:	mov    %eax,0x4(%esp)
   0x080485e0 <+84>:	mov    %edx,(%esp)
   0x080485e3 <+87>:	call   0x8048360 <printf@plt>
   0x080485e8 <+92>:	leave
   0x080485e9 <+93>:	ret
End of assembler dump.
(gdb) break *0x0804859a
Breakpoint 1 at 0x804859a
(gdb) run
Starting program: /home/user/level13/level13
```
