# Docker: I use them everyday but I don't understand what they are
[source](https://youtu.be/0oEsMwSxBsk)
## Background
- Setup docker on WSL2 on Win10
- Create a c file named hello_world.c
- Compile the code with static linking
```
gcc hello_world.c -static -o hello_world
```
- Check that **_hello_world_** is and executable with _**x**_ as file permission
```
ls -alogF
```
![image](https://user-images.githubusercontent.com/31771892/161368236-e993b0ad-eeb4-4a7f-b834-5f13cf7e7d1e.png)
If you reboot your system these files will still be there. There is a possibility that you might delete some file or put files in wrong location.
Imagine setting up a server, may be you have to install nginx, apache, python, php, .NET, and set it up. If you get it wrong you will have configuration issues. If you are dealing with lots of computers this becomes tedious task 

