# WSL Password Reset
[source](https://itsfoss.com/reset-linux-password-wsl/)
## Switch Root as a default user
1. Note down the user name of wsl machine. This is text in green color on the prompt **user_name@windows_PC_name**.
2. Open CMD and type foll
    ```
    ubuntu config --default-user root
    ```
    ### Commands for different distributions
    Distro       | Windows CMD
    ---          |  ---
    Ubuntu       | ubuntu config –default-user root
    Ubuntu 20.04 |	ubuntu2004 config –default-user root
    Ubuntu 18.04 |	ubuntu1804 config –default-user root
    Debian       |	debian config –default-user root
    Kali Linux   |	kali config –default-user root

## Reset the password for the account
1. Start the wsl. This time you will directly login as root.
2. Type following command to reset the password
    ```
    passwd user_name
    ```
## Set user_name as default again
1. Go to CMD
2. Type foll cmd
    ```
    ubuntu config --default-user user_name
    ```
3. If you restart the WSL you would have logged in as _**user_name**_
