Part of [[Active Recon]]

Check own IP with:

``` bash
ip a s
```

We now know our subnet for ping sweep scan ([[Ping Sweeps]])

We will use -sn switch (No port scan, or ping sweep/ping scan) (different to -sN which is a Null scan)

``` bash
sudo nmap -sn [IP]/[mask]
```

We could also use netdiscover, which works via ARP requests:

``` bash
sudo netdiscover -i [interface] -r [IP]/[mask]
```

With nmap we may scan multiple IPs as

``` bash
sudo nmap -sn [IP] [IP]...
```

You may also build a list file, one IP per line, you may also add ranges.

``` bash
sudo nmap -sn -iL [path_to_file]
```

We may also use TCP Syn scans, by default in port 80, if open host responds with SYN/ACK if not  with RST, both allow to know if host is up.

``` bash
sudo nmap -sn -PS [IP]
```

We may specify ports with:

``` bash
sudo nmap -sn -PS[PORT] [IP]
```

Multiple ports separated by commas.

And a range with:

``` bash
sudo nmap -sn -PS[Pi]-[Pf] [IP]
```

If we remove -sn it will also do a port scan.

We can do an ACK scan with -PA. But it's not particullary good or reliable.

We may also use an ICMP Ping scan with -PE to send only echo requests, again not recomendable, just use a Syn scan.