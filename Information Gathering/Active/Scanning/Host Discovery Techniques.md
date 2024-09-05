Related to [[Network Mapping]] and [[NMAP Host Discovery]]

- [[Ping Sweeps]]: ICMP Echo Requests to a range of IP addresses to identify live hosts, often misses Windows Hosts.
- ARP Scanning Using address resolution protocol (ARP) requests to identify hosts on a local network. Effective in discovering hosts within the same broadcast domain.
- TCP SYN Ping (Half-Open Scan): Sending TCP SYN packets to a specific port to check if a host is alive to see if it replies with a TCP SYN-ACK. (See [[Transport Layer]])


ICMP Ping:

- Pros: Widely supported, quick
- Cons: Some firewalls may block ICMP traffic. Can also be easily detected

TCP SYN Ping:

- Pros: Is stealthier than ICMP and may bypass firewalls.
- Cons Some hosts may not respond to TCP Syn requests and results may be affected by firewalls

