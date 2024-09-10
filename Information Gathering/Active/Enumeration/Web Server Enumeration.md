[[Active Recon]] with [[Metasploit]]

A web server is software used to serve website data on the web.

Web servers utilize HTTP to facilitate the communication between clients and the web server
HTTP is an application layer protocol that utilizes TCP port 80 for communication
We can utilize auxilliary modules to enumerate the web server version, HTTP headers, brute forcing directories and more.

Some webservers: Apache, Nginx, Microsoft IIS


``` bash
service postgresql start && msfconsole
```

Set global rhosts with setg

Some http modules we may use:

auxiliary/scanner/http/http_version (remember to change SSL to the correct option)
auxiliary/scanner/http/http_header
auxiliary/scanner/http/robots_txt
auxiliary/scanner/http/dir_scanner
auxiliary/scanner/http/files_dir (you can specify extensions)
auxiliary/scanner/http/http_login
auxiliary/scanner/http/apache_userdir_enum

We can use curl to access specific directories without a browser

Consider reseeing the Apache Enum lab