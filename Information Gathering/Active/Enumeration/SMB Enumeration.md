
SMB - Server Message Block, used for sharing files on a LAN.
Uses port 445 TCP by default, originally tho it used 139
SAMBA is the linux implementation of SMB and allows windows to access Linux shares and devices

We can use [[Metasploit]] auxilliary modules as [[Active Recon]] to enumerate SMB shares, version, users and perform brute-force attacks for authorization.

As usual instance msfconsole after instancing postgre, then you may create a SMB_ENUM workspace

For comodity we may set our target as a global variable

``` bash
setg RHOSTS [target]
```

We may use scanner/smb/smb_version

also: auxiliary/scanner/smb/smb_enumusers
and: auxiliary/scanner/smb/smb_enumshares
We may change ShowFiles to true as they may be useful

Then we can use auxiliary/scanner/smb/smb_login to bruteforce like in [[FTP Enumeration]]

``` bash
set SMBuser admin
set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords
```

Now we can use smbclient:

``` bash
smbclient -L //[IP]/ -U admin
```

It will ask for password, then print all shares
To access one:

``` bash
smbclient //[IP]/[share] -U admin
```

Once there we can list with ls, change directories with cd and download with get.

We may find the NetBios Samba name with

``` bash
nmblookup -A [IP]
```