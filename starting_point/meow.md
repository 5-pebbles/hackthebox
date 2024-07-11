# Meow

> Very Easy

## CONNECT

I didn't have openvpn installed yet: `sudo dnf install openvpn` don't you love it when the package name makes sense.

I don't know how to use this but let me guess `sudo openvpn my_file.ovpn` ... `ping 10.129.15.203` alright boys were in ;)

## Task #1

What does the acronym VM stand for?

> virtual machine

## Task #2

What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell. 

> terminal

## Task #3

What service do we use to form our VPN connection into HTB labs? 

> openvpn

## Task #4

What tool do we use to test our connection to the target with an ICMP echo request?

> ping

## Task #5

What is the name of the most common tool for finding open ports on a target? 

> nmap

## Task #6

What service do we identify on port 23/tcp during our scans? 

> telnet

Thanks, Wikipedia!

I don't have telnet installed (who would) `sudo dnf install telnet` then:

```
~ ❯ telnet -h                                         11/07/24
telnet: invalid option -- 'h'
Usage: telnet [-4] [-6] [-8] [-E] [-L] [-S tos] [-a] [-c] [-d] [-e char] [-l user]
   [-n tracefile] [-b hostalias ] [-r] 
 [host-name [port]]
```

not what I was trying to do, but it works...

`telnet 10.129.15.203`

## Task #7

What username is able to log into the target over telnet with a blank password?

> root

who would have guessed...

## Submit Flag

Submit root flag

```fish
root@Meow:~# ls
flag.txt  snap
root@Meow:~# cat flag.txt
b40abdfe23665f766f9c61ecba8a4c19
```

> b40abdfe23665f766f9c61ecba8a4c19
