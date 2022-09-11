# Aragog

# Aragog

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled.png)

## Nmap:-

**sudo nmap -A -T4 -p- [Ip-addr]**

```html
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 48:df:48:37:25:94:c4:74:6b:2c:62:73:bf:b4:9f:a9 (RSA)
|   256 1e:34:18:17:5e:17:95:8f:70:2f:80:a6:d5:b4:17:3e (ECDSA)
|_  256 3e:79:5f:55:55:3b:12:75:96:b4:3e:e3:83:7a:54:94 (ED25519)
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
|_http-title: Site doesn't have a title (text/html).
|_http-server-header: Apache/2.4.38 (Debian)
```

## **Enumeration:-**

sudo gobuster dir -w /usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt -u [http://10.0.2.6](http://10.0.2.6/)

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%201.png)

## /Blog

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%202.png)

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%203.png)

Which means there are some plugins which can be possibly exploitable.

## Wordpress Scan:-

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%204.png)

## Exploiting wp-file-manager:-

WP-file-manager wordpress plugin (<6.9) vulnerable to unauthenticated arbitary file upload resulting in full compromise of the system.

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%205.png)

## Reverse Shell:-

[http://10.0.2.6/blog/wp-content/plugins/wp-file-manager/lib/files/abc.php](http://10.0.2.6/blog/wp-content/plugins/wp-file-manager/lib/files/abc.php)

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%206.png)

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%207.png)

Local privilege escalation

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%208.png)

Let’s Login into mysql

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%209.png)

Cracking Hash:-

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%2010.png)

Let’s ssh Login into hagrid98.

**privilege escalation:-**

monitor all process using pspy.

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%2011.png)

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%2012.png)

File is editable by hagrid98 which later executed as root.

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%2013.png)

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%2014.png)

**./bash -p**

We become root.

![Untitled](/aragog%20f70d02f6e3b84b98826e52722a78ed2f/Untitled%2015.png)

