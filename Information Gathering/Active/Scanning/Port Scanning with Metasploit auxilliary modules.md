Related to [[Active Recon]] and [[Metasploit]]

Auxilliary modules are used to perform functionality like scanning, discovery and fuzzing.

We can use them for both TCP and UDP port scans as well as enumerating info from services like FTP, SSH, HTTP etc.

Auxilliary modules can be used during the information gathering phase of a pentest as well as the post exploitation phase.

We can also use them for host discovery and port scanning on a different subnet after initial access.
whi
Search modules using the search command inside of metasploit (msfconsole)

Use a module with:

``` bash
use [pathtomodule]
```

See options with:

``` bash
show options
```

See options, like RHOSTS:

```bash
set RHOSTS [targetip]
```

Then execute the module using "run"

When you have a meterpreter session upgrgade it to shell and bash

``` bash
shell
/bin/bash -i
```

And now we can find the internal ip address for the internal network with ifconfig. Now we can scan the internal network with:

``` bash
run autoroute -s [IP_of_one_of_the_systems]
```

We can background sessions using backround and sessions commands

Now we can from our original mfsconsole run a portscan to the internal network usingg the portscan module after setting RHOSTS to the targets IP (in case of confusion check autoroutes created routes) and the port range to the correct one. This is a form of pivoting.