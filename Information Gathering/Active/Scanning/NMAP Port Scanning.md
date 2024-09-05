Part of [[Active Recon]]

Default nmap scan:

``` bash
sudo nmap [IP]
```

Its a SYN scan on most common ports, windows will tipically block ICMP (Ping) requests so we should use:

``` bash
sudo nmap -Pn [IP]
```

This way we dont check if the host is up.

To scan all posible ports we could use:

``` bash
sudo nmap -Pn -p- [IP]
```

To scan only one port:

``` bash
sudo nmap -Pn -p[Num] [IP]
```

For many ports, like 80 and 443:

``` bash
sudo nmap -Pn -p80,443 [IP]
```

For a port range:

``` bash
sudo nmap -Pn -p[initial]-[final] [IP]
```

For a fast scan (most common 1000 ports)

``` bash
sudo nmap -Pn -F [IP]
```

For a UDP port scan:

``` bash
sudo nmap -Pn -sU [IP]
```

For a TCP Connect scan:

``` bash
sudo nmap -Pn -sT [IP]
```

To add verbose to any scan -v, -vv, -vvv

For a service detection scan (See [[NMAP Service version and OS detection]]):

``` bash
sudo nmap -Pn -sV [IP]
```

(could also add -F for a faster scan)

Operating system detection (not always conclusive) (See [[NMAP Service version and OS detection]]):

``` bash
sudo nmap -Pn -O [IP]
```

(could also add -F and -sV)

To run nmap scripts use -sC flag. (Check [[NMAP Scripting Engine]])

The agressive scan is used via -A, its similar to -F with -sC:

``` bash
sudo nmap -Pn -A
```

Timing templates can be used with -T to make scans faster or slower, the higher the number the faster the scan, they also have alias names: paranoid 0, sneaky 1, polite 2, normal 3, aggressive 4, insane 5. Use slower ones to avoid IDSs. NMAP also attempts to adapt its speed if you dont specify it based on the network structure. See [[Firewall Detection and IDS Evation]] and [[NMAP Scan optimization]]

To output results into a file we may use:

- -oN text.txt = Plaintext
- -oX text.xm = For XML format

Check [[NMAP Output Formats]]