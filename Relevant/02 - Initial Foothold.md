Tried a lot in different ways to gain initial foothold using EternalBlue and whatnot

There are 2 IIS server ports open on port 80, 49663.

The network share `nt4wrksv` can be accessed via `http://10.10.250.166:49663/nt4wrksv/`

Using the access we have to the SMB share on the device, uploaded `shell.aspx` generated using msfvenom and ran it to gain a reverse shell as \
![[Pasted image 20240817114119.png]]

