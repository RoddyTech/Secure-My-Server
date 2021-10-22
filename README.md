<h1 align="center"> Secure My Server </h1> <br>
<p align="center">
    <img src="https://www.downloadclipart.net/large/database-server-transparent-png.png" width="450"/>
  </a>
</p>

<h1 align="center">Introduction:</h1>
<p> Most systems have some type of confidential data that needs to be protected. They hold financial information, personal photos, trade secrets, social security numbers, etc. To safeguard this data, we need to secure our important Linux systems. But how do we properly harden a Linux system? To protect against malicious actors who want to steal our precious data. If you are curious about that then this is the project for you. In this project, I will be detailing the process of hardening a Linux server. Deployed on my Local Network and i will be detailing the tools and configurations used to harden the server. For which you can apply to your very own server. </p>


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


## Secure SSH: :closed_lock_with_key:
SSH, or Secure Shell, is a remote administration protocol that allows users securely control and modify their remote servers over the Internet. And With it, you can feel risk-free and worry-free to login to a remote computer, to execute commands in another machine, and to move files between two separate machines over the same network. But their are ways to make SSH even more secure. And for my server i configured the following:

### Making a Backup:
First, before making major changes i back up the configuration file.

``` cp /etc/ssh/sshd_config ~/sshd_config_original ```

### Preventing Empty Passwords:
 ``` nano /etc/ssh/sshd_config ```
 
Find PermitEmptyPasswords. Uncomment it, and replace the yes value with no:

``` PermitEmptyPasswords no ```

### Preventing root login:
``` nano /etc/ssh/sshd_config ```

``` PermitRootLogin no ```

### Key Based Authentication:
uses asymmetric cryptography. That means there are two keys, different but mathematically related to each other. One is private and never sent across the network. The other is public and may be transferred across the network. Because the keys are related, they can be used to confirm identities—identities such as SSH authentication attempts.

You'll need to generate the key pair on the local SSH client computer and then transfer the public key across the network to the destination SSH server. In other words, the keys will identify you on your admin workstation. Once this configuration is in place, you are no longer challenged for a password when you establish an SSH connection.

### Steps:

### generating a key pair:

First you have to generate a keypair on your local machine:

``` ssh-keygen ```

> Note:
The keys are stored in your home directory in a hidden directory named .ssh, and the default key names are id_rsa (private key) and id_rsa.pub (public key).

### Copying Public key over:

``` ssh-copy-id -i ~/.ssh/tatu-key-ecdsa user@host ```

## Firewalls: :fire:


## Disable Vulnerable and unused services
Making sure that unsecure services like Telnet are disabled on the server.

### disabling Telnet: 
Cybersecurity Student enrolled at Penn Cybersecurity Bootcamp | With a passion for learning new techniques relating to Cyber Security ;{}


## Acknowledgments

Enabling a firewall on a server is good way control the traffick 
