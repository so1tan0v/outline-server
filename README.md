# Instruction for install Outline

## Applications

### Outline-manager

Download app https://getoutline.org/ru/get-started/ (In 1 and 2 step)

How to use
1. Download Outline manager
2. Add new server with "Advanced" type
3. In "installation output" put this
```json
{ 
  "apiUrl": "https://1.2.3.4:1234/XXXXXXXXXXXX", 
  "certSha256": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" 
}
```

### Outline-сlient

URLs to Application 
IOS: https://apps.apple.com/us/app/outline-app/id1356177741
Android: https://play.google.com/store/apps/details?id=org.outline.android.client&hl=en_US
PC or MacOS: https://getoutline.org/ru/get-started/ (In the step 3)

How to get VPN
1. Download App
2. Add new server in Outline application. As address put individual key (`ss://xxxxxxxxxxxxx@<ADDRESS>:<PORT>/?outline=1`)



## Installation

### Docker
```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install -y docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
sudo systemctl enable docker
```

### Install outline

#### For x86
```bash
sudo wget -qO- https://raw.githubusercontent.com/Jigsaw-Code/outline-server/master/src/server_manager/install_scripts/install_server.sh | bash
```

#### For arm (Raspberry Pi)
```bash
SB_IMAGE=oreoluwa/shadowbox:daily sudo --preserve-env bash -c "$(wget -qO- https://raw.githubusercontent.com/EricQmore/installer/main/install_server.sh)"
```
When you finished, the output should be like:

Please copy the following configuration to your Outline Manager:
```json
{ 
  "apiUrl": "https://1.2.3.4:1234/XXXXXXXXXXXX", 
  "certSha256": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" 
}
```
Just leave it there. You will need these information in the next step. That's enough for the server side. Now, we will move to the client side.
#### P.S. You could get this information in `/opt/outline/access.txt`
```bash
cat /opt/outline/access.txt
```


### Allow incoming connections in firewalld (if you use this) 

The ports that need to be added will be indicated at the end of the installation command.
```bash
sudo firewall-cmd --permanent --add-port=xxxxxx/tcp
sudo firewall-cmd --permanent --add-port=xxxx/udp
sudo firewall-cmd --reload
```

### Configuration
Put this to Outline-manager
```json
{ 
  "apiUrl": "https://1.2.3.4:1234/XXXXXXXXXXXX", 
  "certSha256": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" 
}
```
Add the required keys for each user


## Manage Outline-server

### Start app
```bash
docker start watchtower
docker start shadowbox
```

### Stop app
```bash
docker start watchtower
docker start shadowbox
```