# Fawn

> Very Easy

## Task #1

What does the 3-letter acronym FTP stand for?

> file transfer protocol

## Task #2

Which port does the FTP service listen on usually?

IDK let's find out:

```fish
~ ❯ nmap 10.129.238.230                               11/07/24
Starting Nmap 7.95 ( https://nmap.org ) at 2024-07-11 13:08 EDT
Nmap scan report for 10.129.238.230
Host is up (0.056s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE
21/tcp open  ftp

Nmap done: 1 IP address (1 host up) scanned in 1.00 seconds
```

> 21

## Task #3

What acronym is used for the version of FTP secured by running over the SSH protocol?

> sftp

The placeholder attribute was ***p which makes it really easy...

## Task #4

What is the command we can use to send an ICMP echo request to test our connection to the target?

> ping

## Task #5

From your scans, what version is FTP running on the target?

```fish
~ ❯ nmap -sV 10.129.238.230                           11/07/24
Starting Nmap 7.95 ( https://nmap.org ) at 2024-07-11 13:15 EDT
Nmap scan report for 10.129.238.230
Host is up (0.055s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.40 seconds
```

> vsftpd 3.0.3

## Task #6

From your scans, what OS type is running on the target?

The placeholder attribute is ***x so good luck getting this one wrong even without nmap...

> Unix

## Task #7

What is the command we need to run in order to display the 'ftp' client help menu?

I don't have ftp installed so lets fix that first `sudo dnf install ftp` then let me guess:

```fish
~ ❯ ftp -h                                            11/07/24

	Usage: { ftp | pftp } [-Apinegvtd] [hostname]
	  -A: enable active mode
	  -p: enable passive mode (default for ftp and pftp)
	  -i: turn off prompting during mget
	  -n: inhibit auto-login
	  -e: disable readline support, if present
	  -g: disable filename globbing
	  -m: don't force data channel interface to the same as control channel
	  -v: verbose mode
	  -t: enable packet tracing [nonfunctional]
	  -d: enable debugging

```

> ftp -h

## Task #8

What is username that is used over FTP when you want to log in without having an account?

> Anonymous

Thanks, Stack Overflow ;)

## Task #9

What is the response code we get for the FTP message 'Login successful'?

Let's find out:

```fish
~ ❯ ftp 10.129.238.230                                11/07/24
Connected to 10.129.238.230 (10.129.238.230).
220 (vsFTPd 3.0.3)
Name (10.129.238.230:ghostbird): Anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>
```

> 230

## Task #10

There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.

> ls

I'm not a toddler...

## Task #11

What is the command used to download the file we found on the FTP server?

How should I know:

```fish
ftp> help
Commands may be abbreviated.  Commands are:

!		debug		mdir		sendport	site
$		dir		mget		put		size
account		disconnect	mkdir		pwd		status
append		exit		mls		quit		struct
ascii		form		mode		quote		system
bell		get		modtime		recv		sunique
binary		glob		mput		reget		tenex
bye		hash		newer		rstatus		tick
case		help		nmap		rhelp		trace
cd		idle		nlist		rename		type
cdup		image		ntrans		reset		user
chmod		lcd		open		restart		umask
close		ls		prompt		rmdir		verbose
cr		macdef		passive		runique		?
delete		mdelete		proxy		send
```

> get

## Submit Flag

Submit root flag

```fish
ftp> get flag.txt
local: flag.txt remote: flag.txt
227 Entering Passive Mode (10,129,238,230,181,195).
150 Opening BINARY mode data connection for flag.txt (32 bytes).
226 Transfer complete.
32 bytes received in 8.1e-05 secs (395.06 Kbytes/sec)
ftp> exit
221 Goodbye.
~/h/s/fawn ❯ cat flag.txt                             11/07/24
035db21c881520061c53e0536e44f815⏎
```

> 035db21c881520061c53e0536e44f815
