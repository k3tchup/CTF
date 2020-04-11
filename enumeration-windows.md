# Windows 

## Enumeration without credentials
### DNS zone transfer

	host -l domain.name dnsserver
	
	dig axfr domain.name @dnsserver
	
	dnsrecon -d domain.name -t axfr
	
### SMB Anonymous Shares

	smbclient -L //server
	
### Anonymous RPC

	rpcclient -U "" <host or IP>
	
	enumdomusers
	as well as other ones, help for commands

### LDAP

	ldapsearch -h <host or IP> -p 389 -x -b 'dc=example,dc=com'
	
### Enum4linux

	enum4linux -a <host or IP>
	
	
### ASREPRoast

Requires that you harvest a list of users first, from one of the above.

	GetNPUsers.py <domain_name>/ -usersfile <users_file> -format <AS_REP_responses_format [hashcat | john]> -outputfile <output_AS_REP_responses_file>
	