Related to [[Active Recon]]

We can see if port are filtered or unfiltered using ACK scans (-sA) and port specifications (-p)

To avoid firewalls we may fragment packets with -f (NOT -F):

```
sudo nmap -Pn -sS -sV -f [IP]
```

We can use --mtu (minimun transmission unit size) to indicate the fragmentation size:

``` bash
sudo nmap -sS -sV -sC -p- -T4 -f --mtu 8 [IP]
```

(The minimun is 8)


We could also use spoofing/Decoy Ip addresses, for example using the gateway IP, imagine an IP that is 101.4.23.4, the gateway would be 101.4.23.1

``` bash
sudo nmap -Pn -sS -sV -p[port],[port] -f --data-length 200 -D 101.4.23.1 [IP]
```

Here we are setting data length to 200, using fragmentation AND using a decoy ip to make the scan seem as if it came from the gateway. We can use more decoy IPs with commas.

We can also use -g to specify source port.

We can use -n to disable DNS resolution.

