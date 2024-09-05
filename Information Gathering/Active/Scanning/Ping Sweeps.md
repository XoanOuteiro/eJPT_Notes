The ping command is meant to be used to see if a host is alive/reachable

Part of [[Active Recon]]

Works by sending one or more special ICMP packet (Type 8 - Echo request) to a host.
If the destination replies with an echo reply (Type 0) packet then its alive.


ICMP Echo request: TYPE: 8, CODE: 0
ICMP Echo reply: TYPE: 0, CODE: 0

We may use simply:

``` bash
ping [IP]
```

But we may also send just one packet

``` bash
ping -c 1 [IP]
```

On Windows use -n instead of -c

To tell ping to scan the whole subnet chage the last digit of local IP to 0, for example if IP is 10.10.20.3:

``` bash
ping -c 1 10.10.20.0
```

You may need to enable broadcast:

``` bash
ping -b -c 1 10.10.20.0
```

We may also use fping:

``` bash
fping -a -g 10.10.20.0/[mask]
```

-a shows alive targets and -g generates a target list

You can also use -s to spoof origin IP address for stealth.

You can also use fping for a single target using only -a

If we target is unreachable we could use -Pn to avoid host discovery with nmap (see  [[NMAP Host Discovery]], [[NMAP Port Scanning]])

``` bash
nmap -sn [IP]
```

Would also fail as it is a ping sweep