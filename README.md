## Pull mumble image:
```
docker pull rdamron/alpine-mumble
```

## Create named storage:
```
docker create -v /data --name mumble-data rdamron/alpine-mumble /bin/true
```

## Run and attach storage:
```
docker run -d --volumes-from mumble-data --name mumble-server-1 -p 64738:64738/tcp -p 64738:64738/udp rdamron/alpine-mumble
```

## Find SuperUser password in logs
```
docker logs mumble-server-1
```

## Update mumble:
```
docker stop mumble-server-1
docker rm mumble-server-1
docker pull rdamron/alpine-mumble
docker run -d --volumes-from mumble-data --name mumble-server-1 -p 64738:64738/tcp -p 64738:64738/udp rdamron/alpine-mumble
```
