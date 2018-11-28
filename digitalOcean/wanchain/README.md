# Setting up Wanchain on DigitalOcean

> Wanchain aims to build a super financial market of digital assets. It is an infrastructure connecting different digital assets.

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

![Choose Hostname](https://s3.amazonaws.com/kaizen-images/github/choose_wanchain_hostname.png)

- Click __Create__

### Add Volumn for store Wanchain blockchain data

You can choose the size you need, recommend 250G.
![Add Volumn](https://s3.amazonaws.com/kaizen-images/github/add_volumn.png)

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

Download newest version from Wanchain
```shell
wget https://github.com/wanchain/go-wanchain/releases/download/v1.0.4/gwan-linux-amd64-1.0.4-b7ce29ea.tar.gz
```

![Latest Wanchain](https://s3.amazonaws.com/kaizen-images/github/aws_review_instance.png)

Unzip the file
```shell
tar xvfz gwan-linux-amd64-1.0.4-b7ce29ea.tar.gz
```

Run the script to install Wanchain
```shell
cd gwan-linux-amd64-1.0.4-b7ce29ea
./gwan --datadir=<VOLUMN_PATH>
```

Using screen to run Wanchain node at background
```shell
screen -dmSL wanchain ./gwan --datadir=<VOLUMN_PATH>
```
