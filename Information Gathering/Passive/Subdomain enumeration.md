Install in Kali:

``` bash
sudo apt-get install sublist3r
```

Using sublist3r

``` bash
sublist3r -d [root_domain_name]
```

Specify search engines with -e/--engines

``` bash
sublist3r -d [root_domain_name] --e google,yahoo
```

If google blocks requests you may use a VPN to bypass
