## On Windows
- Accessing wsl files in Windows Explorer. Type the following after starting wsl in File Explorer Address bar
  ```
  \\wsl$
  ```
  
## On WSL
Command                                     | Description
---                                         | ---
sudo apt-get update && sudo apt-get upgrade | Update and upgrade in one command
sudo -i 		                                | To become root
uname -a		                                | Entire name of system
cd /mnt/c 		                              | C drive
cd /mnt/d 		                              | D drive

## Unable to access internet through WSL
- If ping google.com doesn't work try following. Getting sudo apt-get update and upgrade working.
```
sudo nano /etc/resolv.conf
```
- Change nameserver to following line
```
nameserver 8.8.8.8
```
- To make this change permanent create file _**/etc/wsl.conf**_
```
sudo nano /etc/resolv.conf
```
- Add following to the file
```
[network]
generateResolvConf = false
```  

## Removable Media and Network Drives
- Mount removable media: (e.g. E:)
```
sudo mkdir /mnt/e
```
```
sudo mount -t drvfs D: /mnt/e
```
- To safely unmount
```
sudo umount /mnt/e
```
- You can also mount network shares without smbfs:
```
sudo mount -t drvfs '\\server\share' /mnt/share
```
```
sudo mount -t drvfs '\\Ingoigw111dat\ea\050_D\Knowledge_Sharing\Intern_work\FY20\2019-20_Madhav_Kshirsagar' /mnt/share
```
