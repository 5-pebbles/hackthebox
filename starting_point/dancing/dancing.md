# Dancing

> Very Easy


## Task #1

What does the 3-letter acronym SMB stand for?

> server message block


## Task #2

What port does SMB use to operate at?

```fish
~/h/s/dancing ❯ nmap 10.129.243.28                    11/07/24
Starting Nmap 7.95 ( https://nmap.org ) at 2024-07-11 15:33 EDT
Nmap scan report for 10.129.243.28
Host is up (0.055s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5985/tcp open  wsman

Nmap done: 1 IP address (1 host up) scanned in 3.02 seconds
```

Nope Wikipedia it is...

> 445


## Task #3

What is the service name for port 445 that came up in our Nmap scan?

> microsoft-ds


## Task #4

What is the 'flag' or 'switch' that we can use with the smbclient utility to 'list' the available shares on Dancing?

I don't know what smbclient is... `sudo dnf install smbclient` nope not it...

I had to look it up -_- `sudo dnf install samba-client`

```fish
~/h/s/dancing ❯ smbclient --help | grep "list"        11/07/24
  -L, --list=HOST                              Get a list of shares available
```

> -L


## Task #5

How many shares are there on Dancing?

```fish
~/h/s/dancing ❯ smbclient -L 10.129.243.28            11/07/24
Password for [SAMBA\ghostbird]:

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	WorkShares      Disk      
SMB1 disabled -- no workgroup available
```

> 4


## Task #6

What is the name of the share we are able to access in the end with a blank password?

```fish
~/h/s/dancing ❯ smbclient \\\\10.129.243.28\\ADMIN\$  11/07/24
Password for [SAMBA\ghostbird]:
tree connect failed: NT_STATUS_ACCESS_DENIED
```

you can tell this is a windows tool by the stupid backslashes...

I mean you can access `WorkShares` and `IPC$` but `IPC$` is not very useful... just like windows ;)

> WorkShares


## Task #7

What is the command we can use within the SMB shell to download the files we find?

> get

who would have guessed...


## Submit Flag

Submit root flag

Ok I know that's the goal and all, but I still want to read Amy's work notes first:

```fish
~/h/s/dancing ❯ cat worknotes.txt                     11/07/24
- start apache server on the linux machine
- secure the ftp server
- setup winrm on dancing ⏎     
```

and here is the flag:

```fish
~/h/s/dancing ❯ cat flag.txt                          11/07/24
5f61c10dffbc77a704d76016a22f1664⏎   
```

> 5f61c10dffbc77a704d76016a22f1664
