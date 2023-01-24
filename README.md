docker-Wireguard-Transmission
=========

Docker compose for torrenting with transmission client behind wireguard tunnel inspirated from [this post](https://www.reddit.com/r/VPNTorrents/comments/j1ap68/my_docker_setup_for_torrenting_transmission/)


Requirements
------------

This is a docker-compose file with some configuration samples for wireguard, inside a container, and docker. So the only package required is **docker-compose**. You can install it with something like this on a debian like system:

```
apt install docker-compose
```

To have **ipv6 working**, you should configure docker daemon with the provided **configuration file** by editing the /etc/docker/daemon.json file. Then docker daemon must be reloaded or restart to apply changes with:

```
systemctl restart docker
```

Running this tool
------------


Wireguard configuration sample provided [here](https://github.com/chadek/docker-Wireguard-Transmission/blob/main/wireguard/wg0.conf) should be filed with proper values and mapped to the wireguard image by placing it into the path of the mounted volume for the container of that you will choose by replacing  this one */some/path/to/wireguard/config*.

The wireguard config include some network post up script to nat correctly ipv4 through this mess of interfaces, more detail [here](https://github.com/linuxserver/docker-wireguard) 

This docker-compose start a wireguard container with a provided configuration mounted througt a volume  
