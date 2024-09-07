- -oN text.txt = Plaintext
- -oX text.xm = For XML format
- -oS file.txt = script kiddie format
- -oG file.txt = Greppable format
- -oA (basename) = Three major formats at once

We may also use -v,-vv,-vvv for verbosity and --reason

To use xml [[Metasploit]] output:

``` bash
service postgresql start
msfconsole
workspace -a pentest_1
db_import file.xml
```

Now using hosts will display the hosts we have scanned with their information, same as using services.

Now we can run nmap commands from db_nmap to automatically save them to the imported database.