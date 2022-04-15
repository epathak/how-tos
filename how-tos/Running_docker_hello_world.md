@source: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04<br>
Let apt use packages over HTTPS:<br>
`sudo apt install apt-transport-https ca-certificates curl software-properties-common`<br>

Add the GPG key for the official Docker repository to your system<br>
`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`<br>

Add the Docker repository to APT sources:<br>
`sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"`<br>
This will also update our package database with the Docker packages from the newly added repo.<br>

Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:<br>
NOTE: This command will not run on WSL2<br>
`apt-cache policy docker-ce`<br>

Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:<br>
`sudo systemctl status docker`<br>

Run a hello-world example<br>
`docker run hello-world`<br>

To see the images that have been downloaded to your computer<br>
`docker images`<br>
