---
{"dg-publish":true,"permalink":"/reference/useful-linux-commands/","tags":["linux","Reference"],"noteIcon":"","created":"2024-06-04 1:18:06 pm","updated":"2024-06-04 1:18:50 pm"}
---


### List all normal users in Linux system:
```
getent passwd {1000..60000}
```

### FInd all hosts on (local) network
```
nmap -sn 192.168.1.0/24
```



### Node and NPM
https://docs.npmjs.com/downloading-and-installing-node-js-and-npm

```
sudo apt install npm
```

**Note:** to download the latest version of npm, on the command line, run the following command:

```
npm install -g npm
```

### Information about current RAM usage
https://linuxconfig.org/how-to-check-raspberry-pi-ram-size-and-usage

```
free -ght
```

### Which OS?
```
cat /etc/os-release 
```

### Which [raspberry pi] Model
```
cat /sys/firmware/devicetree/base/model
```

### Check architecture
```
apt-config dump | grep -F "APT::Architectures" -
```

