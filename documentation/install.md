### Dowload Rasbian image:
https://www.raspberrypi.org/downloads/

### Choose RASPBIAN STRETCH LITE
https://downloads.raspberrypi.org/raspbian_lite_latest

### Burn image to SD using Etcher:
https://etcher.io/

### Boot the PI with a screen and a keyboard attached

### Set static IP
sudo nano /etc/dhcpcd.conf 

At the bottom of the file, add:
```
#static IP configuration
interface eth0
static ip_address=192.168.1.15/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1
```

### Restart the PI
```sudo reboot```

### Enable SSH
sudo systemctl enable ssh.service
sudo systemctl start ssh.service

### Verify connection from a remote computer
### Disconnect screen and keyboard