# Web enumeration

## Nikto
  nikto -h <host or IP>

## dirb or dirbuster

### dirbuster
I typically:
* use /usr/share/wordlists/dirb/big.txt
* disable recursion for initial pass
* set about 70 threads
* add an extension (PHP, JSP, etc) for whatever the site runs

### dirb

  dirb http://host /usr/share/wordlists/dirb/big.txt -X .php
  
  
