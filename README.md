<h1 align="center"> Secure My Server </h1> <br>
<p align="center">
  <a href="https://gitpoint.co/">
    <img alt="GitPoint" title="GitPoint" src="https://cdn.freebiesupply.com/logos/thumbs/2x/ubuntu-icon-logo.png" width="450">
  </a>
</p>

<h1 align="center">Introduction:</h1>



<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- Automatic Updates
- Users
- Secure SSH
- Firewalls
- Disable Vulnerable and Unused services
- Isolation(Docker)


## Automatic Updates:

<p align="center">
  <img src = "https://miro.medium.com/max/800/1*Tob4uNPGpWpoFMyW40z8Tw.png" width=400>
</p>

### Why Automatic Updates:
- Enabling Automatic updates help keep a server upto date with the latest patches and software updates. Which will prevent outdated vulnerable applications/software on the server from being expolited by malicious actors. Which can result in malware being installed into the system which can result in data loss, stolen sensitive data, deletion, And etc.

- A way to enable Automatic Updates is to make uses of "Cronjobs" which are scheduled automatic jobs done by the server itself without user intervention. Jobs may include backups, creating reports, cleanup tasks, <b>automatic updates</b>, and more. And for my server I created a cronjob that does the following:

### This cronjob will update the server every Friday at 12 PM:
``` 0 0 * * FRI apt-get update && apt-get upgrade ```


## Users: :exclamation:

Logging in as root is bad practice it leaves the server open to accidental deletions and other mishapes caused by common user errors. So it is absolutely vital to create a User Account with limited privledges. And For my server I did the following:

### Creating User
![](images/adding-user.PNG)


### Adding user to sudoer group
![](images/adding-user-to-sudo.PNG)

These images show the successful creation of a user with now limited privileges.
And now that we have a user with limited privileges the server is more secure.



## Secure SSH



## Firewalls


## Disable Vulnerable and unused services
Making sure that unsecure services like Telnet are disabled on the server.

### disabling Telnet: 
Cybersecurity Student enrolled at Penn Cybersecurity Bootcamp | With a passion for learning new techniques relating to Cyber Security ;{}


## Acknowledgments

Enabling a firewall on a server is good way control the traffick 
