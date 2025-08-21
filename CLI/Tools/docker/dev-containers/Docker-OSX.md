
To setup the container and use in arch linux

What to install of packages, and background services

Paste the docker .img copy comand from compose file

```bash
docker build --platform=linux/amd64 -t sickcodes/docker-osx:naked -f Dockerfile.naked .
```


Get the ip of the machine
```bash
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <container_name_or_id>
```

## on the guest

Paste the ip in the command like in this example

```
sudo usbfluxd -f -r <IP>:5000
```
