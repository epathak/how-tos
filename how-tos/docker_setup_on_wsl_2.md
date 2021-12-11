# Setup Docker on Windows Subsystem for Linux (WSL)
## Setting up WSL in power shell
To see a list of the Linux distributions <br>
`wsl --list --o`<br>
Install Ubuntu-20.04 in wsl <br>
`wsl --install -d Ubuntu-20.04` <br>
Download and install WSL2<br>
https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package<br>
Set WSL version to 2 <br>
`wsl --set-version Ubuntu-20.04 2` <br>
To check the WSL mode <br>
`wsl -l -v`<br>
For more info on WSL<br>
https://docs.microsoft.com/en-us/windows/wsl/install-win10<br>

## Setting up Docker in WSL
Configure sudo access for the non-root user:<br>
`grep -E 'sudo|wheel' /etc/group`<br>
(should get: sudo:27:myusername else run: usermod -aG sudo myusername)<br>
`sudo grep -E '%sudo|%wheel' /etc/sudoers`<br>
(should get: %wheel ALL=(ALL) ALL else edit and uncomment)<br>
`su myusername`<br>
`sudo -v`<br>
(should get: no errors)<br>

## Update/upgrade packages(test network)
`sudo apt update && sudo apt upgrade`<br>
(should get: no errors, else run below commands)<br>
`echo -e "[network]\ngenerateResolvConf = false" | sudo tee -a /etc/wsl.conf`<br>
`sudo unlink /etc/resolv.conf`<br>
`echo nameserver 1.1.1.1 | sudo tee /etc/resolv.conf`<br>
(try above command, if still errors, try below commands)<br>
`netsh winsock reset`<br>
`netsh int ip reset all`<br>
`netsh winhttp reset proxy`<br>
`ipconfig /flushdns`<br>
`reboot`<br>

## Setup docker repo(cli-tools)
`sudo apt remove docker docker-engine docker.io containerd runc`<br>
(remove residue)<br>
`sudo apt install --no-install-recommends apt-transport-https ca-certificates curl gnupg2`<br>
(install dependencies)<br>
`source /etc/os-release`<br>
`curl -fsSL https://download.docker.com/linux/${ID}/gpg | sudo apt-key add -`<br>
(setup docker repo)<br>
`echo "deb [arch=amd64] https://download.docker.com/linux/${ID} ${VERSION_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/docker.list`<br>
`sudo apt update`<br>
(Add repo to source and run update)ocker repo(cli-tools)<br>

##  Install Docker:
`sudo apt install docker-ce docker-ce-cli containerd.io`<br>
(install tools)<br>
`sudo usermod -aG docker $USER`<br>
`exit`<br>
`wsl`<br>
(add user to docker group, logout and login )<br>
`groups`<br>
(lists groups, should list docker)<br>

## Run docker daemon:
NOTE: You will have to run the ubuntu in admin mode to run the sudo dockerd command<br>
`sudo dockerd`<br>
(should get: API listen on /var/run/docker.sock at the end)<br>




