#linux #LPIC-1 

### Hypervisors
Virtualization is a technology that allows for a software platform, called a `hypervisor`, to run processes that contain a fully emulated computer system.

The hypervisor is responsible for managing the physical hardware's resources that can be used by individual virtual machines.

These virtual machines are called `guests` of the hypervisor.

Commonly used hypervisors for Linux include:
1. Xen (Type-1)
2. KVM (Kernel Virtual Machine) (Type-1 & Type-2)
3. VirtualBox (Type-2)

A Type-1 hypervisor does not require an underlying operating system, while a Type-2 does.

The process of moving a virtual machine from one hypervisor to another is called a `migration`. Some migrations can only be done while the hypervisor is shut down, and others can be performed while the hypervisor is still running, these being called `live migrations`.

### Virtual Machines
There are three types of VMs (virtual machines):
1. Fully Virtualized
2. Paravirtualized
3. Hybrid

There are two main types of disk images that a VM can use:
1. COW (Copy on Write)
2. RAW (full disk)

Since VMs are just files on a hypervisor, it's easy to create `templates` in order to simplify the deployment process of a new VM.

Many Linux installations will utilize a machine identification number generated at install time, called the `D-Bus Machine ID`. On a hypervisor, two VMs must not have the same D-Bus Machine ID.

### OpenSSH
The most prevalent method in use for accessing a remote virtual guest on a cloud platform is through the use of OpenSSH software.

A remove VM on a cloud platform would have the OpenSSH `server` running, while the administrator that wants to connect would have the OpenSSH `client` with pre-shared keys for remote access.

In order to generate a key pair, use the following command:

```bash
ssh-keygen
```
This command creates two keys: a `public` one, that gets copied to the remote VM, and a `private` one, that will remain on the administrator's local machine (stored in `~/.ssh/`). 

In order to copy the public key to the remote VM, use this command:

```bash
ssh-copy-id -i <public-key> user@cloud_server
```
This will copy the public SSH key from the key pair just generated to the remote cloud server. The public key will be recorded in the `~/.ssh/authorized_keys` file of the cloud server.

Most of the time, when a cloud Linux system, an SSH key pair will automatically be generated, and the administrator needs to download the private key on their local system.

The permissions for SSH keys must be `0600` for a private key, and `0644` for a public key.

### Containers
Whereas with a VM an entire computer is emulated, a container uses just enough software to run an application. In this way, there is far less overhead.

Containers make use of the `control groups` (better known as `cgroups`) mechanism within the Linux kernel.

### Commands

```bash
# Used to verify and view a system's DBUs ID
dbus-uuidgen

# Used to generate an SSH key pair for accessing a remote VM
ssh-keygen

# Used to copy an SSH public key to a remote VM for remote authentication
ssh-copy-id

# Used to aid in the configuration and deployment of VMs and containers to the cloud
cloud-init
```

---
Concepts in this lesson:
- ✅ Virtual machine
- ✅ Linux container
- ✅ Application container
- ✅ Guest drivers
- ✅ SSH host keys
- ✅ D-Bus machine id