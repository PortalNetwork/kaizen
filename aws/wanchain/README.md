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

![Choose AMI](https://s3.amazonaws.com/kaizen-images/github/aws_choose_ami.png)

- Choose an instance
    - Type: t2.micro (Free tier)
    - vCPUs: 1
    - Memory: 1 GB
    - Storage: EBS only

![Choose Instance](https://s3.amazonaws.com/kaizen-images/github/aws_choose_instance.png)

Review the instance information
![Review Instance](https://s3.amazonaws.com/kaizen-images/github/aws_review_instance.png)

### Using AWS S3 to store Wanchain blockchain data

## 2. Connect to node

```
ssh -i <PEM_PATH> ubuntu@<HOSTNAME>
```

![Launch Instance](https://s3.amazonaws.com/kaizen-images/github/aws_launch_instance.png)

## 3. Download and build

Download newest version from Wanchain
```
wget https://github.com/wanchain/go-wanchain/releases/download/v1.0.4/gwan-linux-amd64-1.0.4-b7ce29ea.tar.gz
```

![Latest Wanchain](https://s3.amazonaws.com/kaizen-images/github/aws_review_instance.png)

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
