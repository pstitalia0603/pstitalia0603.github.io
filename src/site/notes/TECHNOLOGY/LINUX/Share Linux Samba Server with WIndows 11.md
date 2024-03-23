---
{"dg-publish":true,"permalink":"/technology/linux/share-linux-samba-server-with-w-indows-11/","tags":["linux"],"noteIcon":""}
---

# [How to configure Samba Server with Debian 11](https://unixcop.com/how-to-configure-samba-server-with-debian-11/)

## Install Samba server

Check what is the IP address of the server.

```
# ip addr
```

Update Server

```
sudo apt update
```

Install required package for Samba server.

```
sudo apt install samba
```

Enable samba service on reboot.

```
systemctl enable smbd
```

Open the following ports on the firewall.

```
ufw allow 139

ufw allow 445 

sudo ufw allow Samba
```

Now, restart the smbd service

```
systemctl restart smbd
```

Check running status of service.

```
systemctl status smbd
```

## How to setup samba share.

Define a folder that will be shared across the network. In our example, the scenario folder name will be smbshare.

Create a folder first.

```
mkdir /media/USBHDD
```

Before editing, copy the samba configuration file for the safe side.

```
cp /etc/samba/smb.conf smb.conf.orig
```

Edit the conf file and amend the following line at the bottom.

```
\[samba-share\]
comment = unixcop share
path = /media/USBHDD
read-only = no
browsable = yes
writeable=yes
```

Add a samba user to provide access over the internet.

```
sudo useradd smbuser
```

Provide smb authentication to the newly created user i.e. smbuser.

```
sudo smbpasswd -a smbuser
```

Make smbuser owner for samba share.

```
sudo chown smbuser:smbuser /smbshare/
```

Restart the samba service once again.

```
systemctl restart smbd
```

Open an MS window client. Map drive

![](https://unixcop.com/wp-content/uploads/2021/09/image-95.png)

Reference: 
[[TECHNOLOGY/LINUX/Share external drive with Samba on Raspberry Pi\|Share external drive with Samba on Raspberry Pi]]
[[TECHNOLOGY/LINUX/Raspberry Pi as a Samba server to create a Shared folder between two or more computers.\|Raspberry Pi as a Samba server to create a Shared folder between two or more computers.]]
[[TECHNOLOGY/LINUX/Upgrade Debian 12 From Debian 11\|Upgrade Debian 12 From Debian 11]]
[[TECHNOLOGY/LINUX/How to Enable SMB Server in Windows 11 PC – WebNots\|How to Enable SMB Server in Windows 11 PC – WebNots]]