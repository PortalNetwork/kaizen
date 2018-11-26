# Setting up IPFS on DigitalOcean

> A peer-to-peer hypermedia protocol to make the web faster, safer, and more open.

## What is needed

### SSH Terminal 
- Windows: Recommend Putty, [https://www.putty.org/](https://www.putty.org/)
- Mac OS: Using default terminal

## Getting Started

### Login
If you already have DigitalOcean account, you can login into your account.

### Sign up
If you don't have DigitalOcean account, please sign up.

## 1. Create Project
![Create Project](https://s3.amazonaws.com/kaizen-images/github/create_project.png)

## 2. Create Droplets
![Create Droplet](https://s3.amazonaws.com/kaizen-images/github/create_droplet.png)

### Droplets configuration
- Choose an image
    - Ubuntu: 18.04 x 64

- Choose a size
    - CPU: 1 GB
    - SSD: 25 GB
    - Transfer: 1000 GB
    - Price: $5 / month

![Choose Image](https://s3.amazonaws.com/kaizen-images/github/choose_ipfs_image.png)

- CPU Optimized Droplets (Skip)
- Add backups (Skip)
- Add block storage (Skip)
- Choose a datacenter region
    - Bangalore

![Choose Region](https://s3.amazonaws.com/kaizen-images/github/choose_region.png)

- Select additional options (Skip)
- Add your SSH keys (Skip)
- Finalize and create
    - Choose a hostname: _Type a name you'd like_ or using default

![Choose Hostname](https://s3.amazonaws.com/kaizen-images/github/choose_hostname.png)

- Click __Create__

## 3. Connect to node
After create the Droplets, you will receive the email include:
- Droplet Name
- IP Address
- Username
- Password

Using terminal/putty to connect the droplet node
```shell
$ ssh root@<IP_ADDRESS>
```

_NOTE: You must change your password at the first time you connect to the droplet node._

## 4. Download and build

Download newest version from IPFS
```shell
wget https://dist.ipfs.io/go-ipfs/v0.4.18/go-ipfs_v0.4.18_linux-386.tar.gz
```

Unzip the file
```shell
tar xvfz go-ipfs_v0.4.18_linux-386.tar.gz
```

Run the script to install IPFS
```shell
cd go-ipfs
sudo ./install.sh
```

## 5. Start service

Initilize IPFS
```shell
ipfs init
```

Start IPFS daemon
```shell
ipfs daemon
```

Done! The IPFS daemon is started.

## 6. Upload file to IPFS

```shell
echo "hello world" | ipfs add
added QmT78zSuBmuS4z925WZfrqQ1qHaJ56DQaTfyMUF7F8ff5o QmT78zSuBmuS4z925WZfrqQ1qHaJ56DQaTfyMUF7F8ff5o
```

Try it out: https://gateway.ipfs.io/ipfs/QmT78zSuBmuS4z925WZfrqQ1qHaJ56DQaTfyMUF7F8ff5o
