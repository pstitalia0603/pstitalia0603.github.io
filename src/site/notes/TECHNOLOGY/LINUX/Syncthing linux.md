---
{"dg-publish":true,"permalink":"/technology/linux/syncthing-linux/","tags":["linux","syncthing"],"created":"2024-04-04 13:55","updated":"2024-04-04 13:56"}
---

[[TECHNOLOGY/LINUX/Syncthing on Raspberry Pi\|Syncthing on Raspberry Pi]]
# [Syncthing](https://apt.syncthing.net/)

https://pimylifeup.com/raspberry-pi-syncthing/

https://www.linuxfordevices.com/tutorials/ubuntu/syncthing-install-and-setup

**find configuration file: syncthing -paths**

## Debian/Ubuntu Packages

To allow the system to check the packages authenticity, you need to provide the release key.

\# Add the release PGP keys:
**sudo mkdir -p /etc/apt/keyrings
sudo curl -L -o /etc/apt/keyrings/syncthing-archive-keyring.gpg https://syncthing.net/release-key.gpg**

The `stable` channel is updated with stable release builds, usually every first Tuesday of the month.

\# Add the "stable" channel to your APT sources:
**echo "deb \[signed-by=/etc/apt/keyrings/syncthing-archive-keyring.gpg\] https://apt.syncthing.net/ syncthing stable" | sudo tee /etc/apt/sources.list.d/syncthing.list**

The `candidate` channel is updated with release candidate builds, usually every second Tuesday of the month. These predate the corresponding stable builds by about three weeks.

\# Add the "candidate" channel to your APT sources:
**echo "deb \[signed-by=/etc/apt/keyrings/syncthing-archive-keyring.gpg\] https://apt.syncthing.net/ syncthing candidate" | sudo tee /etc/apt/sources.list.d/syncthing.list**

And finally.

\# Update and install syncthing:
**sudo apt-get update
sudo apt-get install syncthing**

---

## Troubleshooting

## Distribution Package Preferred Over This Version

To make sure the system packages do not take preference over those in this repository, you need to adjust the priority/preference.

\# Increase preference of Syncthing's packages ("pinning")
**printf "Package: \*\\nPin: origin apt.syncthing.net\\nPin-Priority: 990\\n" | sudo tee /etc/apt/preferences.d/syncthing.pref**

## HTTPS Method Driver Missing

Depending on your distribution, you may see an error similar to the following when running `apt-get`:

E: The method driver /usr/lib/apt/methods/https could not be found.
N: Is the package apt-transport-https installed?
E: Failed to fetch https://apt.syncthing.net/dists/syncthing/InRelease

If so, please install the `apt-transport-https` package and try again:

**sudo apt-get install apt-transport-https**

## Server Certificate Verification Failed

Especially for older distributions, your system TLS certificate store might be outdated. Since October 2021, a newer Let's Encrypt root certificate must be installed, or you may see an error similar to the following when running `apt-get`:

E: Failed to fetch https://apt.syncthing.net/dists/syncthing/stable/binary-armhf/Packages
server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
E: Some index files failed to download. They have been ignored, or old ones used instead.

Please make sure you have the latest version of the `ca-certificates` package and try again:

**sudo apt-get update
sudo apt-get install ca-certificates**

---
### Auto on WIndows - Syncthing
https://docs.syncthing.net/users/autostart.html#autostart-windows-taskschd


REFERENCE:
https://viniciusnevescosta.medium.com/syncing-and-backing-up-your-thoughts-with-obsidian-syncthing-and-gitwatch-a55670b2b63f

https://snippets.page/posts/sync-obsidian-notes-between-pc-and-android-with-syncthing/

https://prakashjoshipax.com/free-obsidian-sync/

https://facedragons.com/foss/sync-obsidian-across-devices/

## Edit/change password
Edit the [config file 14.6k](https://docs.syncthing.net/users/config.html) to remove the user and password in the `gui` section, then restart syncthing. 
<encryptionPassword></encryptionPassword>

`%LOCALAPPDATA%\Syncthing` (Windows) (or C:\Users\psfrago\AppData\Local\Syncthing\config.xml)