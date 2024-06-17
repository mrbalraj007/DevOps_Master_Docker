# Swarm services
Swarm services use a declarative model, which means that you define the desired state of the service and rely upon Docker to maintain this state. The state includes information such as (but not limited to):

The image name and tag of the service containers should run.
How many containers participate in the service?
Whether any ports are exposed to clients outside the swarm
Whether the service should start automatically when Docker starts
The specific behavior that happens when the service is restarted (such as whether a rolling restart is used)
Characteristics of the nodes where the service can run (such as resource constraints and placement preferences)


## How to create a service in Docker Swarm
### Command for help:
```bash
docker service --help

Usage:  docker service COMMAND

Manage Swarm services

Commands:
  create      Create a new service
  inspect     Display detailed information on one or more services
  logs        Fetch the logs of a service or task
  ls          List services
  ps          List the tasks of one or more services
  rm          Remove one or more services
  rollback    Revert changes to a service's configuration
  scale       Scale one or multiple replicated services
  update      Update a service
```
> Containers can be deployed to the swarm in much the same way as containers are run on a manager node. A service is created, and the image that should be used to deploy the container is specified.

> To create a service First, open a terminal, ssh into your manager node, and run the following command:
```bash
$ docker service create -d alpine ping 192.168.1.221  # we are creating a apline image and ping it.

$ docker service create -d alpine ping 192.168.1.221
i4acapmlmsuncfdjicwmfs12f
```

> To check the service status ```docker service ls```
```bash
$ docker service ls
ID             NAME                MODE         REPLICAS   IMAGE           PORTS
i4acapmlmsun   distracted_banzai   replicated   1/1        alpine:latest
```

> To check the service logs ```docker service logs <Image name or Image ID>```
```bash
$ docker service logs distracted_banzai


outcomes:
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=169 ttl=64 time=0.178 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=170 ttl=64 time=0.545 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=171 ttl=64 time=0.537 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=172 ttl=64 time=0.595 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=173 ttl=64 time=0.546 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=174 ttl=64 time=0.518 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=175 ttl=64 time=0.212 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=176 ttl=64 time=0.703 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=177 ttl=64 time=0.202 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=178 ttl=64 time=0.183 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=179 ttl=64 time=0.623 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=180 ttl=64 time=0.146 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=181 ttl=64 time=0.530 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=182 ttl=64 time=0.666 ms
distracted_banzai.1.os1zkyewjgaz@docker    | 64 bytes from 192.168.1.221: seq=183 ttl=64 time=0.236 ms
```



