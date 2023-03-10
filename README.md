docker-Wireguard-Transmission
=========

A docker compose file for torrenting through a vpn tunnel, using transmission as torrent client and wireguard as vpn tunnel inspirated from [this post](https://www.reddit.com/r/VPNTorrents/comments/j1ap68/my_docker_setup_for_torrenting_transmission/)


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

The wireguard config include some network post up script to nat correctly ipv4 through interfaces, more detail [here](https://github.com/linuxserver/docker-wireguard) 

After configuring properly wireguard, a simple run of this will bring everything up:

```
docker-compose up
```

Or if you want to run as a daemon in background:

```
docker-compose up -d 
```

To check that torrent client is effectively connected to your vpn ip, you can run the following command:

```
docker exec transmission sh -c 'curl -4 ifconfig.io'
```
and this for ipv6:

```
docker exec transmission sh -c 'curl -6 ifconfig.io'
```
