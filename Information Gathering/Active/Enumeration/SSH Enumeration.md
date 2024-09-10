
[[Active Recon]] with [[Metasploit]]

Secure Shell is a protocol for remote connections to devices

Commonly  TCP port 22

Modules to use:

auxiliary/scanner/ssh/ssh_version
auxiliary/scanner/ssh/ssh_login or auxiliary/scanner/ssh/ssh_login_pubkey
(depends on service config)
(USER_FILE /usr/share/metasploit-framerwork/data/wordlists/common_users.txt
PASS_FILE /usr/share/metasploit-framework/data/wordlists/common_passwords.txt)
auxiliary/scanner/ssh/ssh_enumusers
