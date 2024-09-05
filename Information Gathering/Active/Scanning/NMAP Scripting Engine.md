Part of [[Active Recon]]

Or NSE, its a tool of nmap that allows to automate different tasks.

List all scripts with

``` bash
ls -la /usr/share/nmap/scripts/
```

They are made in Lua and use .nse extension, searh among all scripts with | grep

Default script scan is with -sC

``` bash
sudo nmap -sS -sV -sC -p- -T4 [IP]
```

We can run a specific script with

``` bash
sudo nmap  --script=[name]
```

so:

``` bash
sudo nmap -sS -sV --script=[name] -p- -T4 [IP]
```

we can also limit port to the one with the specific port which has the service related to the script.

To use many scripts use , between names. Scripts like ftp-anon are very useful.