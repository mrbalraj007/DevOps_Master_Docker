
- To build (Start) the container
 ```bash
 docker-compose up -d
```

- To delete the container
```bash
docker-compose down
```
**Note: ** 
- *If you are not defining any network during creation of container then it will create automatically network for us.*

- *If you add any text is existing compose file then it will create only newly added service (command) only and won't delete other one.*

```yml
version: '3.7'
services:
  web-app:
    image: nginx
    ports:
      - "8000:80"
  web-app1:                     
    image: nginx
    ports:
      - "8001:80"      # suppose if I change the port to 8002 then it will delete only web-app1 container and create a new container with new port
```

✨ **Important Note** ✨: If you run the *docker-compose down* command, then volume won't be deleted. If you want to delete volume as well, then you have to pass the --volume parameter as below. It will delete the container along with the volume. 
```bash
docker-compose down --volume
```