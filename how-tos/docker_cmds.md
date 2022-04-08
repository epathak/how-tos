# Basic Docker Cmds	
- List docker images
```
docker images
```
- Remove images, containers, volumes, and networks — that are dangling (not tagged or associated with a container)
```
docker system prune
```
- Build docker image
```
docker build -t name_of_image:latest -f docker_file .
```
- Run the dokcer image with interactive terminal
```
docker run -it name_of_image:latest
```
- List of dokcer images running
```
docker ps
```

