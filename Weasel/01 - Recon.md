##### nmap
```bash
sudo nmap -sC -sV 10.10.225.137 -oA nmap -v -Pn
```
```
PORT     STATE SERVICE       VERSION
22/tcp   open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey: 
|   2048 2b:17:d8:8a:1e:8c:99:bc:5b:f5:3d:0a:5e:ff:5e:5e (RSA)
|   256 3c:c0:fd:b5:c1:57:ab:75:ac:81:10:ae:e2:98:12:0d (ECDSA)
|_  256 e9:f0:30:be:e6:cf:ef:fe:2d:14:21:a0:ac:45:7b:70 (ED25519)
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds?
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: DEV-DATASCI-JUP
|   NetBIOS_Domain_Name: DEV-DATASCI-JUP
|   NetBIOS_Computer_Name: DEV-DATASCI-JUP
|   DNS_Domain_Name: DEV-DATASCI-JUP
|   DNS_Computer_Name: DEV-DATASCI-JUP
|   Product_Version: 10.0.17763
|_  System_Time: 2024-08-19T13:24:28+00:00
|_ssl-date: 2024-08-19T13:24:36+00:00; 0s from scanner time.
| ssl-cert: Subject: commonName=DEV-DATASCI-JUP
| Issuer: commonName=DEV-DATASCI-JUP
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2024-08-18T13:23:47
| Not valid after:  2025-02-17T13:23:47
| MD5:   5661:3d67:205f:2c82:a6c5:e6b7:00d2:f80a
|_SHA-1: 7c8f:7c36:bbac:c212:cd18:d32a:4b14:b519:72be:7d12
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2024-08-19T13:24:29
|_  start_date: N/A
```

```bash
smbclient -N -L \\10.10.225.137
```
![[Pasted image 20240819172641.png]]

Running an all port scan revealed a webserver running on port `8888` 
Navigating to http://10.10.225.137:8888/ shows that it is a log in page for Jupyter notebook
![[Pasted image 20240819173447.png]]

Connecting to `/datasci-team` SMB share, downloaded all the files
![[Pasted image 20240819173515.png]]

`/misc` folder contained a file `jupyter-token.txt`. Will use this token to log in
`067470c5ddsadc54153ghfjd817d15b5d5f5341e56b0dsad78a`
