# hshelp - Tools for Handshake

## install-all-hsd

This script installs a Handshake full node (https://github.com/handshake-org/hsd) and all dependencies.

### Prerequisites
* Ubuntu (20.04 LTS preferred) or Debian
* Static public IP address (for listening full node)
* 2GB RAM
* Enough storage space, the current chain (Feb 2022) takes already about 15GB - check via ```df -h```

If you install this on a new deployed system and currently work with user ```root``` consider using a different user with root privilegies. 

```
adduser <Username>
usermod -aG sudo <Username>
su - <Username>
````

### Installation
On a new deployed system this installation takes about 3 minutes before hsd full node is started as service. 
Duration of a full chain sync depends on your system, most important is fast storage. On performant entry level VPS it takes few hours.
```
sudo apt update
sudo apt install git
cd
git clone https://github.com/befranz/hshelp
hshelp/install-all-hsd
```

![2BDA7A6E-53AD-4F8A-B9F0-2E2E1A8C9AC9_4_5005_c](https://user-images.githubusercontent.com/46194732/153889206-d0c6f38f-9829-4d83-a462-052e02cdd40a.jpeg)


During this first chain sync hsd is still running as a non listening node. After you restart hsd or reboot - which also makes sense since most probably some installed components might require a reboot anyway - the node allows 500 inbound connections. Those could be other full nodes but also SPV nodes like [hnsd](https://github.com/handshake-org/hnsd) or [Fingertip](https://github.com/imperviousinc/fingertip). Running listening public full nodes are essential for Handshake, you do great support by running one!

### Further Settings
The node listens to port ```12038``` and ```44806```. Make sure you allowed those ports on incoming traffic.

If you don't use any firewall consider running one like ```ufw``` and set the specific ports. (Don't forget to set your ssh port ;-)

### Service and Usage
Some useful commands - hsd status: ```systemctl status hsd``` - hsd restart: ```sudo systemctl restart hsd```

hsd node is accessable via ```hsd-cli```, ```hsw-cli``` and API.
Full documentation: https://hsd-dev.org/api-docs/ 

