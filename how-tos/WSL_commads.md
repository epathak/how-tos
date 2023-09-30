# Setup Docker on Windows Subsystem for Linux (WSL)
## Setting up WSL in power shell
- Download and install [WSL2](https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)

- To see a list of the Linux distributions 
  ```
  wsl --list -o
  ```
- Install Ubuntu-20.04 in wsl 
  ```
  wsl --install -d Ubuntu-20.04
  ```
- Set WSL version to 2 
  ```
  wsl --set-version Ubuntu-20.04 2
  ```
- To check the WSL mode 
  ```
  wsl -l -v
  ```
- To update the WSL kernel 
  ```
  wsl --update
  ``` 
- For more info on [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

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

## Convert files to Unix based files
- How do I fix "$'\r': command not found" errors running Bash scripts in WSL?
```
sudo apt-get install dos2unix
```
```
dos2unix [file]
```
```
man dos2unix
```

## Checking disk filesystem
- list of mounted disks
```
df
```
- location of df executable
```
which df
```

## htop is an interactive system-monitor process-viewer and process-manager
```
htop
```
- Will open PWD from Ubuntu as network drive
```
explorer.exe .
```
- List of LSB (Linux Standard Base) modules
```
lsb_release -a
```

## List of Memory devices: Find what the drive is called
```
lsblk
```
```
sudo blkid
```
```
sudo fdisk -l
```
- Mount USB drive
```
sudo mount -t drvfs E: /mnt/e
```
- Unmount USB drive
```
sudo umount -t drvfs E: /mnt/e
```
- Display file in Hexadecimal
```
hexdump  -C ./files_in_c.bin
```
- Display file in Binary
```
xxd -b ./files_in_c.bin
```

## Unzip files
- x = extract, f = file
```
tar -xf archive.tar.gz
```
- v = visible, print names of files
```
tar -xvf archive.tar.gz
```
- C = specify destination directory
```
tar -xf archive.tar.gz -C /home/linuxize/files
```
- Extract specific files
```
tar -xf archive.tar.gz file1 file2
```
- t = list contents of the file
```
tar -tf archive.tar.gz
```
- v = verbose, more information, such as owner, file size, timestamp
```
tar -tvf archive.tar.gz
```
## ls command and its switches
- l: This uses the long listing format while printing out. This is much
			more informative than the default format.
		i: Prints out the inode number of the file
		s: Prints the file size in blocks
		a: Prints out all entries and does not ignore any files
		n: Prints out the numeric user id and group id
		h: Print the sizes in human readable format.

```
ls -lisan <filename>
```
- Print matadata in human readable format
```
stat <filename>
```

## File TxRx using SSH/SCP [source](https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/)
- Install SSH server if you don't have one
```
sudo apt-get install openssh-server
```
- Enable the ssh service by typing
```
sudo systemctl enable ssh
```
- Start the ssh service by typing
```
sudo systemctl start ssh
```
- Test it by login into remote PC using from local PC
```
ssh user@server-name
```
- Configure firewall and open port 22
```
sudo ufw allow ssh
```
```
sudo ufw enable
```
```
sudo ufw status
```
- From Remote PC to Local PC
```
scp pritam@172.16.0.29:~/Downloads/wsl_Ubuntu-20.04.tar C:\Users\z004emnf\Downloads
```
- From Local to Remote PC
```
scp .\wsl_Ubuntu-20.04.tar pritam@172.16.0.29:~/Downloads
```

## Package queries 
- Check if package is installed
```
dpkg-query -l <name of the package>
```

## Upgrade Ubuntu in WSL2
```
sudo apt update && sudo apt upgrade
```
```
# restart Ubuntu
sudo do-release-upgrade
```
- Check the ubuntu version in your system
```
lsb_release -a
```