# 🛠️ Fix: Proxmox VM Not Starting Due to Node Hostname Mismatch
  
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=for-the-badge&logo=proxmox&logoColor=white)

If you're facing an error like this when starting a Proxmox virtual machine:

![img alt](https://github.com/khalidit23/fix-proxmox-vm-start-error/blob/2634491979e5eb5d8d9cc931036c7a3963a323bd/p-error.jpeg)

---  
Then this guide will help you fix the issue by correcting the **Proxmox node hostname mismatch** between the static and transient hostnames.

If your system’s **static hostname** and **transient hostname** don’t match, Proxmox may look in the wrong directory and fail to find `200.conf`, resulting in a VM start failure.

---

## Check Hostnames

Run the following:

```bash
hostnamectl
```
 
## Example output:

```
Static hostname: khalid
Transient hostname: KHALID-DELL-730XD-PROXMOX
```
This mismatch causes Proxmox to look for the VM config under `KHALID-DELL-730XD-PROXMOX`, while the VM was created under `khalid`

## Set all types of hostnames to the same value (`khalid` in this case):

```bash
sudo hostnamectl set-hostname khalid --static --pretty --transient
```
## Then confirm:
```bash
hostnamectl
```
**Now your Proxmox VM should start successfully.

## ❤️ Support
If this guide helped you, feel free to star ⭐ this repository and share it with others!
