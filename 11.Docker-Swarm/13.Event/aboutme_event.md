# Docker Events

[Docker System Events](https://docs.docker.com/reference/cli/docker/system/events/)

When you create any services then it can be seen on master
if any container created alogn with services and event will be seen where the container created.

*master*
```yml
$ docker events
```
```
docker events --filter 'event=create'
docker events --filter 'event=delete'
docker events --filter 'event=disconnet'
docker containter --filter 'container=id'
docker containter --filter 'image=imagename'

```