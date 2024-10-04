# Welcome to my "Cyborg" CTF walkthorugh!
You can find this CTF on https://tryhackme.com/

## Task 1: Deploy the machine
Deploy the machin and get a Target IP Address. I used a Kali virtual machine so I connected using OpenVPN.

## Task 2: Compromise the System
I started by performing a port scan on the host using Nmap. The -sC and -sV flags ensure that basic vulnerability detection scripts are run against the target and that the scan attempts to identify the versions of services running on open ports.

<img align="center" src="images/image1.png">

We can answer questions 1-3 with the results of our nmap scan.

Next we are going to use Gobuster :










