# steamdeck-docker

Instructions &amp; scripts for steamdeck customization

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
```