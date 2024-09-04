Part of [[Active Recon]]

Check own IP with:

``` bash
ip a s
```

We now know our subnet for ping sweep scan

We will use -sn switch (No port scan, or ping sweep/ping scan) (different to -sN which is a Null scan)

``` bash
sudo nmap -sn [IP]/[mask]
```

We could also use netdiscover, which works via ARP requests:

``` bash
sudo netdiscover -i [interface] -r [IP]/[mask]
```

