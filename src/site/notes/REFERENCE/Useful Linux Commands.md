---
{"dg-publish":true,"permalink":"/reference/useful-linux-commands/","tags":["linux","Reference"],"noteIcon":"","created":"2024-06-04 1:18:06 pm","updated":"2024-06-04 1:18:50 pm"}
---


List all normal users in Linux system:
```
getent passwd {1000..60000}
```

FInd all hosts on (local) network
```
nmap -sn 192.168.1.0/24
```



Node and NPM
https://docs.npmjs.com/downloading-and-installing-node-js-and-npm


```
sudo apt install npm
```

**Note:** to download the latest version of npm, on the command line, run the following command:

```
npm install -g npm
```

The free command will give us information about current RAM usage, and break down how it is being utilized across our system. For best results, we recommend using the `-g`, `-h`, and `-t` options. This will tell free to display RAM amounts in Gigabytes, make the amounts human readable, and give us the totals, respectively. https://linuxconfig.org/how-to-check-raspberry-pi-ram-size-and-usage

```
free -ght
```

(which OS?)
```
cat /etc/os-release 
```

which raspberry pi Model
```
cat /sys/firmware/devicetree/base/model
```
