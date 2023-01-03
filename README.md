# steamdeck-docker

Instructions &amp; scripts for steamdeck customization

## install docker and enable ssh server

```bash
# general 
sudo steamos-readonly disable
sudo pacman -Sy archlinux-keyring
sudo pacman -Su

# docker
sudo pacman -S docker
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker

# docker compose
sudo mkdir -R /usr/local/lib/docker/cli-plugins/
sudo wget -O /usr/local/lib/docker/cli-plugins/docker-compose https://github.com/docker/compose/releases/download/v2.14.1/docker-compose-linux-x86_64
sudo chmod 755 /usr/local/lib/docker/cli-plugins/docker-compose

# ssh server
sudo systemctl enable sshd
sudo systemctl start sshd

# switching a session
# steamos-session-select plasma
# steamos-session-select gamescope
```

## make a desktop session persistent

```
sudo vim /etc/sddm.conf.d/zz-steamos-autologin.conf 
```

and replace

```
[Autologin]
Session=plasma-steamos-oneshot.desktop
```

with

```
[Autologin]
Session=plasma.desktop
```

## install husarnet

```
wget https://install.husarnet.com/tgz/husarnet-latest-amd64.tar
sudo tar --directory=/ --no-same-owner --dereference -xf husarnet-latest-amd64.tar
sudo systemctl enable husarnet
sudo systemctl start husarnet
sudo husarnet join 
```