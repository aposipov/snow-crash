## level09
```
flag08@SnowCrash:~$ su level09
Password: 25749xKZ8L7DkSCwJkT9dyv6f
level09@SnowCrash:~$ 
```
```
level09@SnowCrash:~$ ll
total 24
dr-x------ 1 level09 level09  140 Mar  5  2016 ./
d--x--x--x 1 root    users    340 Aug 30  2015 ../
-r-x------ 1 level09 level09  220 Apr  3  2012 .bash_logout*
-r-x------ 1 level09 level09 3518 Aug 30  2015 .bashrc*
-rwsr-sr-x 1 flag09  level09 7640 Mar  5  2016 level09*
-r-x------ 1 level09 level09  675 Apr  3  2012 .profile*
----r--r-- 1 flag09  level09   26 Mar  5  2016 token
```
```
level09@SnowCrash:~$ ./level09 00000
01234
level09@SnowCrash:~$ ./level09 01234
02468
level09@SnowCrash:~$ ./level09 56789
579;=
level09@SnowCrash:~$ ./level09 token 
tpmhr
level09@SnowCrash:~$ cat token 
f4kmm6p|=�p�n��DB�Du{��
```
```
#include <stdio.h>
#include <string.h>

void    main(void)
{
        char    str[100];
        int     i = -1;

        bzero(str, 100);
        scanf("%s", str);

        while (str[++i])
                printf("%c", str[i] - i);
        printf("\n");
}
```
```
level09@SnowCrash:/tmp$ gcc 1.c ; cat ~/token | ./a.out
f3iji1ju5yuevaus41q1afiuq
```
```
level09@SnowCrash:/tmp$ su flag09
Password: 
Don't forget to launch getflag !
flag09@SnowCrash:~$ getflag
Check flag.Here is your token : s5cAJpM8ev6XHw998pRWG728z
flag09@SnowCrash:~$
```
