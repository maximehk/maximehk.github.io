# Raspberry Pi setup

## Hardware

Raspberry Pi 4 + [Sandisk Extreme SSD](https://shop.westerndigital.com/products/portable-drives/sandisk-extreme-usb-3-1-ssd#SDSSDE60-1T00-G25)

## Flashing the SD card and SSD drive + boot from SSD

Source: [video by Andreas Spiess](https://www.youtube.com/watch?v=gp6XW-fGVjo) and [J. Chambers Blog Post](https://jamesachambers.com/raspberry-pi-4-usb-boot-config-guide-for-ssd-flash-drives/)

1. Download the latest OS from [raspberrypi.org](https://www.raspberrypi.org/downloads/raspbian/)
1. Flash the SD Card and SSD disk with [Balena Etcher](https://www.balena.io/etcher/)
1. Remove the SSD disk and make sure the boot partition from the SD Card is mounted
1. Assuming you're running MacOS type the commands below to allow remote access over wifi
1. Remove the SD card from your computer and re-insert the SSD then run the command again
1. At this stage, follow the instructions from the [blog post](https://jamesachambers.com/raspberry-pi-4-usb-boot-config-guide-for-ssd-flash-drives/).

```bash
touch /Volumes/boot/ssh
cat > /Volumes/boot/wpa_supplicant.conf << 'EOF'
country=CH
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
     ssid="kiwi"
     psk="PASSWORD HERE"
     key_mgmt=WPA-PSK
}
EOF
```

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
cat >> .ssh/authorized_keys
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

