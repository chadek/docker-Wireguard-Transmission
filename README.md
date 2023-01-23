# docker-Wireguard-Transmission
Docker compose for torrenting with transmission behind wireguard tunnel inspirated from [this post](https://www.reddit.com/r/VPNTorrents/comments/j1ap68/my_docker_setup_for_torrenting_transmission/)

To have ipv6 working, you should configure docker daemon with the provided configuration file: etc/docker/daemon.json

Wireguard configuration sample provided [here](https://github.com/chadek/docker-Wireguard-Transmission/blob/main/wireguard/wg0.conf) should be filed with proper values and mapped to the wireguard image
