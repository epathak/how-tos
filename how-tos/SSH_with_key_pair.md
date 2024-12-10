# SSH into SSH server with Public Private Key pair
<!-- ---
> NOTE: 
> -->
- On the ssh client Go to `~/.ssh`
  ```
  cd ~/.ssh
  ```

- On the ssh client Create public-private key pair
  ```
  ssh-keygen -t rsa -b 4096 -C "your.mail@id.com"
  ```
  - Give a name to your key pair files or keep it default
  - give a passphrase for your private key or keep it empty
  ![](images/image-20.png)

- From the ssh client Copy the public key to server
  ```
  ssh-copy-id -i public_key.pub user_name@ip_address
  ``` 
  - `-i` is the identity file aka the public key
  ![Alt text](images/image-21.png)

- Login to ssh server and go to `~/.ssh` folder
  - Your public key will be added to `authorized_key` file
  ![Alt text](images/image-22.png)


- On the ssh client open the `~/.ssh/config` file and add this
  ![Alt text](images/image-23.png)

- From all the ssh clients close all the logins to the ssh server
  - open powershell and login using the `user_given_alternative_name`
  ![Alt text](images/image-24.png)