Relateed to [[Active Recon]]] and [[Metasploit]]

Typically on port 3306

auxiliary/scanner/mysql/mysql_version
auxiliary/scanner/mysql/mysql_login (bruteforcer, set speed, target IP, username file and password file: you could also set username to root, the password file could be /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt)
auxiliary/admin/mysql/mysql_enum (requires credentials)
auxiliary/admin/mysql/mysql_sql (Allows to run queries)
auxiliary/scanner/mysql/mysql_schemadump (services, loot, creds after running)
auxiliary/scanner/mysql/mysql_writable_dirs (DIR_LIST /usr/share/metasploit-framework/data/wordlists/directory.txt)

Connect to the db with:

``` bash
mysql [IP] -u [user] -p
```
