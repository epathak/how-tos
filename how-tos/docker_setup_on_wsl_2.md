# Setup Docker on Windows Subsystem for Linux (WSL)
## Setting up WSL in power shell
- To see a list of the Linux distributions 
  ```
  wsl --list -o
  ```
- Install Ubuntu-20.04 in wsl 
  ```
  wsl --install -d Ubuntu-20.04
  ```
- Download and install WSL2
https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package
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
- For more info on WSL
https://docs.microsoft.com/en-us/windows/wsl/install-win10

## Setting up Docker in WSL
- Configure sudo access for the non-root user:
  ```
  grep -E 'sudo|wheel' /etc/group
  ```
  (should get: sudo:27:myusername else run: usermod -aG sudo myusername)
- ```
  sudo grep -E '%sudo|%wheel' /etc/sudoers
  ```
  (should get: %wheel ALL=(ALL) ALL else edit and uncomment)
- ```
  su myusername
  ```
- ```
  sudo -v
  ```
  (should get: no errors)

## Update/upgrade packages(test network)
- ```
  sudo apt update && sudo apt upgrade
  ```
  (should get: no errors, else run below commands)
- ```
  echo -e "[network]\ngenerateResolvConf = false" | sudo tee -a /etc/wsl.conf
  ```
- ```
  sudo unlink /etc/resolv.conf
  ```
- ```
  echo nameserver 1.1.1.1 | sudo tee /etc/resolv.conf
  ```
  (try above command, if still errors, try below commands)
- ```
  netsh winsock reset
  ```
- ```
  netsh int ip reset all
  ```
- ```
  netsh winhttp reset proxy
  ```
- ```
  ipconfig /flushdns
  ```
- ```
  reboot
  ```

## Setup docker repo(cli-tools)
- ```
  sudo apt remove docker docker-engine docker.io containerd runc
  ```
  (remove residue)
- ```
  sudo apt install --no-install-recommends apt-transport-https ca-certificates curl gnupg2
  ```
  (install dependencies)
- ```
  source /etc/os-release
  ```
- ```
  curl -fsSL https://download.docker.com/linux/${ID}/gpg | sudo apt-key add -
  ```
  (setup docker repo)
- ```
  echo "deb [arch=amd64] https://download.docker.com/linux/${ID} ${VERSION_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/docker.list
  ```
- ```
  sudo apt update
  ```
  (Add repo to source and run update)ocker repo(cli-tools)

##  Install Docker:
- ```
  sudo apt install docker-ce docker-ce-cli containerd.io
  ```
  (install tools)
- ```
  sudo usermod -aG docker $USER
  ```
- ```
  exit
  ```
- ```
  wsl
  ```
  (add user to docker group, logout and login )
- ```
  groups
  ```
  (lists groups, should list docker)

## Run docker daemon:
NOTE: You will have to run the ubuntu in admin mode to run the sudo dockerd command
- ```
  sudo dockerd
  ```
  (should get: API listen on /var/run/docker.sock at the end)

## Issue you may face
- apt update and upgrade not working
  ```
  sudo nano /etc/resolv.conf
  ```
- Change nameserver to following line
  ```
  nameserver 8.8.8.8
  ```
- To make this change permanent create file **_/etc/wsl.conf_** and add following
  ```
  sudo nano /etc/resolv.conf
  ```
  ```
  [network]
  generateResolvConf = false
  ```