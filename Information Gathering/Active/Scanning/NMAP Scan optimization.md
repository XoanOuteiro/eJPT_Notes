Related to [[NMAP Port Scanning]], [[NMAP Host Discovery]] and [[Active Recon]]

We can choose speeds generally with -T<0-5> where higher means faster.
We can use --scan-delay and --host-timeout

--host-timeout allows nmap to drop a target if it doesnt respond after a certain time:

``` bash
nmap -Pn -sS -F --host-timeout 5s [IP]/24
```

Here we were doing a fast 100 port scans where if after 5 seconds a host doesnt respond it will be dropped.

Its not recommended to set host timeout to a very small value as we may miss real hosts.

With --scan-delay we can specify an ammount of time to wait between packets

``` bash
nmap -Pn -sS -F --scan-delay 5s [IP]/24
```
