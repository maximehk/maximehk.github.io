# Raspberry Pi setup

## Docker install

Instructions from [dev.to](https://dev.to/rohansawant/installing-docker-and-docker-compose-on-the-raspberry-pi-in-5-simple-steps-3mgl)

```shell
# Install docker and set permissions
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker pi

# Install docker compose (including dependencies)
sudo apt-get install libffi-dev libssl-dev
sudo apt-get install -y python python-pip
sudo apt-get remove python-configparser
sudo pip install docker-compose
```

