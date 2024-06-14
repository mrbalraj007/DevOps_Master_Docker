# We can create a container using JSON format rather than yaml.
✨ *Note* ✨: Why JSON format support because JSON is a superset of yml file.

### Point to Remember:
 - *If you are not defining any network during creation of container then it will create automatically network for us.*

- *If you add any text is existing compose file then it will create only newly added service (command) only and won't delete other one.*

*JSON FORMAT* :
```yml
{
    "version": "3.7",
    "services": {
        "web-app": {
            "image": "nginx",
            "ports": [
                "8000:80"
            ]
        },
        "web-app1": {
            "image": "nginx",
            "ports": [
                "8001:80" # suppose if I change the port to 8002 then it will delete only web-app1 container and create a new container with new port
            ]
        }
    }
}
```
*You can use the online converter from __YAML TO JSON__ : https://jsonformatter.org/yaml-to-json


- To build (Start) the container
 ```bash
 docker-compose -f docker-compose.json up -d
```
*Important*: We have to use -f parameter if we are not using yaml file.

- To delete the container
```bash
docker-compose -f docker-compose.json down
```

✨ **Important Note** ✨: If you run the *docker-compose down* command, then volume won't be deleted. If you want to delete volume as well, then you have to pass the --volume parameter as below. It will delete the container along with the volume. 
```bash
docker-compose -f docker-compose.json down --volume
```