This is a quck-start, for more detailed instructions, please see:
https://docs.microsoft.com/en-us/azure/iot-edge/quickstart-linux

## Install Phyton pip
```
sudo apt-get install python-pip
```

## Install Docker prerequisites
```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

## Install Docker
```
curl -sSL https://get.docker.com | sh
```

## Allow PI user to run docker
```
sudo usermod -aG docker pi
```
Refer to https://docs.docker.com/engine/security/security/#docker-daemon-attack-surface for more information.

## Test docker installation
```
sudo docker run hello-world
```

## Switching to the Azure Portal, create a resource group from the CLI
```
az group create --name IoTEdge --location westeurope
```
## Create an IoT Hub
```
az iot hub create --resource-group IoTEdge --name MyIotHub --sku F1
```

## Set up the IoT device from the azure portal
1. Navigate to your IoT hub.
2. Select IoT Edge (preview).
3. Select Add IoT Edge device.
4. Give your simulated device a unique device ID.
5. Select Save to add your device.
6. Select your new device from the list of devices.
7. Copy the value for Connection string--primary key and save it. You'll use this value to configure the IoT Edge runtime in the next section.

## Install build essentials
```
sudo apt-get install build-essential libssl-dev libffi-dev python-dev
```

## Back to the PI, download, install and start the IoT Edge runtime
(Remember to replace {device connection string} from the previous step)
```
sudo pip install -U azure-iot-edge-runtime-ctl
sudo iotedgectl setup --connection-string "{device connection string}" --auto-cert-gen-force-no-passwords
sudo iotedgectl start
```

## Done!
You can verify the setup by checking for a running docker container
```
sudo docker ps
```
