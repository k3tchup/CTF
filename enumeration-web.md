# Web enumeration

### whatweb
Identifies frameworks, web servers, etc.
  
    whatweb http://host

### Nikto
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
### gobuster for vhost enum
    gobuster vhost -u http://host -w /usr/share/wordlists/vhosts/combined.txt -
  
### wafw00f
Identifies various WAFs that may run in front of the site

    wafw00f <http://host>
  
