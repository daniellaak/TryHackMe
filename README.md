# Welcome to my "Cyborg" CTF walkthorugh!
You can find this CTF on https://tryhackme.com/

## Task 1: Deploy the machine
Deploy the machin and get a Target IP Address. I used a Kali virtual machine so I connected using OpenVPN.

## Task 2: Compromise the System
I started by performing a port scan on the host using Nmap. The -sC and -sV flags ensure that basic vulnerability detection scripts are run against the target and that the scan attempts to identify the versions of services running on open ports.


<img align="center" src="images/image1.png">


We can answer questions 1-3 with the results of our nmap scan.

Let’s check out the web server to see what’s there.


<img align="center" src="images/image3.png">


Next we are going to use Gobuster :


<img align="center" src="images/image2.png">


The two notable directories appear to be /admin and /etc. Let’s begin with /etc, where we found a directory named "squid."
Inside, we discovered a passwd file and a configuration file. The config file includes some authentication rules, while the passwd file contains a username and a password hash.


<img align="center" src="images/image5.png">


I craked the hash using john following the above command:

<img align="center" src="images/image6.png">

## User Flag

We've found a password! Now, heading back to the admin section, there's an option to download an archive file by clicking one of the links in the header. 
You can download the archive.tar file by running: "tar -xvf archive.tar"

<img align="center" src="images/image7.png">

We've just discovered that these files are part of a backup created using Borg. we can install Borg and extract the files.
We can use the following command to do this:

<img align="center" src="images/image13.png">


We will be prompted to enter the password we cracked earlier. Afterward, if we check the home directory, we’ll see that a new directory has been created.
This new directory holds Alex's home directory. The Desktop folder contains a note congratulating us on our progress, while the Documents folder contains login credentials.


<img align="center" src="images/image10.png">

Let’s use these credentials to access the target via SSH.


<img align="center" src="images/image11.png">

 After logging in, we can list the files in this user’s directory and collect the user flag.


<img align="center" src="images/image14.png">

## Root Flag -Privilege Escalation

I used the command sudo -l to identify which files run as root. The file is owned by Alex, allowing us to freely edit its contents to gain root access.
Once you are root tou can access the root.txt.
Run the following commands to become the root user:



<img align="center" src="images/image12.png">

## Thank you for taking the time to read my walkthrough!













