Related to [[Active Recon]] and [[Metasploit]]

FTP - File Transfer Protocol

Tipically in port 21 TCP

Uses authorization and can be bruteforced.

As with all metasploit, start by launching postgresql

``` bash
search ftp
```

We can use auxiliary/scanner/ftp/ftp_version

Then we can bruteforce: auxiliary/scanner/ftp/ftp_login
It needs a username or userfile and password or passwordfile
We can use metasploits own wordlists

``` bash
set USER_FILE /usr/share/metasploit-framework/data/wordlists/common_users.txt
set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
```

Once we have a username and password we can use metasploit to auth:

``` bash
ftp [IP] 
```

If the server is not reachable we may wait as the bruteforce may have acted as a bruteforce.
We could also use the anonymous login module to see if ftp is accessible as an anonymous user:
/auxiliary/scanner/ftp/anonymous

Once we are logged in we can list ftp directory with ls, and download the files with get, exit using the exit command.