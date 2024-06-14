Basic Commands:
docker-compose up -d
docker-compose create
docker-compose start
docker-compose stop
docker-compose rm
docker-compose down

__Docker-compose create__ : This command is used to create a container, and it will neither create the network and volume nor start them; it will just create them. 


*Difference between __Create__ and __up --no-start__*
- Create command won't create __network__ while creating a container while up will do.


Help command: 
docker-compose --help

 Commands:
 ```bash
  build       Build or rebuild services
  convert     Converts the compose file to platform's canonical format
  cp          Copy files/folders between a service container and the local filesystem
  create      Creates containers for a service.
  down        Stop and remove containers, networks
  events      Receive real time events from containers.
  exec        Execute a command in a running container.
  images      List images used by the created containers
  kill        Force stop service containers.
  logs        View output from containers
  ls          List running compose projects
  pause       Pause services
  port        Print the public port for a port binding.
  ps          List containers
  pull        Pull service images
  push        Push service images
  restart     Restart service containers
  rm          Removes stopped service containers
  run         Run a one-off command on a service.
  start       Start services
  stop        Stop services
  top         Display the running processes
  unpause     Unpause services
  up          Create and start containers
  version     Show the Docker Compose version information
```