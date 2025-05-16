```bash
#!/bin/bash

nmap -sn -n -PE -T5 192.168.1.0/24 | grep "^Nmap scan report for" | awk '{print $5}' > targets.txt
xargs -P 40 -I{} sudo nmap -sS -F -T5 -Pn -n -oG nmap-{} {} < targets.txt
```
