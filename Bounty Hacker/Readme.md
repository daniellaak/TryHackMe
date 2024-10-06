# Welcome to my "Bounty Hacker" CTF walkthorugh!
You can find this CTF on https://tryhackme.com/

## Deploy the machine
Deploy the machin and get a Target IP Address. I used a Kali virtual machine so I connected using OpenVPN.

## Find open ports on the machine

I started by performing a port scan on the host using Nmap. The -sC and -sV flags ensure that basic vulnerability detection scripts are run against the target and that the scan attempts to identify the versions of services running on open ports.
<br><br>

<img align="center" src="Images/1.png">
<br>

We found 3 open ports: 21 (ftp), 22 (ssh) and port 80 (http)
We see that anonymous access is available on the FTP service.
Let’s try logging in on the ftp service:

<br>
<img align="center" src="Images/2.png">
<br>
We discovered task.txt file on it and a locks.txt file
<br><br>

<img align="center" src="Images/3.png">

## Who wrote the task list?

We can see that lin has written the task file.
<br><br>

<img align="center" src="Images/4.png">
<br><br>

<img align="center" src="Images/5.png">

## What service can you bruteforce with the text file found?
We can bruteforce to the ssh server since we have a user and a possible passwords list.
Let's use hydra:

<img align="center" src="Images/6.png">

## User Flag

We've found a password! Now, we can connect via ssh and get yhe user flag:

<img align="center" src="Images/7.png">

## Root Flag -Privilege Escalation

I used the command sudo -l to identify which files run as root.
We’ve discovered that the /bin/tar command can be executed with root privileges. This is a potential privilege escalation vector we can exploit!
For more details on this vulnerability, I found useful information at the following source: https://gtfobins.github.io/gtfobins/tar/
<br>
<img align="center" src="Images/9.png">
<br>

<img align="center" src="Images/8.png">
<br>

## Thank you for taking the time to read my walkthrough!

