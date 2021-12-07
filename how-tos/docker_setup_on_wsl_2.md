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


