Using gathered credentials for `skyfuck`
```bash
ssh skyfuck@10.10.94.13
```

Found `user.txt` in /home/merlin directory

Under skyfuck's home directory
- credential.pgp
- tryhackme.asc

Using this website for cracking passwords with [JtR](https://ed4m4s.blog/password-attacks/john-the-ripper)

```bash
gpg2john tryhackme.asc > hash
```
- Crack the hash with john
```bash
john --format=gpg --wordlist=/usr/share/wordlists/rockyou.txt hash
```
![[Pasted image 20240823183747.png]]
- import `tryhackme.asc:alexandru`
```bash
gpg --import tryhackme.asc
```
- decrypt `credential.pgp` file
```bash
gpg --decrypt credential.pgp
```
![[Pasted image 20240823183934.png]]
`merlin:asuyusdoiuqoilkda312j31k2j123j1g23g12k3g12kj3gk12jg3k12j3kj123j`

SSH as user `merlin`

