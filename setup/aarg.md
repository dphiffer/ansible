# aarg

"aarg" comes from Tom Gauld's Noisy Alphabet comic

## Hardware

-   [Intel NUC with 16GB RAM](https://ark.intel.com/content/www/us/en/ark/products/71275/intel-nuc-kit-dc3217iye.html)
-   1TB Kingston internal SSD (KC600 SATA3 MSATA)

## Operating System

-   [Ubuntu 22.04](https://ubuntu.com/download/server)
-   [Installed via USB stick](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos)

## Upgrade/install Packages

```
sudo apt update
sudo apt upgrade -y
sudo apt install emacs-nox yamllint -y
```

## SSH Key

```
cd ~/.ssh
echo "ssh-rsa *public key here*" >> authorized_keys
```

## Static IP

-   Do the following as the root user: `sudo su`
-   Run this server on `192.168.1.4` using CloudFlare's DNS: `emacs /etc/netplan/00-installer-config.yaml`

```
---
network:
  version: 2
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
      addresses:
        - 192.168.1.4/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses: [1.1.1.1, 1.0.0.1]
```

-   Fix file permissions: `chmod 600 /etc/netplan/00-installer-config.yaml`
-   Check config syntax: `yamllint /etc/netplan/00-installer-config.yaml`
-   Apply updates: `netplan apply`
