#linux 

### What is SSH?
SSH stands for Secure Shell or Secure Socket Shell, and is a network protocol that gives users, particularly system administrators, a secure way to access a computer over an unsecured network.

SSH also refers to the suite of utilities that implement the SSH Protocol.

SSH provides remote authentication via a password or a public key, as well as encrypted communication between two computers over an open network, such as the internet.

Commonly, SSH is used in order to log in into a remote computer, and execute various commands, such as moving files from one computer to another.

SSH uses a client-server model. The person who connects to remote computer is using an SSH Client, while the remote computer is using an SSH Server.

By default, an SSH Server listens to port 22 (TCP).

### How does SSH work?
The most basic use of SSH is to connect to a remote host for a terminal session. The syntax of that command is the following:

```bash
ssh username@sshserver.example.com
```

This command initiates an attempt to connect to the server named `sshserver.example.com`, using the user id `username`.

If this is the first time negotiating a connection between the local host and the server, the user will be prompted with the remote host's public key fingerprint and prompted to connect, despire there having been no prior connection:

```bash
The authenticity of host 'sample.ssh.com' cannot be established.  
 DSA key fingerprint is 01:23:45:67:89:ab:cd:ef:ff:fe:dc:ba:98:76:54:32:10.  
 Are you sure you want to continue connecting (yes/no)?
```

### What is SSH used for?
Present in all data centers, SSH ships by default with every Unix, LInux, and Mac server.

In addition to creating a secure channel between local and remote computers, SSH is used to manage routers, server hardware, virtualization platforms, operating systems, and inside system management and file transfer applications.

SSH keys can be integrated in backup scripts in order to automate access to remote servers.

SSH is designed to be convenient, providing single sign-on (SSO) so that users can move between their accounts without typing a password each time.

### SSH Capabilities
1. secure remote access to SSH-enabled networks
2. secure file transfers
3. secure executions of commands on remote devices
4. secure management of network infrastructure components

### Key Exchange
Once a connection is established, the client and the server use what is known as a `Diffie-Hellman Key Exchange Algorithm` to create a `symmetrical key`.

This algorithm allows both the client and the server to arrive at a shared encryption key which will be used henceforth to encrypt the entire communication sesssion.


---
https://www.techtarget.com/searchsecurity/definition/Secure-Shell
https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work
https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange