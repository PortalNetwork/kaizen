# Setting up Wanchain on AWS

> Wanchain aims to build a super financial market of digital assets. It is an infrastructure connecting different digital assets.

## What is needed

### SSH Terminal 
- Windows: Recommend Putty, [https://www.putty.org/](https://www.putty.org/)
- Mac OS: Using default terminal

## Getting Started

### Login
If you already have AWS account, you can login into your account.

### Sign up
If you don't have AWS account, please sign up.

## 1. Create AWS EC2

### AWS EC2 configuration
- Choose an image
    - Ubuntu: 18.04 x 64

- Choose a size
    - CPU: 1 GB
    - SSD: 25 GB
    - Transfer: 1000 GB
    - Price: $5 / month

### Using AWS S3 to store Wanchain blockchain data

## 2. Connect to node

```
ssh -i <PEM_PATH> ubuntu@<HOSTNAME>
```

## 3. Download and build

Download newest version from Wanchain
```
wget https://github.com/wanchain/go-wanchain/releases/download/v1.0.4/gwan-linux-amd64-1.0.4-b7ce29ea.tar.gz
```

Unzip Wanchain file
```
tar xvfz gwan-linux-amd64-1.0.4-b7ce29ea.tar.gz
```

Download `s3fs` to mount AWS S3 
```
sudo apt-get update
sudo apt-get install s3fs
```

Setup the configuration of `s3fs`
```
echo ACCESS_KEY_ID:SECRET_ACCESS_KEY >  ~/.passwd-s3fs
chmod 600  ~/.passwd-s3fs
```

Create a folder to store Wanchain blockchain data
```
mkdir wanchain
s3fs wanchain-s3fs wanchain -o passwd_file=~/.passwd-s3fs
```

Change directory to the Wanchain source
```
cd gwan-linux-amd64-1.0.4-b7ce29ea/
```

Try to start Wanchain, using CTRL+C can interrupt the daemon
```
./gwan --datadir=/home/ubuntu/wanchain
```

Using `screen` to run Wanchain in the background 
```
screen -dmSL wanchain ./gwan --datadir=/home/ubuntu/wanchain --rpc --rpcport 8545 --rpcaddr 0.0.0.0
```
