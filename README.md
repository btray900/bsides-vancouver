# bsides-vancouver
Walkthrough for Vulnhub VM Bsides - Vancouver


## netdiscover

Running netdiscover shows us the IP of the VM to be 192.168.56.102 provisioned on our host-only adapter.

![Alt text](./netdiscover.png?raw=true)


## nmap

Nmap identifies some interesting ports.

![Alt text](./nmap.png?raw=true)


## dirbuster

My Kali install did not have an ftp client, otherwise I would have started with an attempt to login anonymously, which does work, and since there is a helpful file there, but I didn't check it until I was on the box. So I started with dirbuster and I usually try a big list and many extensions from the jump.

![Alt text](./dirbuster.png?raw=true)


## browser

Robots.txt gives us a URI to begin enumerating.

![Alt text](./robotsdottxt.png?raw=true)


## wpscan

The site is a WordPress install and enumerating the users gives us a starting point for brute force.

![Alt text](./wpscan-users.png?raw=true)

Using rockyou on 'john' cracks the wordpress login.

![Alt text](./wpscan-password.png?raw=true)


## Low privilege shell

I install a Wordpress PHP code then visit the site for a low priv shell in the msf multi/handler.

![Alt text](./plugin.png?raw=true)

![Alt text](./apache-shell.png?raw=true)


## Enumeration

So this is where you can find the FTP user list if you didn't find it enumerating, but /etc/passwd of course works. Also the wp-config.php has a password, and the password for john was known. None of these worked for any users. Brute forcing shows that most users use SSH keys, except anne.

![Alt text](./hydra.png?raw=true)

![Alt text](./anne-test.png?raw=true)



## hydra

Brute force on anne with rockyou cracks the anne password.

![Alt text](./anne-cracked.png?raw=true)


## sudo

Login as anne, sudo -l shows us we get mad root.

![Alt text](./anne-sudo.png?raw=true)


## root

<html><pre>
\(*_*)
  ( (>
  /  \
  </pre></html>
  
![Alt text](./root.png?raw=true)


## flag

cat flag.txt

![Alt text](./flag.png?raw=true)


## thanks!

Shout out to abatchy17 for the VM.
