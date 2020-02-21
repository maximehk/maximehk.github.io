# Raspberry Pi setup

## Flashing the SD card

## Initial configuration

### raspi-config

```shell
sudo raspi-config
```

### Standard maximehk stuff

```shell
sudo apt-get install -y git && \
  git clone https://github.com/maximehk/new_setup.git && \
  ./new_setup/init.sh
```

### SSH keys

```shell
# Init your ssh directory
mkdir .ssh
chmod 700 .ssh
touch authorized_keys
chmod 644 authorized_keys

# Append your public key to `authorized_keys`
cat >> authorized_keys
```

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

