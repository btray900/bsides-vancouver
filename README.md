# bsides-vancouver
Walkthrough for Vulnhub VM Bsides - Vancouver


## netdiscover

Running netdiscover shows us the IP of the VM to be 192.168.56.102 provisioned on our host-only adapter.

![Alt text](./netdiscover.png?raw=true)


## nmap

Nmap identifies some intesting ports.

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




## root

<html><pre>
\(*_*)
  ( (>
  /  \
  </pre></html>
