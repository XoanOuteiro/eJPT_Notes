We can use a quick Syn stealth scan, part of [[Active Recon]]:

``` bash
sudo nmap -sS [IP]
```

``` bash
sudo nmap -sS -p- -T4 [IP]
```

To enable service detection:

``` bash
sudo nmap -sS -p- -T4 -sV [IP]
```

To add OS Detection:

``` bash
sudo nmap -sS -p- -T4 -sV -O [IP]
```

We could also use:

``` bash
sudo nmap -sS -p- -T4 -sV -O --osscan-guess [IP]
```

We can use version intensity to make it more accurate (and aggressive):

``` bash
sudo nmap -sS -p- -T4 -sV --version-intensity [NUM1-10] [IP]
```