Can RDP as Wade using gathered credentials
```bash
xfreerdp /cert-ignore /u:"Wade" /p:'parzival' /v:10.10.46.78
```

Gained another foothold as user `iis apppool\retro` from Wordpress using [](obsidian://open?vault=OSCP-Notes&file=Exploits%2FWeb%20Shells%2FWordpress%2FWP_Theme)  by logging in as user `Wade:parzival`