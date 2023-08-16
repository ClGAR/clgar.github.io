# Keeper

![Untitled](/keeper/Untitled.png)

Keeper is an easy-level HackTheBox laboratory machine running Linux. It involves various tasks, including identifying a standard password, exploring password transmission through an open communication channel, encountering an untimely change, and exploiting a vulnerability in Keepass.

# Nmap

```bash
Command:- nmap -A -T4 -p- 10.129.208.9
```

```bash

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 3539d439404b1f6186dd7c37bb4b989e (ECDSA)
|_  256 1ae972be8bb105d5effedd80d8efc066 (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.93%E=4%D=8/16%OT=22%CT=1%CU=33068%PV=Y%DS=2%DC=T%G=Y%TM=64DCC1D
OS:5%P=x86_64-pc-linux-gnu)SEQ(SP=104%GCD=1%ISR=106%TI=Z%CI=Z%II=I%TS=A)SEQ
OS:(SP=104%GCD=1%ISR=106%TI=Z%CI=Z%TS=A)OPS(O1=M569ST11NW7%O2=M569ST11NW7%O
OS:3=M569NNT11NW7%O4=M569ST11NW7%O5=M569ST11NW7%O6=M569ST11)WIN(W1=FE88%W2=
OS:FE88%W3=FE88%W4=FE88%W5=FE88%W6=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M569NNSN
OS:W7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%D
OS:F=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O
OS:=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=N)U1(R=Y%DF=N
OS:%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%C
OS:D=S)

Network Distance: 2 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 110/tcp)
HOP RTT       ADDRESS
1   351.44 ms 10.10.16.1 (10.10.16.1)
2   158.05 ms 10.129.208.9 (10.129.208.9)

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1125.60 seconds
```



# User Flag

We have two Port:

```bash
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 3539d439404b1f6186dd7c37bb4b989e (ECDSA)
|_  256 1ae972be8bb105d5effedd80d8efc066 (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
```

While accessing the Port 80 we get an hostname.

Let’s add the hostname under the hosts

![Untitled](/keeper/Untitled%201.png)

```bash
sudo nano /etc/hosts

<Ip address> keeper.htb tickets.keeper.htb
```

When I visit the URL, a login page appears. However, we can use the default username and password

![Untitled](/keeper/Untitled%202.png)

![Untitled](/keeper/Untitled%203.png)

Click on the lnorgaard

![Untitled](/keeper/Untitled%204.png)

We get Unix Login access which is ssh access.

![Untitled](/keeper/Untitled%205.png)

Let’s login via ssh.

![Untitled](/keeper/Untitled%206.png)

# Root Flag

We get the zip file in the home directory. Let’s extract the zip.

![Untitled](/keeper/Untitled%207.png)

First Let’s send the file into our local directory.

We get two files.

![Untitled](/keeper/Untitled%208.png)

If we search recent blogs regaring keepass we get to know we can get plain text password by using dotnet command, however there is a script available for linux to get the plain password.

```jsx
https://github.com/CMEPW/keepass-dump-masterkey
```

To get the password we can use the following command

```bash
python3 poc.py -d KeePassDumpFull.dmp
```

We get the following possible password.

![Untitled](/keeper/Untitled%209.png)

Let’s search on google to find possible password

![Untitled](/keeper/Untitled%2010.png)

![Untitled](/keeper/Untitled%2011.png)

let’s try with this password:-

```jsx
rødgrød med fløde
```

let’s use keepass and select the database which we found under the zip.

![Untitled](/keeper/Untitled%2012.png)

And try the above password.

We get access of the database.

Copy whole ssh-rsa, let’s use add import whole ssh-rsa file in puttygen.

![Untitled](/keeper/Untitled%2013.png)

I have copied whole text into a file and save it.

Imported the file into puttygen and generate a ssh-key.

![Untitled](/keeper/Untitled%2014.png)

I have exported the key now will use rsa key in ssh to get root access.

```bash
chmod 600 root_rsa
ssh -i root_rsa root@keeper.htb
```

We got the root access

![Untitled](/keeper/Untitled%2015.png)

## Conclusion

The Keeper HackTheBox machine provided an opportunity to explore various aspects of penetration testing, including port scanning, identifying vulnerabilities, exploiting Keepass vulnerabilities, and escalating privileges to root.

This writeup offers a comprehensive overview of the steps taken to conquer this machine, serving as a valuable reference for those interested in the field of ethical hacking and penetration testing.

Happy hacking!