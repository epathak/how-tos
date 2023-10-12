[@source](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
- Let apt use packages over HTTPS:
  ```
  sudo apt install apt-transport-https ca-certificates curl software-properties-common
  ```

- Add the GPG key for the official Docker repository to your system
  ```
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  ```

- Add the Docker repository to APT sources:
  ```
  sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
  ```
  This will also update our package database with the Docker packages from the newly added repo.

- Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
> **NOTE**: This command will not run on WSL2
> ```
>  apt-cache policy docker-ce
> ```

- Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:
  ```
  sudo systemctl status docker
  ```

- Run a hello-world example
  ```
  docker run hello-world
  ```

- To see the images that have been downloaded to your computer
  ```
  docker images
  ```
