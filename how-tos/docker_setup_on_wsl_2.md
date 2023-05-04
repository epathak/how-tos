# Setting up Docker in WSL
If you think setting up docker is a single cmd task then you are wrong!... I hope this works for you... : )
- Configure sudo access for the non-root user:
  ```
  grep -E 'sudo|wheel' /etc/group
  ```
- (should get: `sudo:27:myusername` el ose run: `usermod -aG sudo myusername`)
  ```
  sudo grep -E '%sudo|%wheel' /etc/sudoers
  ```
- should get: %wheel ALL=(ALL) ALL else edit and uncomment
  ```
  su myusername
  ```
- should get: no errors
  ```
  sudo -v
  ```

## Update/upgrade packages(test network)
- should get: no errors
  ```
  sudo apt update && sudo apt upgrade
  ```
- **else** run below commands)
  ```
  echo -e "[network]\ngenerateResolvConf = false" | sudo tee -a /etc/wsl.conf
  ```
  ```
  sudo unlink /etc/resolv.conf
  ```
  ```
  echo nameserver 1.1.1.1 | sudo tee /etc/resolv.conf
  ```
- (try above command, if there are still errors, try the below commands)
  ```
  netsh winsock reset
  ```
  ```
  netsh int ip reset all
  ```
  ```
  netsh winhttp reset proxy
  ```
  ```
  ipconfig /flushdns
  ```
  ```
  reboot
  ```

## Setup docker repo(cli-tools)
- (remove residue)
  ```
  sudo apt remove docker docker-engine docker.io containerd runc
  ```
  ```
  sudo apt install --no-install-recommends apt-transport-https ca-certificates curl gnupg2
  ```
- (install dependencies)
  ```
  source /etc/os-release
  ```
  ```
  curl -fsSL https://download.docker.com/linux/${ID}/gpg | sudo apt-key add -
  ```
- (setup docker repo)
  ```
  echo "deb [arch=amd64] https://download.docker.com/linux/${ID} ${VERSION_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/docker.list
  ```
- Add repo to source and run update docker repo(cli-tools) 
  ```
  sudo apt update
  ```

##  Install Docker:
- This is where you install docker
  ```
  sudo apt install docker-ce docker-ce-cli containerd.io
  ```
- (install tools)
  ```
  sudo usermod -aG docker $USER
  ```
  ```
  exit
  ```
  ```
  wsl
  ```
- (add user to docker group, logout and login )
  ```
  groups
  ```
  (lists groups, should list docker)

## Run docker daemon:
NOTE: You will have to run the ubuntu in admin mode to run the sudo dockerd command
  ```
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